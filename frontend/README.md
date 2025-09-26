# Frontend (SvelteKit) UI

The frontend is built with **SvelteKit**, featuring a **ChatGPT-like interface** for interacting with Baymax. It uses **Tailwind CSS** for utility-first styling and **DaisyUI** components for a clean, interactive design.

### Features

- **Chat interface**: Input field, send button, and chat bubbles for messages.
- **Responsive layout**: Works well on desktop and mobile.
- **DaisyUI components**: Chat bubbles, buttons, and forms for fast UI development.
- **Real-time interaction**: Sends messages to the FastAPI backend and displays Baymax responses instantly.

### Installation

```bash
cd frontend
npm install
npm run dev
```

Open your browser at `http://localhost:5173`.

### Example Usage

- Type a message into the input box (e.g., `"Hello Baymax"`) and press Enter or click Send.
- Baymax responds according to the **Baymax system prompt**, starting with:
  `"Are you physically or emotionally in pain?"`
- Continue the conversation, and Baymax remembers previous messages in the session.

### Tailwind & DaisyUI Integration

- Tailwind is used for layout, spacing, and typography.
- DaisyUI provides ready-made components for chat bubbles and buttons:

This setup gives a **clean, interactive chat interface** that works seamlessly with the FastAPI backend.
