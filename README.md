# LangGraph Course Repository

This repository contains educational examples demonstrating LangGraph, a framework for building graph-based workflows with LLMs and other components.

## Notebooks Overview

### 1. **simple_nodes.ipynb**
A foundational notebook that demonstrates the basic building blocks of LangGraph:

- **Concepts Covered:**
  - Creating a `StateGraph` with a typed state dictionary
  - Defining simple node functions that process state
  - Adding sequential edges between nodes
  - Executing the graph with initial input

- **Example Workflow:**
  - Starts with an amount in USD
  - Calculates total in USD (with 8% interest)
  - Converts total USD to INR (₹82 per $1)
  - Returns the final portfolio state

- **Key Takeaway:** Demonstrates how to chain multiple operations in a linear sequence using LangGraph.

---

### 2. **graph_with_condition.ipynb**
Builds upon the simple_nodes example by adding conditional logic and branching:

- **Concepts Covered:**
  - Conditional edges with `conditional_edges()` method
  - Routing logic based on state values
  - Multipath execution (two different conversion paths)
  - Merging multiple execution paths to a common end point

- **Example Workflow:**
  - Calculates total in USD (with 8% interest)
  - Routes to different conversion nodes based on target currency:
    - **INR Path:** Converts USD to INR (₹82 per $1)
    - **EUR Path:** Converts USD to EUR (€8 per $1)
  - Returns the appropriate currency conversion

- **Key Takeaway:** Demonstrates how to create dynamic workflows that branch and merge based on runtime conditions.

---

### 3. **tool_call.ipynb**
Introduces tool calling capabilities in LangGraph, allowing LLMs to interact with external functions:

- **Concepts Covered:**
  - Binding tools to an LLM using `bind_tools()`
  - Creating tool nodes with `ToolNode`
  - Conditional routing based on tool calls using `tools_condition`
  - Executing tool calls and incorporating results into the conversation

- **Example Workflow:**
  - User queries for stock prices (e.g., "What is the price of AAPL stock?")
  - LLM recognizes the intent and calls a custom `get_stock_price` tool
  - Tool returns the price, and LLM generates a final response

- **Key Takeaway:** Shows how to extend LangGraph with external tools for dynamic, function-based interactions.

---

### 4. **tool_call_agent.ipynb**
An advanced example building on tool calling, demonstrating agent-like behavior with persistent state and tool integration:

- **Concepts Covered:**
  - Stateful agent workflows with message history
  - Tool execution in a graph-based agent loop
  - Handling multiple tool calls and responses
  - Integrating LLMs with custom tools for complex tasks

- **Example Workflow:**
  - Maintains conversation state across interactions
  - Processes user queries that require tool usage (e.g., data retrieval)
  - Executes tools and generates coherent responses based on results

- **Key Takeaway:** Illustrates building intelligent agents that can perform actions and maintain context using LangGraph.

---

## Running the Notebooks

1. Ensure you have the required dependencies installed:
   ```bash
   uv sync
   ```

2. For notebooks involving LLM integration (e.g., `chatbot.ipynb`, `tool_call.ipynb`, `tool_call_agent.ipynb`), install Ollama and the required models:
   - Install Ollama: Follow the instructions at [ollama.ai](https://ollama.ai) for your operating system.
   - Pull the necessary models:
     ```bash
     ollama pull qwen2.5:7b  # For Qwen 2.5 7B model
     ollama pull phi3:latest  # If using Phi-3 model
     ```
   - Ensure Ollama is running in the background before executing LLM-related cells.

3. Start a Jupyter server:
   ```bash
   jupyter notebook
   ```

4. Open and run the desired notebook

## Project Structure

```
.
├── chatbot.ipynb              # Advanced LLM-based chatbot using LangGraph
├── simple_nodes.ipynb         # Basic sequential graph workflow
├── graph_with_condition.ipynb # Graph with conditional branching
├── tool_call.ipynb            # Tool calling with external functions
├── tool_call_agent.ipynb      # Agent-like behavior with tools and state
├── main.py                    # Main entry point (if applicable)
├── pyproject.toml             # Project dependencies
└── README.md                  # This file
```

## Technologies Used

- **LangGraph:** Framework for building stateful, multi-actor applications
- **LangChain:** For LLM integration and tool binding
- **Ollama:** Local LLM runtime for running models like Qwen 2.5
- **Python:** 3.11+
- **Jupyter:** For interactive notebook exploration

## Chatbot and Agent Examples

The `chatbot.ipynb`, `tool_call.ipynb`, and `tool_call_agent.ipynb` notebooks showcase advanced LangGraph usage with LLMs:

- **Features:**
  - Uses Ollama-based LLMs (e.g., Qwen 2.5) for conversational AI
  - Maintains conversation state within graphs
  - Integrates external tools for dynamic interactions
  - Demonstrates agent-like behavior with tool calling and state management

> Refer to the respective notebooks for step-by-step walkthroughs of building conversational workflows and tool-integrated agents.
