project report in pdf 
file:///C:/Users/user/Downloads/ideation%20phase.pdf
file:///C:/Users/user/Downloads/Performance%20Testing.pdf



<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Poultry Disease Detection</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f5f5f5;
      margin: 0;
      padding: 0;
    }
    header {
      background-color: #2c3e50;
      color: white;
      padding: 20px;
      text-align: center;
    }
    .container {
      max-width: 600px;
      margin: 50px auto;
      background: white;
      padding: 30px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
      border-radius: 8px;
    }
    h2 {
      text-align: center;
      color: #333;
    }
    form {
      display: flex;
      flex-direction: column;
      gap: 15px;
    }
    input[type="file"] {
      padding: 10px;
    }
    input[type="submit"] {
      background-color: #27ae60;
      color: white;
      border: none;
      padding: 10px;
      cursor: pointer;
      font-size: 16px;
    }
    input[type="submit"]:hover {
      background-color: #219150;
    }
    .result {
      margin-top: 20px;
      text-align: center;
      font-size: 18px;
      color: #2980b9;
    }
  </style>
</head>
<body>
  <header>
    <h1>Poultry Disease Detection</h1>
    <p>Upload an image to diagnose the disease</p>
  </header>

  <div class="container">
    <h2>Upload Image</h2>
    <form action="/predict" method="POST" enctype="multipart/form-data">
      <input type="file" name="image" accept="image/*" required />
      <input type="submit" value="Detect Disease" />
    </form>

    <div class="result">
      <!-- This is where the result will be shown -->
      <!-- Example: <p>Disease Predicted: Coccidiosis</p> -->
    </div>
  </div>
</body>
</html>
