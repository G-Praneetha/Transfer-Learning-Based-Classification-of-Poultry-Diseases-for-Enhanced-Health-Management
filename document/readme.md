project report in pdf 
file:///C:/Users/user/Downloads/ideation%20phase.pdf
file:///C:/Users/user/Downloads/Performance%20Testing.pdf




<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Poultry Disease Diagnosis Project</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      line-height: 1.6;
      background: #f7f9fa;
      color: #333;
    }
    header, footer {
      background-color: #34495e;
      color: #fff;
      text-align: center;
      padding: 20px;
    }
    nav {
      background-color: #2c3e50;
      padding: 10px;
      text-align: center;
    }
    nav a {
      color: white;
      margin: 0 15px;
      text-decoration: none;
    }
    nav a:hover {
      text-decoration: underline;
    }
    .container {
      padding: 40px;
      max-width: 1200px;
      margin: auto;
      background-color: #fff;
      box-shadow: 0 0 10px rgba(0,0,0,0.05);
    }
    section {
      margin-bottom: 50px;
    }
    h2 {
      color: #2c3e50;
      border-bottom: 2px solid #eee;
      padding-bottom: 5px;
    }
    ul {
      margin: 10px 0 0 20px;
    }
  </style>
</head>
<body>
  <header>
    <h1>AI-Powered Poultry Disease Classification</h1>
    <p>Transfer Learning-Based Enhanced Health Management</p>
  </header>

  <nav>
    <a href="#overview">Overview</a>
    <a href="#scenarios">Scenarios</a>
    <a href="#prerequisites">Setup</a>
    <a href="#objectives">Objectives</a>
    <a href="#flow">Flow</a>
  </nav>

  <div class="container">
    <section id="overview">
      <h2>Project Overview</h2>
      <p>This project develops a Transfer Learning-based system to classify poultry diseases: Salmonella, New Castle Disease, Coccidiosis, and Healthy. It integrates a model with a mobile/web app enabling farmers to receive real-time diagnosis and treatment suggestions by uploading symptoms and images.</p>
    </section>

    <section id="scenarios">
      <h2>Use Case Scenarios</h2>
      <h3>1. Outbreak in a Rural Community</h3>
      <p>Farmers detect signs of disease in birds. Using the app, they upload symptoms and get a Coccidiosis diagnosis with treatment suggestions—allowing early action and reduced loss.</p>
      <h3>2. Commercial Poultry Farm</h3>
      <p>Farm managers use the app daily. It flags potential New Castle Disease early, triggering immediate isolation protocols and preserving flock health and revenue.</p>
      <h3>3. Veterinary Student Training</h3>
      <p>Students input real-life cases into the app and learn AI-driven diagnostic workflows, enhancing their readiness for fieldwork.</p>
    </section>

    <section id="prerequisites">
      <h2>Setup & Prerequisites</h2>
      <h3>Software</h3>
      <ul>
        <li>Anaconda Navigator</li>
        <li>Python Libraries: numpy, pandas, scikit-learn, matplotlib, seaborn, scipy, tensorflow</li>
        <li>Flask (for backend)</li>
      </ul>
      <h3>Prior Knowledge</h3>
      <ul>
        <li>Neural Networks and CNNs</li>
        <li>Transfer Learning (VGG16, VGG19, ResNet50)</li>
        <li>Data Preprocessing & Augmentation</li>
        <li>Overfitting & Regularization Techniques</li>
        <li>Basic Flask Web Framework</li>
      </ul>
    </section>

    <section id="objectives">
      <h2>Project Objectives</h2>
      <ul>
        <li>Understand deep learning and model evaluation</li>
        <li>Train transfer learning models on poultry disease images</li>
        <li>Deploy a predictive model in a Flask web app</li>
        <li>Assist farmers and students with diagnostic support</li>
      </ul>
    </section>

    <section id="flow">
      <h2>Project Workflow</h2>
      <ul>
        <li>Data Collection (Kaggle API + Google Colab)</li>
        <li>Data Preprocessing & Sampling (500 images/class)</li>
        <li>Model Training using VGG16/VGG19/ResNet50</li>
        <li>Evaluation using loss/accuracy and confusion matrix</li>
        <li>Save model as .h5 for inference</li>
        <li>Build Flask App (index.html + Python backend)</li>
        <li>Deploy: Upload image → Predict → Show Result</li>
      </ul>
    </section>
  </div>

  <footer>
    <p>&copy; 2025 Poultry Disease AI Project. All rights reserved.</p>
  </footer>
</body>
</html>
