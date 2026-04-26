<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Image App</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f9;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    .image-container {
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      text-align: center;
      width: 400px;
    }
    img {
      max-width: 100%;
      border-radius: 10px;
      margin-top: 15px;
      transition: 0.3s;
    }
    input[type="file"] {
      margin: 10px 0;
    }
    button {
      margin: 5px;
      padding: 10px 15px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      background: #2196F3;
      color: white;
    }
    button:hover {
      background: #1976D2;
    }
  </style>
</head>
<body>
  <div class="image-container">
    <h2>Image App</h2>
    <input type="file" id="fileInput" accept="image/*">
    <div>
      <button onclick="applyFilter('grayscale(100%)')">Grayscale</button>
      <button onclick="applyFilter('brightness(150%)')">Brighten</button>
      <button onclick="applyFilter('contrast(200%)')">Contrast</button>
      <button onclick="resetFilter()">Reset</button>
    </div>
    <img id="preview" src="" alt="Preview will appear here">
  </div>

  <script>
    const fileInput = document.getElementById("fileInput");
    const preview = document.getElementById("preview");

    fileInput.addEventListener("change", () => {
      const file = fileInput.files[0];
      if (file) {
        const reader = new FileReader();
        reader.onload = e => {
          preview.src = e.target.result;
        };
        reader.readAsDataURL(file);
      }
    });

    function applyFilter(filter) {
      preview.style.filter = filter;
    }

    function resetFilter() {
      preview.style.filter = "none";
    }
  </script>
</body>
</html>
