# CivicAI: Search Whitehorse City Council Meetings with LLM-Powered Precision

**CivicAI** is an AI-powered semantic search interface for exploring official documents; agendas, minutes, and reports, published by the City Council of Whitehorse, Yukon. Built using **Google Vertex AI Search**, this project transforms a static archive of PDFs into a conversational search experience grounded in city policy, planning, and decisions.

## Why This Project Matters

Traditional government archives are not search-friendly. Meeting minutes and agenda packages contain valuable insights on housing, infrastructure, zoning, and budget allocations, yet they’re buried in dated PDFs. **CivicAI democratizes access to civic records**—making it easy for residents, researchers, and journalists to ask questions and get answers with citations from the original documents.

---

## Documents Covered

We collected and cleaned **688 documents** from the official Whitehorse City Council archive:

> https://www.whitehorse.ca/city-council/meetings/agendas-minutes-and-reports/

These include:
- Regular & Special Council Meeting Agendas
- Meeting Minutes
- Response-to-Council Questions
- Strategic Plans and Staff Reports

---

## System Architecture

| Layer                  | Technology Used                     |
|------------------------|-------------------------------------|
| Embedding & Chunking   | Document AI + Vertex AI pipelines   |
| Vector Indexing        | Vertex AI Matching Engine           |
| Semantic Search        | Vertex AI Search (Generative RAG)   |
| Frontend Integration   | Custom HTML + Google Search Widget  |
| Hosting                | GitHub Pages                        |

---

## Development Journey

1. **Data Collection**  
   Scraped and renamed 688 Whitehorse PDF documents using a consistent `YYYY-MM-DD-subject_category.pdf` format.

2. **Upload to GCS**  
   Stored files in a Google Cloud Storage bucket designed for ingestion by Vertex AI Search.

3. **Vertex AI Search Setup**  
   - Created a Datastore (`civic-ai-datastore`)
   - Created an App (`civic-ai`) linked to that datastore
   - Imported all documents into the Vertex AI pipeline
   - Applied custom parsing logic and metadata enhancement

4. **Widget Integration**  
   - Used the Vertex AI-provided `<gen-search-widget>` with a custom input trigger
   - Deployed a minimalist public interface via GitHub Pages

---

## Live Demo

Visit the live search portal: [[https://pidoko.github.io/civic-ai/](https://pidoko.github.io/civic-ai-search/)]


Ask questions like:
- _“What zoning changes were discussed in January 2024?”_
- _“What initiatives have been proposed to address crime?”_
- _“Was affordable housing discussed in 2024?”_

---

## Tech Stack

- **Vertex AI Search**: Grounded answer generation with citations
- **Document AI**: PDF preprocessing and intelligent extraction
- **Google Cloud Storage**: Document hosting
- **GitHub Pages**: Static frontend hosting
- **HTML/JS**: Custom UI with embedded widget

---

## Future Plans

- Add query follow-ups and deep linking to documents
- Add Google Sign-In or Entra ID to support internal city use
- Track usage analytics and feedback for iterative tuning
- Explore integration with the City of Whitehorse official site

---

## Credits

Built by **Peter Chibuikem Idoko**, a computer scientist in training at Northeastern University exploring semantic interfaces for public accountability.

Northeastern University MSCS (Align)  
Based in Vancouver / Whitehorse / Calgary  
Website: [pidoko.com](https://pidoko.com)

---

## License

This project is shared under the MIT License for public interest, learning, and civic innovation.

