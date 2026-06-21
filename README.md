## README Structure for AgenticRAG-DTA

```markdown
# AgenticRAG-DTA: Agentic RAG with LangGraph for Discovery-to-Action

A cutting-edge AI assistant combining Retrieval-Augmented Generation (RAG) with LangGraph's agentic capabilities for intelligent discovery-to-action workflows.

## ✨ Features

*   **Intelligent Agentic Workflow:** Leverages LangGraph to orchestrate complex interactions between an LLM and external tools.
*   **Retrieval-Augmented Generation (RAG):** Integrates a knowledge base search tool for grounding LLM responses in provided documents.
*   **Dynamic Tool Use:** Agent intelligently decides whether to use a knowledge base search tool or respond directly.
*   **Local Vector Store:** Uses ChromaDB for efficient storage and retrieval of document embeddings.
*   **Flexible LLM Integration:** Designed to be adaptable to various LLMs (currently configured for Google Generative AI `gemini-2.5-flash`).
*   **PDF Document Processing:** Loads, chunks, and embeds content from PDF documents.

## 🛠️ How it Works

This project implements a Discovery-to-Action (DTA) framework using LangGraph. The core components are:

1.  **Document Ingestion:** A sample PDF document is loaded, split into manageable chunks, and converted into embeddings.
2.  **Vector Database (ChromaDB):** These embeddings are stored in a persistent ChromaDB instance, serving as the knowledge base.
3.  **Knowledge Base Search Tool:** A custom LangChain tool is defined to query the ChromaDB for relevant information.
4.  **Agentic Workflow (LangGraph):**
    *   An `AgentState` manages the conversation history and input/output.
    *   An `agent_node` uses an LLM (e.g., `gemini-2.5-flash`) to decide the next action: either respond directly or call a tool.
    *   A `tool_node` executes the `knowledge_base_search` tool if requested by the agent.
    *   A `conditional_edge` dynamically routes the workflow based on the agent's decision.
    *   The entire workflow is compiled into a runnable agent.

## 🚀 Setup & Installation

Follow these steps to get the project running locally:

### Prerequisites

*   Python 3.9+
*   Google API Key (for Gemini models) added to Colab secrets as `GOOGLE_API_KEY`.

### Clone the Repository

```bash
git clone https://github.com/your-username/AgenticRAG-DTA.git
cd AgenticRAG-DTA
```

### Install Dependencies

```bash
pip install -U langchain langchain-community langchain-chroma langgraph pypdf unstructured tiktoken python-dotenv sentence-transformers langchain-huggingface langchain-google-genai
```

### Run the Notebook

Open the `agentic_rag_dta.ipynb` notebook in Google Colab or your preferred Jupyter environment and execute the cells sequentially. Ensure your `GOOGLE_API_KEY` is configured in Colab secrets.

## 💡 Usage

Once the notebook cells are executed, the agent will be ready to answer questions. You can test it with:

*   **Document-specific questions:** E.g., "What are the three main risks of bias mentioned in the document?"
*   **General knowledge questions:** E.g., "What is 2+2?"

The agent will dynamically decide whether to use its `knowledge_base_search` tool based on the query.

## 📂 Project Structure

*   `agentic_rag_dta.ipynb`: The main Jupyter notebook containing all the code and explanations.
*   `ai_ethics.pdf`: Sample PDF document used for the knowledge base.
*   `chroma_db/`: Persistent directory for the ChromaDB vector store.

## 🛣️ Future Enhancements

*   Integrate more sophisticated decision-making for tool use.
*   Add support for multiple tools and more complex tool orchestration.
*   Implement a user interface for easier interaction.
*   Expand document loaders to support various file formats.
*   Fine-tune LLM for specific RAG tasks.

## 🤝 Contributing

Contributions are welcome! Please feel free to open issues or submit pull requests.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
```
