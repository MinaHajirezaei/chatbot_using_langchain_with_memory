# 🤖 LangChain Chatbot with Memory

A conversational AI chatbot powered by **LangChain**, **OpenAI GPT-3.5**, and session-based memory — just like ChatGPT, but in your own hands!

---

## 📌 Features

- 💬 Chatbot with **contextual memory** (remembers your name and past messages)
- 🧠 Built with **LangChain Expression Language (LCEL)**
- 🔑 Integrates **OpenAI GPT-3.5**
- 🔄 Memory support via `InMemoryChatMessageHistory`
- 🧪 Ideal for testing multi-user chat sessions
- 📊 Compatible with **LangSmith** for logging and debugging

---

## 🚀 Installation

```bash
pip install -q langchain
pip install -q langchain-community
pip install -q openai
```

---

## 🔐 Environment Setup

Make sure you set your OpenAI API key:

```python
import os
os.environ["OPENAI_API_KEY"] = "sk-..."  # Replace with your real key
```

---

## 🧱 Core Components

- `ChatOpenAI`: LLM interface to GPT-3.5
- `ChatPromptTemplate`: Custom chat prompt with dynamic message injection
- `MessagesPlaceholder`: Enables streaming in message history
- `InMemoryChatMessageHistory`: Stores messages per session ID

---

## 🧪 Example Conversation

```python
from langchain.schema import HumanMessage, AIMessage

messages = [
    HumanMessage(content="Hi! I'm Mina"),
    AIMessage(content="Hello Mina! How can I assist you today?"),
    HumanMessage(content="What's my name?")
]

response = chain.invoke({"messages": messages})
print(response.content)
# Output: Your name is Mina.
```

---

## 🧠 Multi-session Memory (Advanced)

Each user/session is tracked with a unique `session_id`:

```python
store = {}  # Dictionary to hold multiple user conversations

def get_session_history(session_id: str):
    if session_id not in store:
        store[session_id] = InMemoryChatMessageHistory()
    return store[session_id]
```

This allows memory separation between `firstchat`, `secondchat`, etc.

---

## 🧰 Tools & Tracing

To enable LangSmith tracing and logging:

```python
os.environ["LANGCHAIN_TRACING_V2"] = "true"
os.environ["LANGCHAIN_API_KEY"] = "your-langsmith-key"
os.environ["LANGCHAIN_PROJECT"] = "my-chatbot-project"
```

---

## 📸 Screenshot

*(Optional: Add screenshots of LangSmith logs, chatbot UI if any)*

---

## 📌 Next Steps

- 🔄 Connect to vector DB for RAG (Retrieval Augmented Generation)
- 🧩 Add tool usage or API calling with Agents
- 🌐 Deploy with Streamlit or Gradio

---

## 📜 License

MIT License — free for personal and commercial use.

---

## 🙌 Credits

Built with ❤️ using:
- [LangChain](https://www.langchain.com/)
- [OpenAI](https://platform.openai.com/)
- [LangSmith](https://smith.langchain.com/)
