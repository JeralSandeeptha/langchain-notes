# Augment LLM with Tools

```pwd
Model should supports tool calling
```

```python
from langchain_openai import ChatOpenAI
from langchain_core.tools import tool

# Create Tools
@tool
def get_weather(city: str) -> str:
    """Get the weather for a city"""
    
    weather_data = {
        "New York": "Sunny, 72 F",
        "London": "Cloudy, 15 F",
        "Tokyo": "Rainy, 20 C"
    }
    
    return weather_data.get(city, "Weather data not available")

@tool
def calculate_tip(bill_amount: float, tip_percentage: float) -> float:
    """Calculate tip amount nased on bill and percentage"""
    
    return round(bill_amount * (tip_percentage/100), 2)

# LLM should supports tool calling
llm = ChatOpenAI(model="gpt-4o")

# Bind the tools
llm_with_tools = llm.bind_tools([
    get_weather,
    calculate_tip
])

weather_prompt = "What's the weather in Tokyo"
tip_prompt = "Calculate a 20% tip on a $50 bill"

response = llm_with_tools.invoke(weather_prompt)

tool_calls = response.tool_calls

print(tool_calls)
```
