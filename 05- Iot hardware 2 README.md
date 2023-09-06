# Week 5

## Cara Pengerjaan

Mohon menjawab pertanyaan yang ada dibawah ini, untuk menjawabnya kalian dapat membaca perintah yang telah diberikan dan upload code dan penjelasan/jawaban selain code dalam sebuah MD files ( namakan [README.md](http://README.md) ) ke repo github kalian masing-masing, dan namakan repo tersebut sebagai technical-assignment-week-5-NAMAKALIAN. Dan kemudian silahkan copy dan share link repo github kalian.

---

## Pertanyaan

Menggunakan sebuah sensor ***selain sensor ultrasonic HC-SR04***, buatlah hal-hal berikut:

1. Wiring diagram untuk sensor tersebut menggunakan fritzing ( upload dalam MD files screenshot wiring diagram tersebut )(![image](https://github.com/rippin8/.NEEDDUIT/assets/138226567/0be9ffb8-d970-4170-9b62-ae8669dd779f)

2. Script sensor.py dan sebuah fungsi untuk mengambil data dari sensor tersebut (import RPi.GPIO as GPIO
import time
from actuator import *
from send_data import *

GPIO.setwarnings(False)
GPIO.setmode(GPIO.BCM)
GPIO.setup(4, GPIO.IN)         #Read output from PIR motion sensor
#GPIO.setup(3, GPIO.OUT)         #LED output pin

def detect_motion():
	i=GPIO.input(4)
	if i==0:                 #When output from motion sensor is LOW
		print("No intruders",i)
		send_ubidots("01","tidak",0)
		ledredoff()
		buzzeroff()
		#GPIO.output(3, 0)  #Turn OFF LED
		time.sleep(0.1)
	elif i==1:               #When output from motion sensor is HIGH
		print("Intruder detected",i)
		send_ubidots("01","ya",1)
		ledredon()
		buzzeron()
		#GPIO.output(3, 1)  #Turn ON LED
		time.sleep(0.5)
  
3. Sebuah script utama [main.py](http://main.py) yang terdiri dari sebuah logic sederhana yang menjawab sebuah use case sederhana ( jelaskan use case tersebut dalam MD files! )
   (import time
from sensor import * 

def cleanup():
    # Membersihkan pin GPIO pada Raspberry Pi
    GPIO.cleanup()


try:
    while True:
        detect_motion()

        #print("Jarak benda: %.2f cm" % distance)           
       #time.sleep(0.5)  # Memberi jeda sebelum membaca data berikutnya

except KeyboardInterrupt:
    # Memberhentikan program dengan menekan Ctrl + C
    cleanup() )
5. (Optional) Ambil sekitar 5 - 10 sample data dan tampilkan dalam sebuah grafik matplotlib dan screenshot hasil tersebut dan upload pada MD files. (-)
