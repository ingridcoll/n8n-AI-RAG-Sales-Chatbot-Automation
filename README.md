# AI RAG Sales User-Facing Chatbot (n8n)
### A Self-Updating Retrieval-Augmented Generation System that Turns Sales Documents into an AI Chatbot
Technologies used: 
- *Google Drive* for centralized sales collateral storage
- *Google Gemini* for chunk contextualization and chat response generation
- *Supabase Vector Database* for semantic document retrieval
- *Cohere Reranker* to optimize relevance and reduce hallucinations
- *Postgres* for persistent chat memory
- *Calculator Tool* for deterministic numeric answers

This fully automated AI Sales RAG Agent transforms your company’s sales collateral into a conversational AI assistant that answers questions about your products, services, and offers, accurately, in real-time, and with full context from your documents. Ideal for any sales or customer-facing team that wants to provide instant, reliable answers based on internal knowledge, while maintaining conversation memory.

This automation was created by *Ingrid Coll*. See my other projects on GitHub at [github.com/ingridcoll](https://github.com/ingridcoll) or send me a LinkedIn message at [linkedin.com/in/ingridcoll](https://www.linkedin.com/in/ingridcoll/) with any questions or business inquiries!

## In PHASE 1: Pull All Files to Be Ingested...
### Detects changes in the central sales collateral folder and loops through each file for ingestion.
The main workflow is automatically triggered whenever a new file is added to the Google Drive folder or an existing file is updated.
All files in the folder are listed and passed into a loop that processes each file individually.
This ensures that the system continuously ingests the latest sales documents without missing updates or requiring manual intervention.
The loop structure optimizes memory usage by handling one file at a time, preparing it for downstream chunking, contextualization, and embedding.
<img width="1813" height="858" alt="image" src="https://github.com/user-attachments/assets/50698dc7-0682-459e-a33a-11b7f7eb81bf" />

## In PHASE 2: Process Each File, Contextualize, Add Metadata, and Store in Supabase Vector Database…
### Downloads each file, breaks it into chunks, generates contextual descriptions, enriches with metadata, and stores embeddings for semantic retrieval.
Each file from the loop is downloaded from Google Drive using its id.
Content is split into manageable chunks for efficient processing.
Google Gemini generates a 1-sentence contextual description for each chunk to improve retrieval relevance.
Each chunk is enriched with rich metadata, including:
`document_description` (AI-contextualized summary)
`document_title`
`number_of_pages`
`language`
`version`
The processed chunks and embeddings are stored in the Supabase vector database, making the content searchable and ready for use by the AI Sales Chatbot.
This phase ensures accurate, structured, and fully contextualized data is available for retrieval.
<img width="2476" height="703" alt="image" src="https://github.com/user-attachments/assets/8f2ba4c2-be33-48fd-b9f1-8a65ec80c51a" />
<img width="1276" height="742" alt="image" src="https://github.com/user-attachments/assets/f9178eb7-2540-426d-9036-2f069a1b4cf3" />

