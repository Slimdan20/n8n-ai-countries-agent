# DOX - AI Documentation Assistant

Dox is an AI documentation assistant built with n8n and Groq. It fetches the [Rest Countries](https://app.swaggerhub.com/apis/d1corps/REST-Countries-API/1.0.0) OpenAPI specification from SwaggerHub in real time, allowing developers to ask natural language questions about the API and receive structured responses strictly from the API specification, rather than from external knowledge.

Dox is useful for exploring the API endpoints, understanding request formats, and getting implementation details without manually readinng through documentation.

https://github.com/user-attachments/assets/65c90dad-1c6e-4aca-b08d-3417dd5e1669

## Why I built this

Developers often need quick answers from API documentation without manually searching through large OpenAPI specifications.

I built Dox to explore whether a lightweight workflow using n8n and Groq could act as a documentation assistant by retrieving a live OpenAPI specification, grounding responses in that specification, and maintaining conversational context across follow-up questions.

## How it works

- A user sends a question through the chat interface
- The workflow retrieves the Rest Countries OpenAPI specification
- The specification is injected into the AI agent's system prompt
- The Groq model generates an answer using only the API specification
- Memory allows the assistant to handle follow-up questions naturally

## Features

- Dynamically fetches OpenAPI/Swagger specifications at runtime
- Answers questions directly from API documentation
- Prevents hallucinations through specification-grounded responses
- Maintains conversational context using memory-based chat history
- Supports follow-up questions without requiring users to repeat context
- Generates structured responses with endpoint details, request examples, and code samples
- Built entirely with n8n and Groq's Llama 3.3 70B model
- No vector database or external retrieval infrastructure required

## Architecture

```text
User Question
      │
      ▼
n8n Chat Trigger
      │
      ▼
Fetch OpenAPI Spec
      │
      ▼
   AI Agent
      │
 ┌────┴────┐
 ▼         ▼
Memory   Groq LLM
      │
      ▼
Structured Response
```

## Tech stack

- n8n for workflow automation
- Groq (Llama 3.3-70b) as the language model
- SwaggerHub for OpenAPI spec hosting
- Rest Countries API
