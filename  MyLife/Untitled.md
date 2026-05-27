#include <fstream>
#include <iostream>
#include <string>
#include <vector>

#define TARGET_WIDTH 190

/* YOU NEED TO ZOOM OUT THIS THING IS REALLY BIG */

//const char asciis[]{' ', '.', ':', '-', '=', '+', '*', '#', '%', '@'};
const char asciis[]={'.', ',', '-', '~', ':', ';', '=', '!', '*', '#', '$', '@'};

struct pixel_t {
  float brightness;
  unsigned char r;
  unsigned char g;
  unsigned char b;

  pixel_t(float brightness, unsigned char r, unsigned char g, unsigned char b)
      : brightness(brightness), r(r), g(g), b(b) {}
};

auto calculateBrightness(float red, float green, float blue) -> float {
  // uses linzmanz formel bc humans value green more than blue eg
  // mormally its 0.2126 * r + 0.7152 * g + 0.0722 * b;
  // return (0.2126f * red + 0.7152f * green + 0.0722f * blue) / 255.0f;
  float linearBrightness =
      (0.2126f * red + 0.7152f * green + 0.0722f * blue) / 255.0f;

  return std::cbrt(linearBrightness); // cubic wurzel so wichtig für helligkeit 1 -> 1 aber 0.25 -> 0.58
}

auto processImageToAscii(const std::vector<unsigned char> &rawImage,
                         std::vector<pixel_t> &asciiPixels, int width,
                         int height) -> void {
  int targetHeight = (height * TARGET_WIDTH) / (width * 2);

  float stepX = static_cast<float>(width) / TARGET_WIDTH;
  float stepY = static_cast<float>(height) / targetHeight;

  // skip y lines to compromiss because a letter is 1 x 2 not 1 x 1
  for (int y = 0; y < targetHeight; ++y) {
    for (int x = 0; x < TARGET_WIDTH; ++x) {

      // Berechne exakt, von welchem originalen Pixel wir sampeln
      int origX = static_cast<int>(x * stepX);
      int origY = static_cast<int>(y * stepY);

      int pixelIndex = (origY * width + origX) * 3;

      unsigned char r = rawImage[pixelIndex];
      unsigned char g = rawImage[pixelIndex + 1];
      unsigned char b = rawImage[pixelIndex + 2];

      float brightness = calculateBrightness(r, g, b);
      asciiPixels.emplace_back(brightness, r, g, b);
    }
  }
}

auto printAscii(const std::vector<pixel_t> &asciiPixels, int width) -> void {
  int columnCount = 0;

  for (const auto &p : asciiPixels) {
    int index = static_cast<int>(p.brightness * 11.0f); // oder 9.0f bei den wenigern ascis

    if (index < 0)
      index = 0;
    if (index > 9)
      index = 9;

    std::cout << "\033[38;2;" << static_cast<int>(p.r) << ";"
              << static_cast<int>(p.g) << ";" << static_cast<int>(p.b) << "m"
              << asciis[index];

    columnCount++;

    if (columnCount == TARGET_WIDTH) {
      std::cout << "\n";
      columnCount = 0;
    }
  }

  std::cout << "\033[0m\n";
}

auto main() -> int {
  std::string fileName;
  std::cout << "Enter PPM filename (without .ppm): ";

  if (!(std::cin >> fileName)) {
    std::cerr << "Error: fileName cannot be empty!\n";
    return 1;
  }

  std::ifstream file(fileName.append(".ppm"), std::ios::binary);
  if (!file) {
    std::cerr << "Error: Could not open " << fileName << "!\n";
    return 1;
  }

  std::string format;
  file >> format;
  if (format != "P6") {
    std::cerr << "Error: Wrong Format (Needs to be P6)!\n";
    return 1;
  }

  int width = 0, height = 0, maxVal = 0;
  file >> width >> height >> maxVal;

  file.ignore();

  std::cout << "WIDTH: " << width << "\tHEIGHT: " << height << '\n';

  int imageSize = width * height * 3;
  std::vector<unsigned char> rawImage(imageSize);
  file.read(reinterpret_cast<char *>(rawImage.data()), imageSize);
  file.close();

  std::vector<pixel_t> asciiPixels;
  asciiPixels.reserve(width * (height / 2));

  processImageToAscii(rawImage, asciiPixels, width, height);
  printAscii(asciiPixels, width);

  return 0;
}
