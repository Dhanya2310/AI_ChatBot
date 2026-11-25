# ChatAI

A responsive AI chatbot built with Next.js, React, Tailwind CSS, and the Google Gemini API. It supports multi-topic conversations, in-chat memory, Markdown responses, loading states, and error handling.

## Setup

1. Install dependencies:

   ```bash
   npm install
   ```

2. Create a `.env.local` file in the project root and add your API key:

   ```env
   GEMINI_API_KEY=your_api_key_here
   ```

   Optionally override the model (defaults to `gemini-3.5-flash-lite`):

   ```env
   GEMINI_MODEL=gemini-3.5-flash-lite
   ```

   The key is read only on the server in `app/chat/route.js` and `.env*` files are gitignored. Never expose it in client code.

3. Start the development server:

   ```bash
   npm run dev
   ```

   Open [http://localhost:3001](http://localhost:3001).

## How it works

- `app/page.js` renders the chat UI and keeps the conversation in React state.
- `app/chat/route.js` is a server route that calls Gemini with the conversation history and a system prompt defining the assistant's behaviour.
- Previous messages are sent with each request so the assistant remembers the current chat. History resets when the page is refreshed or "New chat" is clicked.
- AI replies are rendered as Markdown with GitHub-style tables and fenced code blocks.

## Scripts

- `npm run dev` — start the development server
- `npm run build` — create a production build
- `npm start` — serve the production build
- `npm run lint` — run ESLint
