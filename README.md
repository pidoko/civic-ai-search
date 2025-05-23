# CivicUnlock: Search Whitehorse City Council Meetings with LLM-Powered Precision
[[civicunlock.com](https://civicunlock.com)]

**CivicUnlock** is an AI-powered semantic search interface for exploring official documents; agendas, minutes, and reports, published by the City Council of Whitehorse, Yukon. Built using **Google Vertex AI Search**, this project transforms a static archive of PDFs into a conversational search experience grounded in city policy, planning, and decisions.

## Why This Project Matters

Traditional government archives are not search-friendly. Meeting minutes and agenda packages contain valuable insights on housing, infrastructure, zoning, and budget allocations, yet they’re buried in dated PDFs. **CivicUnlock democratizes access to civic records** making it easy for residents, researchers, and journalists to ask questions and get answers with citations from the original documents.

---

## Documents Covered

I collected and cleaned **690 documents** from the official Whitehorse City Council archive:

> [https://www.whitehorse.ca/city-council/meetings/agendas-minutes-and-reports/](https://www.whitehorse.ca/our-government/city-council/meetings/agendas-minutes-and-reports/#1651084772994-e30573fb-d311)

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
| Hosting                | GoDaddy                             |

---

## Development Journey

1. **Data Collection**  
   Scraped and renamed 688 Whitehorse PDF documents using a consistent `YYYY-MM-DD-subject_category.pdf` format.

2. **Upload to GCS**  
   All 688 cleaned PDF documents were uploaded to a Google Cloud Storage (GCS) bucket strategically provisioned in the us-west1 region (Oregon). This region was selected deliberately for the following reasons:
    Climate-Conscious Cloud Hosting: us-west1 is one of Google Cloud's low-carbon regions, powered by renewable energy sources. Hosting the dataset in this region aligns with the project’s civic mission to support sustainability and responsible computing.

    Low Latency with Vertex AI: Vertex AI’s vector search, document AI, and LLM services are all available in us-west1, ensuring fast, in-region processing for indexing, querying, and embedding.

    Open Data Principles: GCS enables public-read access for controlled transparency, aligning with the goal of making civic data accessible without compromising security or control.

   The uploaded files were named and structured using a consistent, machine-readable format (regular_council_agenda_YYYY-MM-DD.pdf, etc.), making the ingestion process seamless for Vertex AI Search. This ensured high-quality indexing and enabled accurate grounding of user queries in the source material.

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
- _“Were there any proposed rezoning applications for downtown Whitehorse in 2023?”_
- _“What updates were made to the Official Community Plan in the past year?”_
- _“What are the key highlights from the 2025–2028 Capital Expenditure Program?”_
- _“How much funding was allocated to housing development in 2024?”_
- _“What actions has the City Council taken to address affordable housing since 2023?”_
- _“Were there any discussions about new housing developments in the Whistle Bend area?”_
- _“Has the City received any public feedback on housing affordability in recent meetings?”_
- _"What infrastructure projects were approved to improve sustainability or climate resilience?"_
- _"What major land use changes were approved in the 2024 planning cycle?"_
- _“Did Council discuss any transportation upgrades or roadworks for 2024?”_

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

