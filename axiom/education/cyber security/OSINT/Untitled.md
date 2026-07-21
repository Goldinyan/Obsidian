
Blackbird searches trough hundred of networks based on known WhatsMyName Databases.

GitHub: p1ngul1n0/blackbird

#### Installation:

```bash
python3 --version
git --version

git clone https://github.com/p1ngul1n0/blackbird
cd blackbird

pip3 install -r requirements.txt 

# This might get blocked, then use virtual enviroment

python3 -m venv venv
source venv/bin/activate
pip3 install -r requirements.txt

# Start

python3 blackbird.py -u <username>

# Integrate with AI

python3 blackbird.py -u <username> -ai

# You need to supply an API KEY


```