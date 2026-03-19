# EXP 5 : SPEECH RECOGNITION USING SCILAB

## AIM: 

To perform and verify speech recognition using SCILAB. 

## APPARATUS REQUIRED: 
Google Colab

## PROGRAM : 
```

!pip -q install SpeechRecognition pydub
!apt-get -qq install ffmpeg

import speech_recognition as sr
from google.colab import files
from pydub import AudioSegment

print("📁 Upload audio file (MP3 or WAV)")
uploaded = files.upload()

audio_file = list(uploaded.keys())[0]

if audio_file.endswith(".mp3"):
    print("🔄 Converting MP3 to WAV...")
    sound = AudioSegment.from_mp3(audio_file)
    audio_file = "converted.wav"
    sound.export(audio_file, format="wav")

recognizer = sr.Recognizer()

with sr.AudioFile(audio_file) as source:
    audio_data = recognizer.record(source)

try:
    text = recognizer.recognize_google(audio_data)
    print("\n🎯 Converted Text:\n", text)

except sr.UnknownValueError:
    print("\n❌ Could not understand audio")

except sr.RequestError:
    print("\n❌ API error (Check internet)")
```

## OUTPUT: 

<img width="500" height="600" alt="image" src="https://github.com/user-attachments/assets/937e8da0-fe18-46bf-ad7c-8bd2fee1bc59" />

## RESULT: 
Thus the speech recognition was performed and verified.
