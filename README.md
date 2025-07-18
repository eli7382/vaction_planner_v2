PersonalTripPlanner

A dynamic web application for generating fully personalized travel itineraries, tailored exactly to each user's needs and situation. The platform leverages state-of-the-art AI via two APIs:

A Prompt Generation API: Interprets user requirements and context to create an optimized prompt for research.

A Deep Research API: Consumes the prompt and delivers a comprehensive, individualized trip plan.


Features

User-Centric: Plans are custom-built for each user’s specific profile, constraints, and preferences.

Multi-API Architecture: Decouples prompt engineering from deep itinerary generation for modularity and flexibility.

Real-Time Personalization: Immediate adaptation based on user inputs or changing constraints.

Modern UX/UI: Clean, responsive design for web and mobile.


Architecture

User → [Frontend] → Prompt Generation API → Deep Research API → [Frontend]

Frontend: Collects user data (destination, dates, travelers, budget, special requirements, etc.) and interacts with APIs.

Prompt Generation API: Receives structured user data, applies business logic and context rules, outputs a high-quality prompt.

Deep Research API: Consumes the prompt, performs in-depth research (e.g., using LLMs, web scraping, travel data), returns a multi-day itinerary tailored to the user.


How It Works

1. Input Collection: User fills a form specifying all relevant travel needs and preferences.


2. Prompt Generation: The prompt API transforms this input into a detailed, context-aware prompt for the research API.


3. Deep Research: The research API returns a custom plan (itinerary, tips, bookings, etc.), fully matching the user's scenario.


4. Output & Customization: The user receives a structured plan, with options to further edit or refine results.



API Overview

1. Prompt Generation API

Endpoint: /api/prompt

Input: Structured JSON (user profile, trip specs, constraints, goals)

Output: Optimized natural-language prompt


Example Request

{
  "destination": "Japan",
  "dates": { "start": "2025-08-10", "end": "2025-08-25" },
  "travelers": [ { "age": 40, "needs": ["wheelchair"] }, { "age": 12 } ],
  "interests": ["culture", "nature", "food"],
  "budget": "medium"
}

Example Response

{
  "prompt": "Create a detailed 15-day itinerary for a family traveling to Japan, with accessibility needs, focused on culture, nature, and food, within a medium budget..."
}

2. Deep Research API

Endpoint: /api/research

Input: Prompt (natural language)

Output: Full, multi-day itinerary (structured JSON or Markdown)


Example Request

{
  "prompt": "Create a detailed 15-day itinerary for a family traveling to Japan..."
}

Example Response

{
  "itinerary": [
    {
      "day": 1,
      "location": "Tokyo",
      "activities": ["Senso-ji Temple", "Asakusa street food tour"],
      "notes": "Wheelchair accessible, local guides available..."
    }
    // ...
  ]
}

Running Locally

1. Clone this repo:

git clone https://github.com/yourusername/PersonalTripPlanner.git
cd PersonalTripPlanner


2. Install dependencies:

npm install


3. Configure API keys and endpoints in .env (see .env.example).


4. Run the development server:

npm run dev


5. Open your browser at http://localhost:3000.



Customization

User Profile: The prompt generator considers all relevant user context.

Dynamic Rules: Add or adjust prompt rules in prompt-rules.json (or relevant config).

API Swap: Supports swapping to different prompt or research APIs as needed.


Roadmap

[ ] User accounts and persistent plans

[ ] Real-time feedback/plan adjustment UI

[ ] Integrations with booking APIs

[ ] Multilingual support


License

MIT License (see LICENSE)


---

Built with ❤️ by [Your Name].
Pull requests and feedback welcome!
