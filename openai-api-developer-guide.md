# OpenAI API Developer Guide

*Sample API documentation created for technical writing portfolio purposes.*

---

## 📌 What is the OpenAI API?

The **OpenAI API** provides access to advanced AI models for tasks such as:
- Text generation
- Summarization
- Translation
- Embeddings
- Code generation
- Conversational AI (chatbots)

🌐 [https://platform.openai.com/docs](https://platform.openai.com/docs)

---

## 🌐 Base URL

```
https://api.openai.com/v1/
```

---

## 🔐 Authentication

All requests to the OpenAI API require an API key.  
Include it in the `Authorization` header as a Bearer token.

Example header:
```
Authorization: Bearer YOUR_API_KEY
```

---

## 📖 Key Endpoints Overview

| Endpoint             | Purpose                           |
|----------------------|-----------------------------------|
| `/completions`        | Generate or complete text         |
| `/chat/completions`   | Create chat-like conversations    |
| `/edits`              | Edit existing text                |
| `/embeddings`         | Get vector embeddings of text     |
| `/models`             | List available models             |

---

## 🚀 Example Request: Completion

**HTTP request:**
```http
POST https://api.openai.com/v1/completions
Content-Type: application/json
Authorization: Bearer YOUR_API_KEY
```

**Request body:**
```json
{
  "model": "text-davinci-003",
  "prompt": "Write a short poem about the ocean.",
  "max_tokens": 50
}
```

**Sample response:**
```json
{
  "id": "cmpl-abc123",
  "object": "text_completion",
  "created": 1234567890,
  "model": "text-davinci-003",
  "choices": [
    {
      "text": "The ocean waves roll to the shore\nA melody forevermore...",
      "index": 0,
      "finish_reason": "length"
    }
  ]
}
```

---

## 🧑‍💻 Example in Python

```python
import requests

url = "https://api.openai.com/v1/completions"
headers = {
    "Content-Type": "application/json",
    "Authorization": "Bearer YOUR_API_KEY"
}
data = {
    "model": "text-davinci-003",
    "prompt": "Write a short poem about the ocean.",
    "max_tokens": 50
}

response = requests.post(url, headers=headers, json=data)

if response.status_code == 200:
    result = response.json()
    print(result["choices"][0]["text"])
else:
    print("Error:", response.status_code, response.text)
```

---

## ⚠️ Error Handling

Common status codes:
- `200 OK` — Request successful  
- `400 Bad Request` — Invalid input  
- `401 Unauthorized` — Missing/invalid API key  
- `429 Too Many Requests` — Rate limit exceeded  
- `500 Internal Server Error` — Server issue  

---

## 💡 Notes

- All responses are JSON formatted.  
- The API uses rate limits based on your plan.  
- Sensitive data should not be shared in prompts.  
- Pricing is based on tokens processed — see OpenAI pricing docs.  

---

## 📄 License / Disclaimer

This documentation is a writing sample for portfolio use only.  
It is not affiliated with OpenAI.
