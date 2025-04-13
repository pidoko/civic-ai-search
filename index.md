---
layout: default
---

<!-- Vertex AI Search JavaScript -->
<script src="https://cloud.google.com/ai/gen-app-builder/client?hl=en_US"></script>

<style>
  body {
    font-family: "Segoe UI", "Helvetica Neue", sans-serif;
    background: #f9f9f9;
    color: #111;
    margin: 0;
    padding: 0;
  }

  .container {
    max-width: 700px;
    margin: 4rem auto;
    padding: 2rem;
    background: #ffffff;
    border-radius: 12px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.08);
    text-align: center;
  }

  h1 {
    font-size: 1.9rem;
    margin-bottom: 1rem;
    color: #222;
  }

  p {
    font-size: 1rem;
    color: #555;
    line-height: 1.5;
  }

  a {
    color: #0078d4;
    text-decoration: none;
  }

  .search-box {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 0.5rem;
    margin-top: 2rem;
    flex-wrap: wrap;
  }

  .search-box input {
    padding: 0.75rem 1rem;
    font-size: 1rem;
    width: 280px;
    border: 1px solid #ccc;
    border-radius: 8px;
  }

  .search-box button {
    padding: 0.75rem 1.2rem;
    font-size: 1rem;
    background-color: #0057b8;
    color: white;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  .search-box button:hover {
    background-color: #003f8f;
  }
</style>

<div class="container">
  <h1>Ask Questions Based on City Council Agendas, Minutes, and Reports</h1>
  <p>
    Get clear, reliable answers grounded in official Whitehorse City Council meeting documents.<br />
    All responses are sourced from published agendas, minutes, and supporting reports available at:<br />
    <a href="https://whitehorse.ca/city-council/meetings/agendas-minutes-and-reports/" target="_blank">
      whitehorse.ca/city-council/meetings/agendas-minutes-and-reports/
    </a>
  </p>

  <div class="search-box">
    <input
      type="text"
      id="searchBox"
      placeholder="E.g., What zoning changes were proposed in January 2024?" />
    <button id="searchButton">Ask a Question</button>
  </div>
</div>

<!-- Vertex AI Search Widget -->
<gen-search-widget configId="c6d6616c-c71f-4f1b-b5af-9344fcd18aa9" id="searchWidget"></gen-search-widget>

<script>
  const button = document.getElementById('searchButton');
  const input = document.getElementById('searchBox');
  const widget = document.getElementById('searchWidget');

  button.addEventListener('click', () => {
    const query = input.value.trim();
    if (query.length === 0) return;
    widget.open({ query });
  });
</script>
