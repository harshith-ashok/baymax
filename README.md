# Baymax

This is a **Baymax-inspired personal healthcare chatbot** that I built to simulate a friendly, caring, and interactive medical assistant. The system uses **Llama 3.2 via Ollama** for natural language understanding and reasoning, and a **FastAPI backend** to handle chat requests. The frontend is a **SvelteKit app** with a ChatGPT-like interface, styled using **Tailwind CSS** and **DaisyUI**.

---

## Features

- **Baymax-style conversation**: Polite, calm, and empathetic responses strictly in the tone of Baymax from _Big Hero 6_.
- **Dynamic questioning**: Asks the user whether they are physically or emotionally in pain, ranks the pain, and follows up with clarifying questions.
- **Stateful chat sessions**: Remembers previous messages per session so the conversation flows naturally.
- **Easy integration with web frontend**: SvelteKit app with ChatGPT-like interface for real-time chat.
- **CORS enabled**: Allows smooth communication between the frontend and backend.

---

## Tech Stack

- **Backend**: Python, FastAPI, Requests
- **Language Model**: Llama 3.2 via Ollama
- **Frontend**: SvelteKit, Tailwind CSS, DaisyUI
- **Communication**: REST API (`/chat`)

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/baymax-chatbot.git
cd baymax-chatbot
```

### 2. Backend Setup

1. Make sure **Ollama** is installed and running locally.
2. Pull the Llama 3.2 model:

```bash
ollama pull llama3.2
```

3. Install Python dependencies:

```bash
pip install fastapi uvicorn requests
```

### 3. Run the backend

```bash
uvicorn main:app --reload --port 8000
```

The backend API will be available at `http://127.0.0.1:8000/chat`.

---

### 4. Frontend Setup

1. Navigate to your SvelteKit frontend directory:

```bash
cd frontend
```

2. Install dependencies:

```bash
npm install
```

3. Start the development server:

```bash
npm run dev
```

4. Open your browser at `http://localhost:5173` (or the port SvelteKit shows) and start chatting with Baymax.

---

## Usage

- The chatbot **always begins** by asking:
  `"Are you physically or emotionally in pain?"`
  and then: `"On a scale of 1 to 10, how would you rate your pain?"`

- Based on your responses, Baymax will **ask follow-up questions** to help narrow down the issue and provide a recommendation.

- Multiple users can chat simultaneously using **session IDs**, ensuring each conversation stays independent.

---

## Example API Request

```bash
curl -X POST "http://127.0.0.1:8000/chat" \
-H "Content-Type: application/json" \
-d '{"session_id": "user123", "message": "Hello Baymax"}'
```

Response:

```json
{
  "reply": "Are you physically or emotionally in pain? On a scale of 1 to 10, how would you rate your pain?"
}
```

---

## Notes

- The system is **stateful**, meaning it remembers previous messages in a session.
- Designed for **educational and demo purposes** — not a substitute for real medical advice.
- Frontend UI uses **DaisyUI components** for chat bubbles, buttons, and input fields for a clean, interactive experience.

---

## Future Improvements

- Add **automatic session cleanup** to prevent memory bloat.
- Extend to handle **image-based health inputs** (e.g., X-rays, retina scans, blood smears).
- Add **speech-to-text** and **text-to-speech** for a more interactive Baymax experience.

---

## License

MIT License © 2025 Harshith Ashok
