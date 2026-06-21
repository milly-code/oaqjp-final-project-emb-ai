Here's everything you need to submit for the AI-Graded (Option 1) path:

---

## Task 1: GitHub Repository URL

Submit the public URL of your `README.md` file on GitHub (e.g., `https://github.com/your-username/oaqjp-final-project-emb-ai/blob/main/README.md`)

---

## Task 2: Emotion Detection Application

**2a_emotion_detection** (code from emotion_detection.py):

```python
import json
import requests


def emotion_detector(text_to_analyze):
    url = ('https://sn-watson-emotion.labs.skills.network/v1/'
           'watson.runtime.nlp.v1/NlpService/EmotionPredict')
    headers = {"grpc-metadata-mm-model-id":
               "emotion_aggregated-workflow_lang_en_stock"}
    input_json = {"raw_document": {"text": text_to_analyze}}

    response = requests.post(url, headers=headers, json=input_json, timeout=30)

    if response.status_code == 400:
        return {
            'anger': None,
            'disgust': None,
            'fear': None,
            'joy': None,
            'sadness': None,
            'dominant_emotion': None
        }

    result = json.loads(response.text)

    emotions = result['emotionPredictions'][0]['emotion']

    anger_score = emotions['anger']
    disgust_score = emotions['disgust']
    fear_score = emotions['fear']
    joy_score = emotions['joy']
    sadness_score = emotions['sadness']

    emotion_scores = {
        'anger': anger_score,
        'disgust': disgust_score,
        'fear': fear_score,
        'joy': joy_score,
        'sadness': sadness_score
    }

    dominant_emotion = max(emotion_scores, key=emotion_scores.get)

    emotion_scores['dominant_emotion'] = dominant_emotion

    return emotion_scores
```

**2b_application_creation** (terminal output — you'll need to run this yourself):

```
$ python3
>>> from emotion_detection import emotion_detector
>>> emotion_detector("I love this new technology.")
```

---

## Task 3: Format Output

**3a_output_formatting** — same code as 2a above (it already returns the formatted dictionary).

**3b_formatted_output_test** (terminal output — run this):

```
$ python3
>>> from EmotionDetection import emotion_detector
>>> emotion_detector("I am so happy I am doing this.")
```

Verify dominant_emotion is `'joy'`.

---

## Task 4: Package Validation

**Activity 1:** Submit the public GitHub URL of your `__init__.py` file:
`https://github.com/your-username/oaqjp-final-project-emb-ai/blob/main/EmotionDetection/__init__.py`

The content is:

```python
from .emotion_detection import emotion_detector
```

**4b_packaging_test** (terminal output — run this):

```
$ python3
>>> from EmotionDetection import emotion_detector
>>> emotion_detector("I hate working long hours.")
```

Verify dominant_emotion is `'anger'`.

---

## Task 5: Unit Tests

**5a_unit_testing** (code from test_emotion_detection.py):

```python
import unittest
from EmotionDetection import emotion_detector


class TestEmotionDetection(unittest.TestCase):

    def test_joy(self):
        result = emotion_detector("I am glad this happened")
        self.assertEqual(result['dominant_emotion'], 'joy')

    def test_anger(self):
        result = emotion_detector("I am really mad about this")
        self.assertEqual(result['dominant_emotion'], 'anger')

    def test_disgust(self):
        result = emotion_detector("I feel disgusted just hearing about this")
        self.assertEqual(result['dominant_emotion'], 'disgust')

    def test_sadness(self):
        result = emotion_detector("I am so sad about this")
        self.assertEqual(result['dominant_emotion'], 'sadness')

    def test_fear(self):
        result = emotion_detector("I am really afraid that this will happen")
        self.assertEqual(result['dominant_emotion'], 'fear')


if __name__ == "__main__":
    unittest.main()
```

**5b_unit_testing_result** (run `python3 -m unittest test_emotion_detection.py` and paste output).

---

## Task 6: Flask Web Deployment

**6a_server** (code from server.py):

```python
"""Flask server for the Emotion Detection application."""

from flask import Flask, render_template, request
from EmotionDetection import emotion_detector

app = Flask("Emotion Detector")


@app.route("/emotionDetector")
def emotion_detector_route():
    """
    Analyze the given text for emotions and return a formatted response.
    """
    text_to_analyze = request.args.get("textToAnalyze")

    response = emotion_detector(text_to_analyze)

    if response['dominant_emotion'] is None:
        return "Invalid text! Please try again!"

    return (
        f"For the given statement, the system response is "
        f"'anger': {response['anger']}, "
        f"'disgust': {response['disgust']}, "
        f"'fear': {response['fear']}, "
        f"'joy': {response['joy']} and "
        f"'sadness': {response['sadness']}. "
        f"The dominant emotion is {response['dominant_emotion']}."
    )


@app.route("/")
def render_index_page():
    """Render the index page of the application."""
    return render_template("index.html")


if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

**6b_deployment_test.png** — Run `python3 server.py`, open `localhost:5000` in browser, test with "I think I am having fun", and screenshot.

---

## Task 7: Error Handling

**7a_error_handling_function** — same emotion_detection.py code as above (the `status_code == 400` block handles it).

**7b_error_handling_server** — same server.py code as above (the `dominant_emotion is None` check handles it).

**7c_error_handling_interface.png** — Run the app, submit a blank input, and screenshot the "Invalid text! Please try again!" message.

---

## Task 8: Static Code Analysis

**8a_server_modified** — same server.py code as above (already has docstrings for 10/10).

**8b_static_code_analysis** (run `pylint server.py` and paste the output showing 10/10).

---

The only things you need to do manually are:
1. Run the commands in the IBM Skills Network lab to capture terminal output
2. Take the 3 screenshots (6b, 7c, and push to GitHub for Task 1 & 4a)
3. Push code to your GitHub fork