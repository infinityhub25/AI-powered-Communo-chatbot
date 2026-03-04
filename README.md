# AI-powered-Communo-chatbot
An AI-powered conversational chatbot built using NLP and Dialogflow that allows users to order food through natural language interaction. The chatbot understands user intents, extracts entities like food items and quantities, manages conversation context, and processes orders in real-time through a backend webhook integration.

Table of Contents
Project Overview
Features
Flow
Tech Stack
How it works
API/Webhook Details
Example Conversations


📖 Project Overview
This project simulates an automated food ordering assistant for restaurants or food delivery platforms. The chatbot interacts with users conversationally and allows them to:
Add food items
Remove or modify items
Confirm orders
Track orders
The backend processes logic such as order management and response generation, while Dialogflow handles NLP tasks like intent classification and entity extraction.

Features
Natural Language Understanding using Dialogflow
Add, remove, update food items
Multi-turn, context-aware conversations
Real-time order confirmation
Webhook-based backend integration
Fallback intent handling
REST API communication
Session-based order state management

Flow Explanation:
User sends a message.
Dialogflow detects intent & extracts entities.
Webhook sends request to FastAPI backend.
Backend processes order logic.
Response is returned to Dialogflow.
Dialogflow replies to the user.

🛠️ Tech Stack
Technology	Purpose
Dialogflow	NLP, Intent detection
Python	Backend logic
FastAPI	Webhook service
ngrok	Local HTTPS tunnel
REST APIs	Communication protocol



 How It Works
🔹 Intent Detection

Dialogflow identifies user intent such as:
order.add
order.remove
order.confirm
order.track

🔹 Entity Extraction
Entities include:
Food item name
Quantity

🔹 Context Handling
The chatbot maintains session context to:
Continue incomplete orders
Ask clarification questions
Track order status

💬 Example Conversation
User: I want 2 burgers and 1 pizza
Bot: Added 2 burgers and 1 pizza to your order. Anything else?
User: Remove 1 burger
Bot: Updated your order. You now have 1 burger and 1 pizza.
User: Confirm order
Bot: Your order has been placed successfully! 🍔

🔗 API / Webhook Details

Endpoint:

POST /webhook

Request Format: (from Dialogflow)

{
  "queryResult": {
    "intent": { "displayName": "order.add" },
    "parameters": {
      "food-item": "pizza",
      "number": 2
    }
  }
}

Response Format:

{
  "fulfillmentText": "Added 2 pizzas to your order."
}
