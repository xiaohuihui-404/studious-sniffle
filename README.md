# studious-sniffle
初步学习
import os
import requests
api_key = os.getenv('WEATHER_API_KEY')
if not api_key:
    print("API key is missing! Please set the environment variable.")
    exit()
city = 'beijing'
base_url = "http://api.openweathermap.org/data/2.5/weather?"
complete_url = f"{base_url}q={city}&appid={api_key}&units=metric"  
response = requests.get(complete_url)
data = response.json()
if data["cod"] == 200:
main_data = data["main"]
weather_data = data["weather"][0]
print(f"Weather in {city}:")
print(f"Temperature: {main_data['temp']}°C")
print(f"Weather: {weather_data['description']}")
print(f"Humidity: {main_data['humidity']}%")
print(f"Pressure: {main_data['pressure']} hPa")
else:
print(f"Error: {data['message']}")
