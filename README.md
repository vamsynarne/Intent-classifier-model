# Intent Classifier Model

This small project demonstrates:
- Training a tiny text classifier.
- Saving the model artifact.
- Serving predictions via a Flask API (`/predict`).

## Quick start (local)
1. Create a virtualenv and install:
    python3 -m venv .venv
    source .venv/bin/activate   #Local: use this command:  source .venv/Scripts/activate
    pip install -r requirements.txt
    # Run the below command instead of above. This is captured from Demo session from Udemy course ####
    python -m pip install -r requirements.txt
    ####

2. Train the model:
    python model/train.py
    This will create `model/artifacts/intent_model.pkl`.

3. Run the API:
    gunicorn --workers 3 --bind 127.0.0.1:6000 wsgi:app # This is captured from Demo session from Udemy course
    python app.py
    The API will be available at http://127.0.0.1:6000

4. Example request:
    curl -X POST http://127.0.0.1:6000/predict -H "Content-Type: application/json" -d '{"text":"I want to cancel my subscription"}'

    Response:
    {
        "intent": "complaint",
        "probabilities": {"complaint": 0.85, "question": 0.05, ...}
    }
