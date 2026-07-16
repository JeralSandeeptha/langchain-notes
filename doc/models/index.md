# Chat Models

`Chat models in LangChain are wrappers around large language models that take a sequence of structured messages as inputs and return a message as output`

Unlike legacy, plaintext LLMs that only process raw strings, chat models utilize distinct "roles" to organize conversation history, frame instructions, and retain context.

---

## Key Characteristics

`Message-In`, `Message-Out`: They accept a list of message objects and return an AIMessage containing the generated text.

`Unified Interface`: LangChain provides a standardized interface (BaseChatModel) that lets you switch between different underlying providers seamlessly without rewriting core logic.

`Advanced Features`: Modern chat models support native tools like structured outputs, multimodal inputs (images and video), and tool calling (function calling).

<br/>

## Comparison: Chat Models vs. Traditional LLMs

| Feature | Chat Models (BaseChatModel) | Traditional LLMs (BaseLLM) |
| :--- | :--- | :--- |
| **Input Format** | List of message objects or tuples | Single raw text string |
| **Output Format** | Structured message (AIMessage) | Raw text string |
| **Context Awareness** | Built-in support for conversational history | Requires manual text formatting/cloning |
| **Modern Capabilities** | Native tool-calling and multimodal input | Primarily text completion |

<br/>

## Setup Chat Model

1. Pick a Provider (`OpenAI`, `Gemini`)
2. Get relavant `API KEY`
3. Set `API KEY` as a env (Use standard api key names for get key automatically) / (`OPENAI_API_KEY`)
4. Funded your account with money before usage

```python
from langchain_openai import ChatOpenAI

model = ChatOpenAI(model="gpt-4")

response = model.invoke("Who is the president of France")

print(response.content)
```

<br/>

## Runnables

Read more about [Runnables](./runnables.md)

<br/>

## Message Types

Read more about [Message Types](./message-types.md)
