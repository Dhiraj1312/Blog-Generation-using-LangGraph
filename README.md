Blog Generator using Agentic AI
This project is an end-to-end application that generates blog posts using an AI agent built with langgraph. It can create blog titles, generate content, and even translate the content into different languages (currently Hindi and French).

Features
Blog Title Creation: Generates creative and SEO-friendly titles based on a given topic.
Blog Content Generation: Produces detailed blog content for the specified topic.
Multi-language Translation: Supports translation of blog content into different languages like Hindi and French.
API Endpoint: Exposes a FastAPI endpoint for easy integration and usage.
Technologies Used
Python 3.13
FastAPI: For creating the web API.
LangChain: Core framework for building LLM applications.
LangGraph: For orchestrating the multi-step AI agent workflows.
Langchain-Groq: Integration with Groq's LLM inference for fast responses (using llama-3.1-8b-instant).
Uvicorn: An ASGI server to run the FastAPI application.
python-dotenv: To manage environment variables.
Project Structure
app.py: The main FastAPI application that exposes the /blogs API endpoint for generating blog posts.
src/: Contains the core logic for the AI agent.
src/graphs/graph_builder.py: Defines the langgraph workflows (graphs) for blog generation, including conditional routing for translation.
src/llms/groqllm.py: Handles the initialization and configuration of the Groq LLM.
src/nodes/blog_node.py: Contains the individual steps (nodes) of the blog generation process, such as title_creation, content_generation, and translation.
src/states/blogstate.py: Defines the data structure (state) that flows through the langgraph workflow.
.env: Stores your API keys (e.g., GROQ_API_KEY).
pyproject.toml / requirements.txt: Lists all project dependencies.
uv.lock: Lock file for uv package manager, ensuring consistent dependency installations.
Setup and Installation
Clone the repository (if applicable):

# If this project is part of a larger repository, clone it.
# git clone <repository_url>
# cd end-to-end-blog-generator-agenticai-app
Set up Python Environment: Ensure you have Python 3.13 installed. You can use uv for dependency management, which is often faster than conda or standard venv.

# Install uv if you don't have it
# pip install uv

# Create a new virtual environment
uv venv

# Activate the virtual environment
# On macOS/Linux:
source .venv/bin/activate
# On Windows:
# .venv\Scripts\activate
Install Dependencies:

uv pip install -r requirements.txt
Configure Environment Variables: Create a .env file in the root directory of the project (e.g., brahme27/end-to-end-blog-generator-agenticai-app/END-TO-END-BLOG-GENERATOR-AgenticAI-APP-3c34fa8d13afad9a39a0ae98ab296be5f15fa8f9/) and add your Groq API Key:

LANGCHAIN_PROJECT=
LANGCHAIN_API_KEY=
GROQ_API_KEY="YOUR_GROQ_API_KEY"
Replace "YOUR_GROQ_API_KEY" with your actual Groq API key.

How to Run
Start the FastAPI Application: Navigate to the root directory of the project (where app.py is located) and run:

uvicorn app:app --host 0.0.0.0 --port 8000 --reload
This will start the API server, usually accessible at http://localhost:8000.

Usage
You can interact with the API using tools like curl, Postman, or any HTTP client.

The API endpoint is POST /blogs.

Example Request (Generate Blog by Topic)
To generate a blog post on a specific topic:

{
    "topic": "Agentic AI"
}
Example Request (Generate Blog by Topic and Language)
To generate a blog post and translate it to a specific language:

{
    "topic": "Agentic AI",
    "language": "french"
}
You can send these JSON payloads to http://localhost:8000/blogs. The API will return the generated blog title and content.
