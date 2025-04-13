<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Ask Whitehorse Council</title>
  <script src="https://cloud.google.com/ai/gen-app-builder/client?hl=en_US"></script>
  <style>
    body {
      margin: 0;
      font-family: "Segoe UI", "Helvetica Neue", sans-serif;
      background: #f9f9f9;
      color: #111;
    }

    .hero {
      padding: 2rem 1rem;
      background: linear-gradient(to right, #0866c6, #11a672);
      color: white;
      text-align: center;
    }

    .hero h1 {
      font-size: 2rem;
      margin: 0.5rem 0;
    }

    .hero p {
      font-size: 1rem;
      margin-bottom: 0.5rem;
    }

    .container {
      max-width: 700px;
      margin: 1rem auto;
      padding: 1rem;
      text-align: center;
    }

    .container p {
      font-size: 0.95rem;
      color: #333;
      margin: 0.5rem 0 1.5rem;
    }

    .search-box {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;
      gap: 0.5rem;
      margin-top: 1rem;
    }

    .search-box input {
      padding: 0.75rem 1rem;
      font-size: 1rem;
      width: 300px;
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
    }

    .search-box button:hover {
      background-color: #004799;
    }

    a {
      color: #0057b8;
    }
  </style>
</head>
<body>

  <div class="hero">
    <h1>Ask Whitehorse Council</h1>
    <p>Get sourced answers from city council documents</p>
  </div>

  <div class="container">
    <p>
      Ask questions based on City Council agendas, minutes, and reports.<br />
      Sourced from: 
      <a href="https://whitehorse.ca/city-council/meetings/agendas-minutes-and-reports/" target="_blank">
        whitehorse.ca/city-council/meetings/agendas-minutes-and-reports
      </a>
    </p>

    <div class="search-box">
      <input
        type="text"
        id="searchBox"
        placeholder="E.g. What zoning changes were proposed in 2024?" />
      <button id="searchButton">Ask a Question</button>
    </div>
  </div>

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
</body>
</html>
