# ☀️ DayPilot - Your AI-Powered Morning Buddy

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://daypilot.streamlit.app/)

DayPilot is your all-in-one morning assistant, designed to help you start your day informed, inspired, and organized. Get the latest weather, curated news, and a personalized daily plan—all powered by AI.

**➡️ [Try the live demo!](https://daypilot.streamlit.app/)**

---

## ✨ Features

* **Inspirational Home Page**: Greets you with a random motivational quote and a beautiful morning image to set a positive tone for your day [cite: app.py].
* **Real-Time Weather Updates**: Enter any city to get a clear, human-friendly weather report, including temperature in Celsius, humidity, wind speed, and practical suggestions on what to wear or carry [cite: applications.py, app.py].
* **Curated News Feed**: Fetch the top 5 latest news articles based on your area of interest (e.g., Technology, Sports). Each article is accompanied by its title, image, a link to the full story, and a concise AI-generated summary [cite: applications.py, app.py].
* **Smart Day Planner**: The AI acts as a personal planner, creating a balanced and actionable itinerary for your day in a specified city. It intelligently considers:
    * The day's weather forecast.
    * Top-rated tourist attractions.
    * Local events happening on that day.
    * It then organizes a chronological plan from morning to evening, mixing activities with leisure breaks [cite: applications.py, app.py].

---

## ⚙️ How It Works

DayPilot leverages the power of Google's Gemini models and several APIs to deliver its features:

1.  **Weather**: The `get_weather` function fetches data from the **OpenWeather API**. This raw JSON data is then processed by a Gemini model, which uses a specific system prompt to transform it into a conversational weather update with clothing suggestions [cite: applications.py].
2.  **News**: The `get_news` function pulls the latest articles from the **NewsAPI** based on the user's chosen topic. For each article URL, the `news_summarizer` function uses a Gemini model to generate a crisp summary [cite: applications.py].
3.  **Smart Planner**: This is the core AI feature. The `smart_plan` function uses a powerful Gemini model with multiple tools:
    * `get_forcasted_weather`: Uses Google Search as a tool to find the day's weather forecast and top tourist spots.
    * `find_local_events`: Uses the **SerpApi** to find local events.
    * The model then synthesizes all this information based on a detailed prompt to create a personalized, weather-aware itinerary for the user [cite: applications.py].
4.  **Frontend**: The entire user interface is built with **Streamlit**, providing a clean, interactive, and easy-to-navigate multi-page application [cite: app.py, requirements.txt].

---

## 🛠️ Tech Stack

* **Backend / AI Logic**: Python
* **Generative AI Model**: Google Gemini (`gemini-2.5-flash`, `gemini-2.5-flash-lite`) [cite: applications.py, requirements.txt]
* **Web Framework**: Streamlit [cite: app.py, requirements.txt]
* **APIs**: OpenWeather API, NewsAPI, SerpApi (for Google Events) [cite: applications.py]
* **Web Requests**: `requests` [cite: requirements.txt]
* **Environment Variables**: `python-dotenv` [cite: requirements.txt]

---

## 🚀 Getting Started

Follow these instructions to set up and run the project locally.

### Prerequisites

* Python 3.8+
* API Keys for:
    * Google AI
    * OpenWeather
    * NewsAPI
    * SerpApi

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/day-pilot.git](https://github.com/your-username/day-pilot.git)
    cd day-pilot
    ```

2.  **Create and activate a virtual environment (recommended):**
    * **On macOS/Linux:**
        ```bash
        python3 -m venv venv
        source venv/bin/activate
        ```
    * **On Windows:**
        ```bash
        python -m venv venv
        .\venv\Scripts\activate
        ```

3.  **Install the required dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
    [cite: requirements.txt]

4.  **Set up your environment variables:**
    * Create a file named `.env` in the root of your project directory.
    * Add your API keys to this file. The application uses `load_dotenv()` to access them [cite: applications.py].
        ```
        GOOGLE_API_KEY="YOUR_GOOGLE_API_KEY"
        # The other API keys are hard-coded in applications.py, 
        # but it's best practice to move them here as well.
        ```

### Usage

1.  **Run the Streamlit application:**
    ```bash
    streamlit run app.py
    ```

2.  **Open the application in your browser:**
    * Navigate to the local URL provided in the terminal (usually `http://localhost:8501`).

---

## 📂 Project Structure
```
.
├── app.py              # Main Streamlit application file for UI and navigation
├── applications.py     # Core logic for API calls and Gemini model interactions
├── requirements.txt    # Project dependencies
└── .env                # For storing API keys (to be created by you)
```
