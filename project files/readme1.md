1. Flask app structure
bash
Copy
Edit
/project_folder
│
├── app.py              # Flask backend app
├── model.h5            # Your trained model file (placeholder name)
├── requirements.txt    # For Python dependencies
├── static/
│   └── css/
│       └── style.css   # CSS styles (optional)
├── templates/
│   ├── index.html      # Home page
│   ├── prerequisites.html
│   ├── predict.html
│   └── result.html
└── uploads/            # Folder to temporarily store uploaded images
2. app.py (Flask backend)
python
Copy
Edit
from flask import Flask, render_template, request, redirect, url_for
import os
from werkzeug.utils import secure_filename
from tensorflow.keras.models import load_model
from tensorflow.keras.preprocessing import image
import numpy as np

app = Flask(_name_)
app.config['UPLOAD_FOLDER'] = 'uploads'
app.config['ALLOWED_EXTENSIONS'] = {'png', 'jpg', 'jpeg'}

# Load your trained model (replace with your actual model filename)
model = load_model('model.h5')

# Disease categories - update according to your model classes
DISEASE_CLASSES = ['Salmonella', 'New Castle Disease', 'Coccidiosis', 'Healthy']

def allowed_file(filename):
    return '.' in filename and \
           filename.rsplit('.', 1)[1].lower() in app.config['ALLOWED_EXTENSIONS']

def preprocess_image(img_path):
    img = image.load_img(img_path, target_size=(224, 224))  # Assuming model expects 224x224 images
    img_array = image.img_to_array(img)
    img_array = np.expand_dims(img_array, axis=0)
    img_array /= 255.0  # Normalize pixel values
    return img_array

@app.route('/')
def home():
    return render_template('index.html')

@app.route('/prerequisites')
def prerequisites():
    return render_template('prerequisites.html')

@app.route('/predict', methods=['GET', 'POST'])
def predict():
    if request.method == 'POST':
        # Check if file part is present
        if 'file' not in request.files:
            return render_template('predict.html', error="No file part")
        file = request.files['file']
        if file.filename == '':
            return render_template('predict.html', error="No selected file")
        if file and allowed_file(file.filename):
            filename = secure_filename(file.filename)
            filepath = os.path.join(app.config['UPLOAD_FOLDER'], filename)
            file.save(filepath)
            
            # Preprocess and predict
            img = preprocess_image(filepath)
            prediction = model.predict(img)
            class_idx = np.argmax(prediction)
            disease = DISEASE_CLASSES[class_idx]
            
            # Remove uploaded image after prediction
            os.remove(filepath)
            
            return render_template('result.html', disease=disease)
        else:
            return render_template('predict.html', error="File type not allowed. Upload png, jpg, jpeg.")
    return render_template('predict.html')

if _name_ == '_main_':
    os.makedirs(app.config['UPLOAD_FOLDER'], exist_ok=True)
    app.run(debug=True)
3. HTML templates
templates/index.html (Home page)
html
Copy
Edit
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <title>Poultry Disease Classification</title>
</head>
<body>
    <h1>Transfer Learning-Based Classification of Poultry Diseases</h1>
    <p>This project aims to develop a transfer learning-based system for classifying poultry diseases into four categories: Salmonella, New Castle Disease, Coccidiosis, and Healthy.</p>

    <h2>Project Scenarios</h2>
    <h3>Scenario 1: Outbreak in a Rural Community</h3>
    <p>Farmers use the mobile app to input symptoms and receive diagnosis & treatment recommendations.</p>

    <h3>Scenario 2: Commercial Poultry Farm Management</h3>
    <p>Early detection of diseases allows quarantine and control measures to prevent outbreaks.</p>

    <h3>Scenario 3: Research and Training for Veterinary Students</h3>
    <p>Students learn to diagnose diseases using the application and modern technology.</p>

    <nav>
        <a href="{{ url_for('prerequisites') }}">Prerequisites & Prior Knowledge</a> |
        <a href="{{ url_for('predict') }}">Try Disease Prediction</a>
    </nav>
</body>
</html>
templates/prerequisites.html
html
Copy
Edit
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <title>Prerequisites - Poultry Disease Classification</title>
</head>
<body>
    <h1>Prerequisites & Prior Knowledge</h1>
    <h2>Software & Packages</h2>
    <ul>
        <li>Anaconda Navigator</li>
        <li>Python packages: numpy, pandas, scikit-learn, matplotlib, scipy, seaborn, tensorflow</li>
    </ul>

    <h2>Prior Knowledge Topics</h2>
    <ul>
        <li>Deep Learning Concepts</li>
        <li>Neural Networks (CNNs, VGG16, etc.)</li>
        <li>Transfer Learning</li>
        <li>Flask Basics</li>
    </ul>

    <nav>
        <a href="{{ url_for('home') }}">Home</a> |
        <a href="{{ url_for('predict') }}">Try Disease Prediction</a>
    </nav>
</body>
</html>
templates/predict.html
html
Copy
Edit
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <title>Upload Image - Predict Poultry Disease</title>
</head>
<body>
    <h1>Upload an Image to Predict Poultry Disease</h1>
    
    {% if error %}
        <p style="color:red;">{{ error }}</p>
    {% endif %}
    
    <form method="POST" enctype="multipart/form-data">
        <input type="file" name="file" accept="image/png, image/jpeg, image/jpg" required />
        <button type="submit">Predict</button>
    </form>

    <nav>
        <a href="{{ url_for('home') }}">Home</a> |
        <a href="{{ url_for('prerequisites') }}">Prerequisites</a>
    </nav>
</body>
</html>
templates/result.html
html
Copy
Edit
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <title>Prediction Result</title>
</head>
<body>
    <h1>Prediction Result</h1>
    <p><strong>The model predicts the poultry disease as:</strong> {{ disease }}</p>

    <nav>
        <a href="{{ url_for('predict') }}">Predict Another</a> |
        <a href="{{ url_for('home') }}">Home</a>
    </nav>
</body>
</html>
4. requirements.txt (sample)
nginx
Copy
Edit
flask
tensorflow
numpy
werkzeug
How to run
Put your trained model file as model.h5 in the project folder (or update app.py accordingly).

Make sure you have Python and the necessary packages installed (pip install -r requirements.txt).

Run the Flask app:
