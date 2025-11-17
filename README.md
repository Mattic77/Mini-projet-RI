# Information Retrieval System – Inverted Index & TF-IDF Search

This project implements a lightweight **Information Retrieval (IR)** pipeline using Node.js, Express, and MongoDB. It was originally created as an academic / research project to explore concepts like document preprocessing, inverted index construction, TF-IDF computation, query ranking, and search with cosine-based scoring.

The system loads raw text documents, preprocesses them, builds an inverted index, and provides a search endpoint that returns relevant documents ranked by similarity score.

## 📁 Project Structure
/routes  
    documents.js – Save documents, build inverted index, search  
/models  
    Document.js – Mongoose schema for processed docs  
    FichierInverse.js – Schema for inverted index entries  
/utils  
    saveDocumentsFromFolder.js  
    query.js – TF-IDF search + scoring  
    creationfichierinverse.js  
/Collection_TIME – Folder containing raw text files

## 🔍 Features

### 1. Document Loader
- Reads `.txt` files from `/Collection_TIME`
- Preprocesses text
- Computes term frequencies
- Saves documents into MongoDB

### 2. Inverted Index Builder
- Creates TF-IDF-ready inverted index
- Stores posting lists and document term frequencies

### 3. TF-IDF Search Engine
- Tokenizes user query
- Computes TF-IDF score
- Ranks documents by similarity
- Returns most relevant content

## 📡 API Endpoints

### POST /save
Loads and stores all documents.

### POST /build-inverted-index
Creates the TF-IDF inverted index.

### POST /search
Request:
{
  "request": "your keywords"
}

Response:
{
  "results": [
    { "fileName": "...", "content": "...", "score": 0.87 }
  ]
}

## 🗄️ Data Models

### Document Model
- fileName  
- content  
- indexdoc.index  
- indexdoc.frequency  

### Inverted Index Model
- terme  
- nb_doc  
- posting[fileName, frequency]

## ⚙️ Technologies
- Node.js / Express  
- MongoDB / Mongoose  
- TF-IDF scoring  
- Basic IR engine design

## 🚀 How to Run
npm install  
npm start  

Workflow:
1. Add documents to `/Collection_TIME`
2. POST /save
3. POST /build-inverted-index
4. POST /search

## 📌 Future Improvements
- Add stemming & stop words  
- Improve cosine similarity  
- Add pagination & highlighting  
- Add frontend viewer
