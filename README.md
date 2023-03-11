# Daily-weather-Update
Get your city's daily weather update automatically in whatsapp even when you are sleeping

#import important libraries
import pywhatkit
import requests
import json

api_key = "1659cf5477bd0a121c844691d4bd9e81"
#This api key is an auto generated api key from the website from which I will take the live weather update

city='bangalore'
#Enter your city name here

url = 'https://api.openweathermap.org/data/2.5/weather?q=%s&appid=%s&units=metric'% (city, api_key)
response = requests.get(url)
data = json.loads(response.text)
f = '%.2f'%(((int(data['main']['temp']))*1.8)+32)
d = str(data['weather'])
print(data['weather'])
d1 = d[13:-16]
print(d1)
print(data['main']['temp'])
x = (" the temperature in {} is ".format(city)+str(data["main"]["temp"])+' C'+' or'+' '+str(f)+' F')
print(d1)
print(x)
pywhatkit.sendwhatmsg('+91-XXXXXXXXXX',d1+ x,7,30)
#input the whatsapp number of the person to whom you want to send the weather update
#I have set the time at 7:30 am in line number 27, so adjust accordingly.

#The whatsapp number will get a message as "main : Clouds, description : overcast clouds, the temperature in bangalore is 14.8 C or 57.20 F"
