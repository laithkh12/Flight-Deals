# ✈️ Flight Price Tracker

This project automatically tracks flight prices for specified destinations and sends notifications when the price is below a certain threshold. It utilizes APIs like **Amadeus** and **Twilio** to fetch flight data and send alerts via SMS or WhatsApp.

## 📂 Project Structure

The project consists of the following main files and components:

1. **main.py** - The entry point of the project, managing the workflow.
2. **notification_manager.py** - Handles notifications via SMS and WhatsApp.
3. **flight_search.py** - Interacts with the Amadeus API to search for flights.
4. **flight_data.py** - Processes and organizes flight data.
5. **data_manager.py** - Manages Google Sheets data through the Sheety API.

---

## 🚀 Getting Started

### 🔑 Prerequisites

1. **Python** (3.x)
2. Required libraries:
   - `requests`
   - `dotenv`
   - `twilio`
3. **.env file** containing API keys and credentials for Twilio, Amadeus, and Sheety.

### 📜 Environment Variables

Create a `.env` file in the root directory with the following variables:

```plaintext
TWILIO_SID=your_twilio_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
TWILIO_VIRTUAL_NUMBER=your_twilio_virtual_number
TWILIO_VERIFIED_NUMBER=your_verified_number
TWILIO_WHATSAPP_NUMBER=your_whatsapp_number

AMADEUS_API_KEY=your_amadeus_api_key
AMADEUS_SECRET=your_amadeus_secret

SHEETY_USERNAME=your_sheety_username
SHEETY_PASSWORD=your_sheety_password
SHEETY_PRICES_ENDPOINT=your_sheety_endpoint
```
---
## 🛠 Installation
1. Clone the repository.
2. Install dependencies:
```bash
pip install -r requirements.txt
```
3. Set up environment variables as described above.
---
## 🗃️ Modules
### main.py
This script orchestrates the following steps:
1. Update Airport Codes in the Google Sheet for each city.
2. Search Flights between a specified origin and destination within a six-month timeframe.
3. Send Notifications via WhatsApp if the flight price is below the threshold.
### notification_manager.py
Handles sending notifications through Twilio. You can either:
- Use send_sms() to send an SMS notification.
- Fetch flight offers based on specified dates and cities.
### flight_data.py
Defines the FlightData class and find_cheapest_flight function to:
- Parse flight data.
- Identify the cheapest flight and return the details.
### data_manager.py
Interacts with the Google Sheets API (Sheety) to:
- Retrieve destination data.
- Update city IATA codes in the Google Sheet.
---
## 📝 Usage
1. Set your origin city code in main.py (default: LON for London).
2. Run the program:
```bash
python main.py
```
3. The program will:
- Update IATA codes in the Google Sheet.
- Search for flights.
- Send a WhatsApp alert if a cheaper flight is found.
---
## 📧 Notifications
When a lower-priced flight is found, you will receive a message with details such as the price, origin, destination, departure date, and return date. The notification appears in the following format:
```plaintext
Low price alert! Only £{price} to fly from {origin} to {destination}, from {departure} to {return}.
```
---
## 🛠 Troubleshooting
- Twilio SMS Not Working? Make sure your Twilio credentials are correct and verified in the Twilio console.
- Amadeus API Rate Limits? You might need to add delays between API calls to prevent exceeding rate limits.
---
## 💬 Support
For any issues or suggestions, please contact the repository maintainer or raise an issue on GitHub.

