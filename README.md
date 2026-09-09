# AI E-Commerce Customer Support Agent

An agentic AI customer support system for e-commerce. This project uses an AI agent to understand customer requests, retrieve relevant policy information, and perform backend actions such as order lookup, return initiation, inventory checks, and human escalation.

## Features

- AI-powered customer support
- Order status lookup
- Return and refund assistance
- Product and policy questions
- Inventory availability checking
- Human agent escalation
- Retrieval-Augmented Generation (RAG)
- Conversational memory
- FastAPI backend
- HTML, CSS and JavaScript frontend
- Ollama support for local AI
- Automated testing

## Project Structure

```text
ai-ecommerce-support-agent/
│
├── backend/
│   ├── data/
│   │   ├── knowledge_base/
│   │   │   ├── faq.md
│   │   │   ├── return_policy.md
│   │   │   └── shipping_policy.md
│   │   ├── inventory.json
│   │   └── orders.json
│   │
│   ├── agent_ollama.py
│   ├── agent.py
│   ├── main.py
│   ├── models.py
│   ├── rag.py
│   ├── tools.py
│   └── requirements.txt
│
├── frontend/
│   ├── chat.js
│   ├── index.html
│   └── style.css
│
├── tests/
│   └── test_agent.py
│
├── .env.example
├── .gitignore
└── README.md
```

## Architecture

```text
Customer
    ↓
Frontend Chat Interface
    ↓
FastAPI Backend
    ↓
AI Agent
    ↓
┌─────────────────────────┐
│      AI Reasoning       │
└─────────────────────────┘
    ↓
┌────────────┬────────────┐
│    RAG     │   Tools    │
│            │            │
│ FAQ        │ Order      │
│ Policies   │ Return     │
│ Knowledge  │ Inventory  │
└────────────┴────────────┘
    ↓
AI Response
    ↓
Customer
```

## Technologies Used

- Python
- FastAPI
- Ollama
- Large Language Model (LLM)
- Retrieval-Augmented Generation (RAG)
- TF-IDF
- HTML
- CSS
- JavaScript
- JSON
- Pytest

## Prerequisites

Install the following:

- Python 3.10 or higher
- Ollama
- Git
- VS Code

## Install Ollama

Download and install Ollama:

https://ollama.com

Check the installation:

```bash
ollama --version
```

Start Ollama:

```bash
ollama serve
```

Open another terminal and download the AI model:

```bash
ollama pull llama3.1
```

## Setup

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/ai-ecommerce-support-agent.git
```

Go to the project folder:

```bash
cd ai-ecommerce-support-agent
```

## Configure Environment

Create the environment file.

### Windows

```powershell
Copy-Item .env.example backend\.env
```

Open:

```text
backend/.env
```

Add:

```env
LLM_PROVIDER=ollama
OLLAMA_MODEL=llama3.1
```

## Create Virtual Environment

Go to the backend:

```bash
cd backend
```

Create a virtual environment:

```bash
python -m venv venv
```

### Windows

```powershell
venv\Scripts\activate
```

### Mac/Linux

```bash
source venv/bin/activate
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

## Run the Backend

From the `backend` folder:

```bash
python main.py
```

The backend server will run at:

```text
http://localhost:8000
```

Health check:

```text
http://localhost:8000/health
```

FastAPI documentation:

```text
http://localhost:8000/docs
```

## Run the Frontend

Open a second terminal.

Go to the frontend folder:

```bash
cd frontend
```

Start the frontend server:

```bash
python -m http.server 5500
```

Open the application:

```text
http://localhost:5500
```

## Example Queries

Try these questions in the chat:

```text
Where is my order ORD-10234?
```

```text
I want to return order ORD-10236 because the pan set arrived scratched.
```

```text
Is the Smart Fitness Watch in stock?
```

```text
What is your return policy?
```

```text
I want to speak to a human agent.
```

## Knowledge Base

The RAG system uses the following knowledge-base documents:

- `faq.md`
- `return_policy.md`
- `shipping_policy.md`

These documents contain store policies and customer support information.

## API

### POST /chat

Example request:

```json
{
  "session_id": "abc-123",
  "message": "Where is my order ORD-10234?"
}
```

Example response:

```json
{
  "session_id": "abc-123",
  "reply": "Your order ORD-10234 has shipped via BlueDart.",
  "escalated": false,
  "tool_calls": [
    {
      "tool_name": "get_order_status",
      "tool_input": {
        "order_id": "ORD-10234"
      }
    }
  ]
}
```

### POST /reset

Clears the conversation memory for a session.

## Running Tests

From the backend folder:

```bash
pip install pytest
pytest ../tests/
```

The tests cover the tools and RAG functionality.

## Customer Support Scenarios

### Order Tracking

The customer provides an order ID and the AI agent retrieves the order status from the order database.

### Return Request

The agent processes a customer's return request using the return functionality.

### Inventory Check

The agent checks the inventory database to determine whether a product is available.

### Policy Question

The RAG system retrieves relevant information from the knowledge base before generating a response.

### Human Escalation

Complex or sensitive requests can be escalated to a human support agent.

## Future Improvements

- Voice-based customer support
- Multilingual support
- WhatsApp integration
- Real-time shipment tracking
- Personalized customer responses
- Real payment and refund integration
- Production vector database
- Redis-based conversation memory
- Analytics dashboard
- Proactive delivery notifications

## Security

This project is intended for learning and demonstration purposes.

Before production deployment:

- Add authentication
- Protect customer information
- Add rate limiting
- Add logging and monitoring
- Use a production database
- Replace mock JSON databases with real APIs
- Add proper ticketing system integration
- Protect API keys and environment variables

## License

MIT License

This project is intended for learning, experimentation, and further development.
