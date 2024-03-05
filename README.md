# SPECH-RECOGNITION

import pyttsx3 as pt
import pywhatkit as pk



listening = sr.Recognizer()
engine = pt.init('dummy')

def speak(text):
    engine.say(text)
    engine.runAndWait()
    
def hear():
    cmd = "" #initialize cmd with a default value
    
    try:
        with sr.Microphone() as mic:
            print('listening....')
            voice = listening.listen(mic)
            cmd = listening.recognize_google(voice)
            cmd=cmd.lower()
            if 'bixby' in cmd:
                cmd=cmd.replace('bixby' ,'')
                print(cmd)
    except Exception as e: # catch specific exception for better error handling
          print("Error:" ,e)
    return cmd

def run():
    cmd=hear()
    print(cmd)   
    if 'play' in cmd:
        song = cmd.replace('play' , '')
        speak('playing' + song)
        pk.playonyt('Playing...' + song)
        
        
run()     
