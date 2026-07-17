# Output Parsers

`Output Parsers` in LangChain are classes designed to bridge the gap between unstructured AI responses and the structured data your application needs.

They append formatting instructions to your prompt and parse the raw LLM output into predictable data formats like JSON, Python dictionaries, lists, or strict Pydantic models.

- `PydanticOutputParser`: Enforces a strict data schema using a Pydantic model. It handles both parsing and type validation.

- `JsonOutputParser`: Parses responses directly into JSON objects or Python dictionaries.

- `CommaSeparatedListOutputParser`: Takes a comma-separated text response and converts it into a clean Python list.XMLOutputParser: Formats instructions for XML tags and parses the resulting text into an XML dictionary.

- `StrOutputParser`: The simplest parser. It strips metadata from the model's message (like AIMessage objects) and extracts the raw string. It supports streaming text.

- `StructuredOutputParser`: Allows you to define custom response schemas as a list, helpful if you are working with text-only prompts and need key-value formatting.

---

## Example

```python
from typing import List
from pydantic import BaseModel, Field
from langchain_openai import ChatOpenAI

# 1. Define your desired output structure using Pydantic
class ActorMovieBio(BaseModel):
    name: str = Field(description="The actor's full name")
    birth_year: int = Field(description="Year the actor was born")
    famous_movies: List[str] = Field(description="List of top 3 famous movies they starred in")

# 2. Initialize the model
model = ChatOpenAI(model="gpt-4o", temperature=0)

# 3. Bind the schema directly to the model
structured_llm = model.with_structured_output(ActorMovieBio)

# 4. Invoke the model
result = structured_llm.invoke("Tell me about Tom Hanks")

# The output is immediately a typed Python object
print(type(result))          # <class '__main__.ActorMovieBio'>
print(result.name)           # Tom Hanks
print(result.birth_year)     # 1956
print(result.famous_movies)  # ['Forrest Gump', 'Saving Private Ryan', 'Toy Story']
```