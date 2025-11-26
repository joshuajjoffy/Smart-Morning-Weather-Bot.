🌤️ Smart Morning Weather Bot

📋 Overview

The Smart Morning Weather Bot is a personal assistant automation designed to run every morning at 6:00 AM. It eliminates the need to check weather apps by proactively sending a decision-based email about what to wear and whether to carry an umbrella.

The system connects to the OpenWeatherMap API to fetch real-time meteorological data, processes the data using a custom Python script to apply "comfort logic," and delivers a concise, actionable summary via Gmail.

🚀 Key Features

Automated Scheduler: Runs automatically every morning (Cron job logic).

API Integration: Fetches live temperature, humidity, and weather conditions from OpenWeatherMap.

Intelligent Decision Engine (Python):

Analyzes temperature to recommend outfits (Winter Jacket vs. Light Jacket vs. T-Shirt).

Detects rain/drizzle codes to trigger "Umbrella Alerts."

Actionable Notifications: Sends a clean, readable email with specific advice, not just raw numbers.

🛠️ Tech Stack

Orchestration: n8n

Scripting: Python (Data parsing & conditional logic)

External API: OpenWeatherMap API

Communication: Gmail (SMTP)

⚙️ Logic & Rules

The Python node implements the following decision matrix:

Condition

Threshold

Action/Advice

Rain

Weather code contains "Rain"

"Don't forget your UMBRELLA ☔"

Cold

Temp < 10°C

"Wear your WINTER jacket ❄️"

Cool

10°C ≤ Temp < 18°C

"Bring a light jacket 🧥"

Warm

Temp ≥ 18°C

"It's t-shirt weather! 👕"

🔄 Workflow Architecture

Schedule Trigger: Wakes up the workflow at 6:00 AM.

HTTP Request: GET request to api.openweathermap.org/data/2.5/weather.

Python Logic:

Extracts main.temp and weather[0].main.

Runs if/else logic to generate the advice string.

Gmail Node: Injects the advice and city name into a dynamic email template.

(Note: Upload a screenshot of your n8n workflow here)

📥 Example Email Output

Subject: Weather Alert for Stade: 8.5°C

Body:
Good Morning! In Stade, it is 8.5°C.

Advice: Wear your winter jacket and don't forget your umbrella!

🔧 How to Run

Get API Key: Sign up at OpenWeatherMap and generate a free API Key.

Import Workflow: Import the weather_bot.json file into n8n.

Configure HTTP Node:

method: GET

URL: https://api.openweathermap.org/data/2.5/weather

query parameters: q={your_city}, appid={your_key}, units=metric

Activate: Toggle the workflow to "Active".

Built with ❤️ and Automation
