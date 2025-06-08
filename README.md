# 🧮 Multi-Tool Math & Reasoning Agent

This project showcases a sophisticated chatbot, built with **Streamlit** and **LangChain**, that functions as a powerful math and reasoning assistant. It uses a LangChain **Agent** powered by the **Groq API** (`gemma2-9b-it` model) to intelligently select from a suite of tools—including a calculator, a Wikipedia search tool, and a reasoning engine—to answer a wide variety of user questions.

---
## ✨ Features

* **Multi-Tool Agent**: Utilizes a LangChain Agent (`ZERO_SHOT_REACT_DESCRIPTION`) that can dynamically choose the best tool for a given task.
* **Mathematical Problem Solving**: Integrates an `LLMMathChain` as a "Calculator" tool, enabling the agent to solve complex mathematical problems expressed in natural language.
* **Wikipedia Integration**: Includes a Wikipedia search tool, allowing the agent to look up information on a vast range of topics to answer general knowledge questions.
* **Logical Reasoning**: Features a dedicated "Reasoning" tool with a custom prompt, designed to handle logic-based questions.
* **High-Speed LLM**: Powered by the `gemma2-9b-it` model via the Groq API for fast and efficient inference.
* **Interactive Chat Interface**: A user-friendly, stateful chat application built with Streamlit that displays the conversation history.
* **Transparent Thought Process**: Implements `StreamlitCallbackHandler` to stream the agent's internal monologue and tool usage directly into the UI, showing how it arrives at an answer.

---
## ⚙️ How it Works

The application's intelligence comes from its agent-based architecture:

1.  **User Input**: The user enters a question into the Streamlit chat interface. This can be a math problem ("What is 34% of 512?"), a request for information ("Who is the founder of OpenAI?"), or a reasoning puzzle.
2.  **Agent Invocation**: The user's question, along with the entire conversation history, is passed to the LangChain `assistant_agent`.
3.  **Tool Selection**: The `ZERO_SHOT_REACT_DESCRIPTION` agent analyzes the input and, based on the descriptions of the available tools, decides which one is most suitable to use.
    * For "What is (5.6 * 12) + 3?", it will choose the **Calculator** tool.
    * For "Who is Marie Curie?", it will choose the **Wikipedia** tool.
    * For logic puzzles, it may select the **Reasoning** tool.
4.  **Tool Execution**: The agent executes the chosen tool with the relevant part of the user's query as input. For example, it passes `(5.6 * 12) + 3` to the `LLMMathChain`.
5.  **Observation and Response**: The agent observes the output from the tool and uses this new information to formulate a final, human-readable answer.
6.  **Streaming to UI**: Throughout this process, the `StreamlitCallbackHandler` captures the agent's "thoughts" and actions, displaying them in real-time in an expander within the chat window, providing transparency into its problem-solving process.

---
## 📋 Requirements

* Python 3.x
* A **Groq API Key**.
* Required Python libraries: `streamlit`, `langchain`, `langchain_groq`, `langchain_community`, `wikipedia`, `numexpr`.

---
## 🛠️ Setup & Installation

1.  **Clone the repository or download the `app.py` script.**

2.  **Create a virtual environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3.  **Install the required Python libraries:**
    ```bash
    pip install streamlit langchain langchain_groq langchain_community wikipedia numexpr
    ```

4.  **Set up Groq API Key**:
    * You will need to get an API Key from your [Groq account](https://console.groq.com/keys).
    * The application allows you to enter this key directly into the sidebar interface, so you don't need to set up a `.env` file.

---
## ▶️ Usage

1.  **Run the Streamlit App**:
    * Open your terminal in the project's root directory.
    * Execute the `app.py` script:
        ```bash
        streamlit run app.py
        ```
    * Your web browser will open with the application's UI.

2.  **Enter Your API Key**:
    * In the sidebar on the left, paste your **Groq API Key** into the designated field. The application will not proceed without it.

3.  **Ask Questions**:
    * Type your question into the text area at the bottom of the chat window.
    * Click the **"find my answer"** button.
    * Watch as the chatbot processes your request. You can expand the "thoughts" container to see which tool the agent decided to use and what its reasoning process was.

---