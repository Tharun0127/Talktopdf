# Talktopdf

Chat with Your PDF Application
This application allows users to upload PDF files and ask questions based on their content. It uses Streamlit for the interface, LangChain for text processing and question answering, and Google Generative AI for generating embeddings and responses. The processed data is stored in a FAISS vector store for efficient similarity searches.

How It Works
Upload PDFs: Users can upload one or multiple PDF files.
Process PDFs: The application extracts text from the PDFs, splits it into smaller chunks, and stores it in a FAISS vector store using embeddings.
Ask Questions: Users type questions related to the uploaded PDFs, and the application retrieves the most relevant information and answers the question.

Code Structure
1. app.py
The main application file includes:
Libraries:
streamlit for the interface.
PyPDF2 for extracting text from PDFs.
langchain for splitting text, embeddings, and managing question-answering chains.
google.generativeai for AI embeddings and chat responses.
FAISS for vector storage and similarity search.
dotenv for loading environment variables.
Functions:
get_pdf_text(pdf_docs): Extracts text from uploaded PDFs.
get_text_chunks(text): Splits the text into smaller chunks (10,000 characters max).
get_vector_store(text_chunks): Stores the text chunks as embeddings in FAISS for future retrieval.
get_conversational_chain(): Creates a QA chain with a specific prompt for detailed and accurate responses.
user_input(user_question): Handles user questions by searching the vector store and retrieving the answer.
main(): The main application logic, handling file uploads, text processing, and user interactions.

2. requirements.txt
Specifies the dependencies required for the application. Examples:
streamlit
PyPDF2
langchain
google-generativeai
faiss
python-dotenv

3. .env
Contains sensitive environment variables such as the Google API Key:
makefile
Copy code
GOOGLE_API_KEY="YOUR_API_KEY_HERE"

Replace YOUR_API_KEY_HERE with your valid Google API key.

Setup and Usage
1. Install Dependencies
Run the following command to install the necessary libraries:
bash
Copy code
pip install -r requirements.txt

2. Set Up Environment Variables
Create a .env file in the project folder and add your Google API key:
bash
Copy code
GOOGLE_API_KEY="your_google_api_key"

3. Run the Application
Execute the Streamlit app:
bash
Copy code
streamlit run app.py

4. Upload PDFs and Ask Questions
Use the sidebar to upload PDF files.
Click Submit & Process to extract and process the content.
Type a question in the input box and view the response.

Features
Multi-PDF Support: Upload multiple PDFs at once.
Efficient Processing: Text is split into manageable chunks for optimal processing.
Smart Search: Uses FAISS for similarity-based retrieval.
Detailed Answers: Answers questions based on available context or informs if an answer is unavailable.

