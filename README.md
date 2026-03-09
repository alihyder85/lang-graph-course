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

## Running the Notebooks

1. Ensure you have the required dependencies installed:
   ```bash
   uv sync
   ```

2. Start a Jupyter server:
   ```bash
   jupyter notebook
   ```

3. Open and run the desired notebook

## Project Structure

```
.
├── chatbot.ipynb              # (Advanced example - LLM-based chatbot using LangGraph)
├── simple_nodes.ipynb         # Basic sequential graph workflow
├── graph_with_condition.ipynb # Graph with conditional branching
├── main.py                    # Main entry point (if applicable)
├── pyproject.toml             # Project dependencies
└── README.md                  # This file
```

## Technologies Used

- **LangGraph:** Framework for building stateful, multi-actor applications
- **Python:** 3.11+
- **Jupyter:** For interactive notebook exploration

## Chatbot Example

The `chatbot.ipynb` notebook showcases how LangGraph can orchestrate an LLM-based conversational agent.

- **Features:**
  - Uses OpenAI/other LLM nodes to process user messages
  - Maintains conversation state within a graph
  - Demonstrates advanced graph constructs and async interactions

> Refer to `chatbot.ipynb` for a step-by-step walkthrough of building the chatbot workflow.
