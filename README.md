# RAG-Hyde-and-NVIDIA-NIM
Project: RAG USING Hyde and NVIDIA NIM(Nvidia Inference Models) 

Retrieval Augmentated Generation using NVIDIA NIM Microservices makes it very easy to deploy models .
NVIDIA NIM is a component of NVIDIA AI Enterprise, designed to facilitate the deployment of foundation models across any cloud or data center. It offers a set of easy-to-use inference microservices that accelerate the deployment of these models, ensuring data security. By leveraging NVIDIA NIM, developers can streamline the process of integrating AI models into their applications, benefiting from NVIDIA's expertise in AI and deep learning.

## Running the Script

To run this script, follow these steps:

1. **Set Up Your Environment**:
   - Ensure Python is installed.
   - Install the required packages using pip:
     ```
   !pip install langchain_nvidia_ai_endpoints
   !pip install langchain-community langchain-text-splitters
   !pip install faiss-cpu
     ```

2. **Prepare Your Google Colab Notebook**:
   - Open Google Colab and create a new notebook.
   - Copy and paste the provided script into the notebook cells.

3. **Configure NVIDIA API Key**:
   - Retrieve your NVIDIA API KEY from NVIDIA NIM Portal by registering yourself (It gives around 1000 free Credits in the start).
   - Set the API key as an environment variable in your Colab notebook:
     ```python
     from google.colab import userdata
     import os
     os.environ["NVIDIA_API_KEY"] = userdata.get('NVIDIA_API_KEY')
     ```

4. **Run the Script**:
   - Execute the script cell by cell, starting from the installation commands to the final function calls.
   - To test the system, invoke the `answer` function with a sample question:
     ```python
     for s in answer.stream("Explain How Mistral Works in Nvidia NIM"):
         print(s, end="")
     ```

## Key Concepts Explained

### Hyde

Hyde(Hypothetical Embeddings) is a method we used with the LangChain framework for generating hypothetical documents based on user queries. This process involves transforming a user's question into a brief level paragraph using a predefined template and the `ChatNVIDIA` model. The transformed query then serves as a basis for creating a hypothetical document, capturing the essence of the user's intent without requiring a perfect or full answer. This hypothetical document is embedded separately and used to retrieve real documents that are semantically similar, enhancing the retrieval process.

### NVIDIA NIM

NVIDIA NIM is a component of NVIDIA AI Enterprise, designed to facilitate the deployment of foundation models across any cloud or data center. It offers a set of easy-to-use inference microservices that accelerate the deployment of these models, ensuring data security. By leveraging NVIDIA NIM, developers can streamline the process of integrating AI models into their applications, benefiting from NVIDIA's expertise in AI and deep learning.

## Code Structure and Functionality

The script is organized around several key components, each playing a specific role in the overall workflow:

- **Document Loading and Preprocessing**: Loads documents from a specified URL and splits them into manageable chunks using `RecursiveCharacterTextSplitter`.
- **Embedding Generation**: Utilizes `NVIDIAEmbeddings` to generate embeddings for the split documents.
- **Vector Store Creation**: Initializes a FAISS vector store for efficient similarity search.
- **Retrieval Mechanism**: Sets up a retriever to find semantically similar documents based on query embeddings.
- **Model Initialization**: Initializes a `ChatNVIDIA` model for interacting with NVIDIA AI endpoints.
- **Hypothetical Document Generation**: Defines a mechanism for generating hypothetical documents based on user queries.
- **Answer Generation Chain**: Constructs a chain for generating detailed answers to user questions, incorporating the hypothetical document retrieval mechanism.


