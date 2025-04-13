---
layout: default
---

<!-- Vertex AI Search JavaScript -->
<script src="https://cloud.google.com/ai/gen-app-builder/client?hl=en_US"></script>

<h1 style="text-align: center;">Ask Questions Based on City Council Agendas, Minutes, and Reports</h1>

<p style="text-align: center; max-width: 600px; margin: auto;">
  Get clear, reliable answers grounded in official Whitehorse City Council meeting documents.<br />
  All responses are sourced from published agendas, minutes, and supporting reports available at:<br />
  <a href="https://whitehorse.ca/city-council/meetings/agendas-minutes-and-reports/" target="_blank">
    whitehorse.ca/city-council/meetings/agendas-minutes-and-reports/
  </a>
</p>

<!-- Search Input and Button -->
<div style="text-align: center; margin-top: 40px;">
  <input
    type="text"
    id="searchBox"
    placeholder="Search here..."
    style="width: 300px; padding: 10px; font-size: 1rem;" />
  <button
    id="searchButton"
    style="padding: 10px 20px; font-size: 1rem; cursor: pointer;">
    Ask a Question
  </button>
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
