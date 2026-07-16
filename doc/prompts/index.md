# Prompt Templates

Prompts are build with messages

`Prompt Templates` are blueprints for prompts

These are:

- `String Templates` (for `plain text` LLMs)
- `Chat Templates` (for `role-based chat` models) - `Few-Shot Templates` (for `providing examples`)

---

## 1. String-Based Templates (Completion Models)

These are ideal for legacy text-completion models that accept a singular string instead of structured role-based arrays.

`PromptTemplate`: A basic wrapper for string formatting. It dynamically replaces named placeholders enclosed in curly brackets (e.g., {topic}). It natively supports f-string, mustache, and jinja2 parsing formats.

## 2. Chat-Based Templates (Chat Models)

Designed for conversational architectures where the API expects an array of messages grouped by system, assistant, or user origins.

`ChatPromptTemplate`: Acts as a high-level array container that bundles multiple individual message templates together into a cohesive conversation sequence.

`Role-Specific Single Templates`: Dedicated sub-classes ensuring individual strings carry explicit structural boundaries:

- `SystemMessagePromptTemplate` (structural or behavioral instructions)
- `HumanMessagePromptTemplate` (user-facing inquiries)
- `AIMessagePromptTemplate` (historical or pre-baked model replies)

`MessagesPlaceholder`: A crucial structural variant that acts as a blank placeholder inside a message stream. It allows you to dynamically inject full arrays of historical message streams at runtime, handling conversation memory seamlessly.

## 3. Few-Shot Templates (Contextual Learning)

Used when a model needs in-context training examples to learn custom behavior before receiving the main user request.

`FewShotPromptTemplate`: Builds string-based prompts containing a static or dynamic collection of input-output examples formatted using an ExampleSelector.

`FewShotChatMessagePromptTemplate`: Constructed specifically for role-based chat models. It formats a structured array of explicit user/assistant sample pairs to append gracefully into conversation arrays.

<br/>

## Summary

| Template Class | Underlying Format Type | Best Used For |
| :--- | :--- | :--- |
| **`PromptTemplate`** | Flat Plain String | Simplistic variable mapping or completion models. |
| **`ChatPromptTemplate`** | Structured Message List | Constructing multi-turn system/user conversations. |
| **`MessagesPlaceholder`** | Variable Dynamic List | Injecting conversational memory objects safely. |
| **`FewShotPromptTemplate`** | Examples + Final Prompt | Training completion models with functional demonstrations. |
| **`FewShotChatMessagePromptTemplate`** | Examples + Message List | Training chat-based models with role-specific demonstrations. |
