## Authors

Navaneeth Sankar K P, Aditi Chaware, Anarva Ghosh, Krishna Gupta of MIT Institute of Design, Pune, India.
Mentored under Prof. Aryan Halkude.

## Project Overview

This is a sophisticated AI Assistant web application built with **React and TypeScript**, utilizing **Google's Gemini model** for core intelligence and **Supabase Edge Functions** for a secure, scalable backend. It features multimodal capabilities, allowing users to interact via **text, voice, and image uploads**, and includes customizable conversational tones.

* **Live Project URL**: [https://lovable.dev/projects/95f6df09-28ee-4e55-a582-855308796326](https://lovable.dev/projects/95f6df09-28ee-4e55-a582-855308796326)
* **Lovable Project ID**: `95f6df09-28ee-4e55-a582-855308796326`

***

## Key Features

The AI Assistant is designed to be a comprehensive conversational tool, offering several modes of interaction:

1.  **Multimodal Chat**
    * **Text Chat**: Send messages using the text input field.
    * **Vision (Image Analysis)**: Use the **`Paperclip`** icon to upload an image or capture a photo with your camera. The image is sent for detailed analysis using the Gemini model.
    * **Voice Input (Speech-to-Text)**: Use the **`Mic`** icon to enable the **browser's Web Speech API** for hands-free input.
    * **Voice Output (Text-to-Speech)**: If you use voice input, the assistant will automatically read its response back to you using the **browser's `speechSynthesis` API**.

2.  **Customizable AI Tone**
    You can adjust the AI's persona, which modifies the system prompt sent to the model. Access this via the emoji button (e.g., 😊) in the header.
    * **Friendly** (😊): Casual, warm, and approachable.
    * **Professional** (👔): Formal, structured, and precise.
    * **Creative** (🎨): Imaginative, witty, and expressive.
    * **Concise** (⚡️): Direct, brief, and to-the-point.

3.  **Theming**
    * Toggle between **Light (☀️)** and **Dark (🌙)** modes with a single click in the header. The theme preference is persisted using `localStorage`.

***

## Technology Stack

This project is built using modern web development standards and a powerful serverless backend:

### Frontend
* **Framework**: **React**
* **Language**: **TypeScript**
* **Build Tool**: **Vite**
* **UI Components**: **shadcn-ui** (based on Radix UI primitives)
* **Styling**: **Tailwind CSS** with custom HSL color variables for easy theming and specific bubble colors (`--assistant-bubble`, `--user-bubble`).
* **State Management/Routing**: `@tanstack/react-query`, `react-router-dom`

### Backend (AI & Data)
* **Serverless Platform**: **Supabase Edge Functions**
* **AI Models**:
    * **Chat & Vision**: **Google Gemini 2.5 Flash** (via the Lovable AI Gateway)
    * **Speech-to-Text**: OpenAI Whisper API
* **Database**: Supabase (Used for Edge Functions deployment and configuration)

***

## Setup and Installation

### Prerequisites
* Node.js & npm (or equivalent like Bun/Yarn)
* A Lovable API Key and an OpenAI API Key (for full functionality)

### Local Development
1.  **Clone the Repository**:
    ```sh
    git clone <YOUR_GIT_URL>
    cd navuxneeth/gemini-assistant-suite/gemini-assistant-suite-13d17f6438daf9696915373fed2ccf99717423e4
    ```

2.  **Install Dependencies**:
    ```sh
    npm install # or bun install / yarn install
    ```
    * *(Note: The project uses various packages including `embla-carousel-react`, `recharts`, and several `@radix-ui/react-*` libraries as detailed in `package.json`.)*

3.  **Configure Environment Variables**:
    Create a local `.env` file in the root directory to match the structure in the provided configuration.

    ```env
    # Supabase Client Details (from .env file)
    VITE_SUPABASE_PROJECT_ID="whjfxdumvxlzwtsyhqhd"
    VITE_SUPABASE_PUBLISHABLE_KEY="<YOUR_SUPABASE_PUBLISHABLE_KEY>"
    VITE_SUPABASE_URL="[https://whjfxdumvxlzwtsyhqhd.supabase.co](https://whjfxdumvxlzwtsyhqhd.supabase.co)"
    ```
    * *You will also need to configure your Supabase Edge Functions with the necessary AI API keys (`LOVABLE_API_KEY` and `OPENAI_API_KEY`) to run the backend logic.*

4.  **Start the Development Server**:
    ```sh
    npm run dev
    ```

***

## API and Backend Configuration

The core logic of the AI assistant resides in three Supabase Edge Functions, utilizing external AI services through API keys set in the serverless environment.

| Function | Purpose | Model / Service | Key Requirement |
| :--- | :--- | :--- | :--- |
| **`chat`** | Handles conversational text requests. | `google/gemini-2.5-flash` via Lovable Gateway | `LOVABLE_API_KEY` |
| **`vision`** | Handles multimodal (image) analysis. | `google/gemini-2.5-flash` via Lovable Gateway | `LOVABLE_API_KEY` |
| **`speech-to-text`** | Converts spoken audio to text. | OpenAI Whisper API | `OPENAI_API_KEY` |

The Supabase project is configured with the ID `whjfxdumvxlzwtsyhqhd`. The frontend establishes its connection using `src/integrations/supabase/client.ts`.
