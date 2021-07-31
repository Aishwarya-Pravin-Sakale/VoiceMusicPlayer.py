# VoiceMusicPlayer
Implemented python modules to play music by takingvoice as input.
import speech_recognition as sr
import pyttsx3
import pywhatkit

listener = sr.Recognizer()
engine = pyttsx3.init()
voices = engine.getProperty('voices')
engine.setProperty('voice', voices[1].id)


engine.say('Hello Everyone....')
engine.say('I am Jimmy')
engine.say('Aishwarya Created me....')
engine.say('What can I do for you')
engine.runAndWait()

def talk(text):
    engine.say(text)
    engine.runAndWait()

def take_command():
    try:
        with sr.Microphone() as source:
            print(' I am Listening ......... ')
            voice = listener.listen(source)
            command = listener.recognize_google(voice)
            command = command.lower()
            if 'Jimmy' in command:
                command = command.replace('Jimmy','')
                print(command)
                talk(command)

    except:
        pass
    return command
def run():
    command = take_command()
    if 'play' in command:
        song = command.replace('play', '')
        talk('playing'+song)
        print('playing'+song)
        pywhatkit.playonyt(command)

run()
