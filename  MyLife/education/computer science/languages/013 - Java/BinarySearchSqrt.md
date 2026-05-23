


public class BinarySearchSqrt {  
  
   public static double binarySearchSqrt(double n) {  
       double low = 0;  
       double high = n;  
       double mid = 0;  
       double epsilon = n * 1e-9;  
  
       while (true) {  
           mid = (low + high) / 2;  
           double square = mid * mid;  
           double error = Math.abs(square - n);  //negativ auch positiv machen für epsilon check
  
           if (error <= epsilon) {  
               break;  
           }  
  
           if (square > n) {  
               high = mid;  
           } else {  
               low = mid;  
           }  
       }  
  
       return mid;  
   }  
  
   public static void main(String[] args) {  
  
       double[] zahlen = {};  
  
       for (double n : zahlen) {  
       //sollte enhanced for loop sein
           long start = System.nanoTime();  
           //System.nanoTime() Zeit tracken
  
           double wurzel = binarySearchSqrt(n);  
  
           long ende = System.nanoTime();  
           long dauer = ende - start;      
  
           System.out.println(n + " ≈ " + wurzel);  
           System.out.println(dauer + " ns\n");  
       }  
   }  
}