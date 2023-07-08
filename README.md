# Yonder

## Conversational Query Across Multiple Sources 

Yonder allows you to process and query multiple documents conversationally.
You can upload a collection of PDFs and ask the application questions related to the content of the documents. 
Yonder will process and analyze the text content and respond to your questions based on the retrieved information.

## Dependencies
To install dependencies, use the following command:

```sh
pip install streamlit langchain PyPDF2 python-dotenv
```
## How it works
When you run the application, you can upload multiple PDF documents. The text content is extracted from these PDFs and broken down into smaller chunks. 

These chunks are then embedded into a vector store using OpenAI embeddings. A retrieval-based model, powered by langchain, is then used to interact with the user. When a question is asked, the model scans the vector store for relevant chunks and returns an answer based on the closest matches.

The user interface is designed with Streamlit, where you can input your questions and get the responses displayed.

## Usage
1. Clone the repository to your local machine.
2. Navigate to the project directory in your terminal.
3. Install the dependencies.
4. Run the app using `streamlit run your_script_name.py`.
5. Navigate to the local URL provided in your terminal to view the Streamlit application.
6. Upload your PDF files and hit the 'Process' button to start the information extraction.
7. Enter your queries in the text input field to get answers from the processed documents.

## Code Explanation

The script is organized into several functions, each with a specific role:

- `get_pdf_text(pdf_docs)`: This function accepts an array of PDF files and extracts the text from each page in the document.
- `get_text_chunks(text)`: This function splits the given text into chunks of 1000 characters each, overlapping by 100 characters.
- `get_vectorstore(text_chunks)`: This function converts the chunks of text into vectors using OpenAIEmbeddings and stores them using FAISS.
- `get_conversation_chain(vectorstore)`: This function sets up a ConversationalRetrievalChain with ChatOpenAI and the vectorstore.
- `handle_userinput(user_question)`: This function handles user input and updates the chat history.
- `main()`: This is the main function where the Streamlit application is set up and the other functions are called based on user interactions.

## Environment Variables
This script uses dotenv to manage environment variables. Make sure to have a `.env` file in your project directory containing any necessary variables.

## Note
Please ensure you have all the necessary permissions and dependencies installed before running the application. Make sure the necessary models and packages are available in your environment to avoid errors.
