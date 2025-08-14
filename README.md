# Agentic AI Calendar

A smart calendar that consolidates personal schedules with local events and provides proactive, AI-driven assistance.

## 🤖 Agentic AI Aspects of This Project
While the current MVP focuses on establishing a robust data pipeline, this foundation is the critical first step toward the project's full agentic vision. An AI agent requires reliable, structured data to reason and act upon. This MVP builds that data layer.

The ultimate goal is to create an AI that functions as a proactive scheduling assistant. The current system enables this by:

1. **Providing the Data:** Securely fetching and normalizing a user's calendar data.

2. **Creating a "World Model":** Storing this data in a structured database, which serves as the agent's understanding of the user's schedule and commitments.

With this foundation, the following agentic features are planned for development:

- **Natural Language Processing (NLP):** Allow users to manage their schedule via chat commands like, _"Find a time for a 30-minute call with Jane next week"_ or _"What's happening downtown this Saturday evening?"_

- **Intelligent Conflict Resolution:** When a user tries to schedule a new event that overlaps with an existing one, the agent will not just report an error but will proactively suggest alternative, conflict-free time slots.

- **Proactive Event Recommendation:** The agent will learn from a user's calendar history and explicit interests to recommend relevant local events, suggesting them at times when the user is free.

- **Automated Travel Time Calculation:** The agent will automatically block out travel time before and after events with physical locations, preventing users from being double-booked.

## 📂 File Structure
The project is organized into a distinct backend and frontend.

```
agentic-ai-calendar/
│
├── backend/
│   ├── main.py             # FastAPI application, API endpoints, OAuth logic
│   └── requirements.txt    # Python dependencies
│
└── frontend/
    └── index.html          # React frontend application (self-contained)
```


## 🛠️ Technology Stack

- ### Backend:

    - **Framework:** FastAPI

    - **Language:** Python

    - **Database:** PostgreSQL

    - **ORM:** SQLAlchemy

    - **Authentication:** Google OAuth 2.0

- ### Frontend:

    - **Library:** React

    - **Styling:** Tailwind CSS

## 🚀 Current Status: MVP Achieved
This project is currently at the **Minimum Viable Product (MVP)** stage. The core data pipeline is fully functional.

### Core Features (MVP)
- ✅ Google Authentication: Securely authenticate users via Google's OAuth 2.0 flow.

- ✅ Google Calendar Integration: Fetch events from a user's primary Google Calendar.

- ✅ Data Normalization: Transform raw event data from the Google API into a standardized internal schema.

- ✅ Database Storage: Persist normalized events in a PostgreSQL database, with logic to update existing events and insert new ones (upsert).

- ✅ Frontend Display: A simple React-based frontend to display the fetched events to the user.

## ⚙️ Setup and Installation
Follow these steps to run the project locally.

### **1. Prerequisites**
    - Python 3.8+

    - PostgreSQL server installed and running.

    - A Google Cloud Platform (GCP) account.

### **2. Backend Setup**

1. **Clone the repository and navigate to the backend directory.**

2. **Create Google Cloud Credentials:**

    - Go to the Google Cloud Console.

    - Create a new project.

    - In the navigation menu, go to "APIs & Services" -> "Enabled APIs & services" and enable the Google Calendar API.

    - Go to "APIs & Services" -> "Credentials".

    - Click "+ CREATE CREDENTIALS" and select "OAuth client ID".

    - Choose "Web application" as the application type.

    - Under "Authorized redirect URIs", add http://localhost:8000/auth/google/callback.

    - Click "Create". Copy the Client ID and Client Secret.

3. **Configure Environment Variables:**

    - Open `backend/main.py1.

    - Replace `'YOUR_GOOGLE_CLIENT_ID'` with your actual Client ID.

    - Replace `'YOUR_GOOGLE_CLIENT_SECRET'` with your actual Client Secret.

4. **Setup Database:**

    - Ensure your PostgreSQL server is running.

    - Create a new database (e.g., `calendar_db`).

    - Update the `DATABASE_URL` string in `main.py` with your PostgreSQL username, password, and database name.

    ```
    Example:
    DATABASE_URL = "postgresql://myuser:mypassword@localhost/calendar_db"
    ```

5. **Install Dependencies and Run Server:**

```
# Navigate to the backend directory
cd backend/

# Install Python packages
pip install -r requirements.txt

# Run the FastAPI server
uvicorn main:app --reload
```

The backend will be running at `http://localhost:8000`.

### **3. Frontend Setup**

1. **Open the Frontend File:**

    - Navigate to the `frontend` directory.

    - Open `index.html` in your web browser (e.g., Chrome, Firefox).

2. **Using the Application:**

    - Click the **"Login with Google"** button. You will be redirected to the Google consent screen.

    - After authorizing, you will be redirected back to the application.

    - Click the **"Fetch My Events"** button to load and display your calendar events.

## 🗺️ Future Roadmap

With the MVP foundation in place, the next steps will focus on expanding functionality and intelligence.

1. **Expand Data Ingestion:**

    - Integrate with Microsoft Outlook Calendar and Apple iCloud Calendar.

    - Integrate with local event aggregator APIs like Eventbrite and Meetup.

2. **Implement the AI Core:**

    - Build the NLP Engine to process natural language commands.

    - Develop the Conflict & Logic Engine for smart scheduling.

3. **Build the Recommendation Engine:**

    - Implement a system to rank and recommend local events based on user preferences and schedule availability.

4. **Enhance the UI/UX:**

    - Create a more sophisticated calendar view (Week/Month).

    - Build out the agent chat interface.
