# Nimesa
import requests

API_URL = "https://api.example.com/hourly_weather_forecast"

def get_weather_data(date):
    response = requests.get(API_URL)
    if response.status_code == 200:
        data = response.json()
        for entry in data:
            if entry['date'] == date:
                return entry['temp']
        return None
    else:
        print(f"Failed to fetch weather data. Status Code: {response.status_code}")
        return None

def get_wind_speed_data(date):
    response = requests.get(API_URL)
    if response.status_code == 200:
        data = response.json()
        for entry in data:
            if entry['date'] == date:
                return entry['wind']['speed']
        return None
    else:
        print(f"Failed to fetch wind speed data. Status Code: {response.status_code}")
        return None

def get_pressure_data(date):
    response = requests.get(API_URL)
    if response.status_code == 200:
        data = response.json()
        for entry in data:
            if entry['date'] == date:
                return entry['pressure']
        return None
    else:
        print(f"Failed to fetch pressure data. Status Code: {response.status_code}")
        return None

def main():
    while True:
        print("\n1. Get weather")
        print("2. Get Wind Speed")
        print("3. Get Pressure")
        print("0. Exit")

        option = input("Enter your choice: ")

        if option == "1":
            date = input("Enter the date (YYYY-MM-DD): ")
            temp = get_weather_data(date)
            if temp is not None:
                print(f"Temperature on {date}: {temp} °C")
            else:
                print(f"No data available for {date}")

        elif option == "2":
            date = input("Enter the date (YYYY-MM-DD): ")
            wind_speed = get_wind_speed_data(date)
            if wind_speed is not None:
                print(f"Wind Speed on {date}: {wind_speed} m/s")
            else:
                print(f"No data available for {date}")

        elif option == "3":
            date = input("Enter the date (YYYY-MM-DD): ")
            pressure = get_pressure_data(date)
            if pressure is not None:
                print(f"Pressure on {date}: {pressure} hPa")
            else:
                print(f"No data available for {date}")

        elif option == "0":
            print("Exiting the program.")
            break

        else:
            print("Invalid option. Please try again.")

if __name__ == "__main__":
    main()
