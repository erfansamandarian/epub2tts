This script takes an epub and creates mp3's of the chapters, read by https://github.com/coqui-ai/TTS

I have not had good luck getting Coqui-AI to run on an M1 mac but it runs great on Linux.

I recognize this is not very user friendly, but I wanted to share in case folks thought it was useful. If there are a few more people than myself that find this is useful I will keep working on turning it into something that could be used by someone without dev experience.

## Docker usage:
This image is HUGE, I think mainly from all the stuff TTS pulls in. When I build locally it's 7.6gb!

Voice models will be saved locally in `~/.local/share/tts`

Change to directory containning your epub and run with:
```
docker run -v "$PWD:$PWD" -v ~/.local/share/tts:/root/.local/share/tts -w "$PWD" -e BOOK=your-book.epub  epub2tts
```

## INSTALLATION:

For  now I've only tested this on a linux machine (Ubuntu 22 in my case)

```
#clone the repo
git clone https://github.com/aedocw/epub2tts
cd epub2tts
#create a virtual environment
python3 -m venv .venv
#activate the virtual environment
source .venv/bin/activate
#install dependencies
sudo apt install espeak-ng ffmpeg
pip3 install -r requirements.txt
```

Usage: `python3 epub2tts.py my-book.epub`
