Task 2: Create an emotion detection application using the Watson NLP library
The Watson NLP libraries are embedded. Therefore, there is no need of importing them to your code. You only need to send a post request to the correct function in the library and receive the output.

For this project, you'll use the Emotion Predict function of the Watson NLP Library. For accessing this function, the URL, the headers, and the input json format is as follows.

plaintext

URL: 'https://sn-watson-emotion.labs.skills.network/v1/watson.runtime.nlp.v1/NlpService/EmotionPredict'
Headers: {"grpc-metadata-mm-model-id": "emotion_aggregated-workflow_lang_en_stock"}
Input json: { "raw_document": { "text": text_to_analyze } }
Note that the text_to_analyze is being used as a variable that holds the actual written text that needs to be analysed.

Create a file named emotion_detection.py in final_project folder.

In the emotion_detection.py file, write the function to run emotion detection using the appropriate Emotion Detection function. Name this function emotion_detector.

Note: Assume that the text to be analysed is passed to the function as an argument and is stored in the variable text_to_analyze. The value being returned must be the text attribute of the response object as received from the Emotion Detection function.

Assessment:

For Option 1 - AI Graded Submission and Evaluation: Copy and paste code from the emotion_detection.py file that shows the application function in a text file and save it as 2a_emotion_detection for the Final project submission and evaluation.

For Option 2 -Peer-Graded Submission and Evaluation: Take a screenshot of the code you write and save it as 2a_emotion_detection.png for Peer Assignment.

The application should now be importable using Python shell. Open a python3 shell.

Import the application.

After you successfully import the application, test your application with the text: "I love this new technology."

Assessment:

For Option 1 - AI Graded Submission and Evaluation: Copy and paste terminal output showing that the application was imported and tested without errors in a text file and save it as 2b_application_creation for the Final project submission and evaluation.

For Option 2 -Peer-Graded Submission and Evaluation: Take a screenshot of the terminal with all three steps included in it along with the final output. Name this file 2b_application_creation.pngfor Peer Assignment.

Note: In case the python shell shows an error ModuleNotFoundError: No module named 'requests', you may install the requests library to your IDE using the following command on the terminal.

plaintext

python3 -m pip install requests
Optional:

At any point of time if you want to push your code to your forked GitHub repository, you can do so by following the instructions provided in this link.

Task 3: Format the output of the application
Convert the response text into a dictionary using the json library functions.

Note the content formatting in this dictionary.

Extract the required set of emotions, including anger, disgust, fear, joy and sadness, along with their scores.

Write the code logic to find the dominant emotion, which is the emotion with the highest score.

Then, modify the emotion_detector function to return the following output format.

plaintext

{
'anger': anger_score,
'disgust': disgust_score,
'fear': fear_score,
'joy': joy_score,
'sadness': sadness_score,
'dominant_emotion': '<name of the dominant emotion>'
}
Assessment:

For Option 1 - AI Graded Submission and Evaluation: Copy and paste code from the emotion_detection.py file showing that the modified emotion_detector function returns the correct output format in a text file and save it as 3a_output_formatting for the Final project submission and evaluation.

For Option 2 -Peer-Graded Submission and Evaluation: Take a screenshot of the modified function code and save it as 3a_output_formatting.png for Peer Assignment.

Test the application in the python3 shell again, with the statement I am so happy I am doing this.

Verify that the response received has the dominant emotion is joy.

Assessment:

For Option 1 - AI Graded Submission and Evaluation: Copy and paste the terminal output showing that the output format is accurate in a text file and save it as 3b_formatted_output_test for the Final project submission and evaluation.

For Option 2 -Peer-Graded Submission and Evaluation: Take a screenshot of the output from the terminal shell and save it as 3b_formatted_output_test.png for Peer Assignment.

Optional

At any point of time if you want to push your code to your forked GitHub repository, you can do so by following the instructions provided in this link.


Task 4: Package the application
In this task, you will package the application created in the previous steps.

Perform the relevant steps in creation of the package. Set the name of the package to EmotionDetection.

Assessment:

For Option 1 - AI Graded Submission and Evaluation: Ensure that you have pushed your init.py file to your forked GitHub repository by following the instructions link. in the provided link. Then, copy and save the public GitHub URL of the __init__.py file that contains the code to import the application module for the Final project submission and evaluation.

For Option 2 -Peer-Graded Submission and Evaluation: Take a screenshot of the contents of the init file along with the final folder structure of the final_project directory.Make sure to fit both of the images into a single screenshot and name it 4a_packaging.pngfor Peer Assignment.

To make sure that the EmotionDetection is a valid package, you need to test the package. To do this:

Run a python shell in the terminal.

Import the emotion_detector function from the package.

If the package is created accurately, you will not receive any error messages.

Test run the function again with the statement I hate working long hours.
Verify that the output displays the dominant emotion as anger.
Assessment:

For Option 1 - AI Graded Submission and Evaluation: Copy and paste the terminal output validating that EmotionDetection is a valid package and save it as 4b_packaging_test for the Final project submission and evaluation.

For Option 2 -Peer-Graded Submission and Evaluation: Take a screenshot of this terminal output and save it as 4b_packaging_test.pngfor Peer Assignment.


Task 5: Run unit tests on your application
With a functional application being available, you now need to run unit tests to validate the application output.

To run unit tests, create a new file, test_emotion_detection.py that calls the required application function from the package and tests it for the following statements and dominant emotions.

Statement	Dominant Emotion
I am glad this happened	joy
I am really mad about this	anger
I feel disgusted just hearing about this	disgust
I am so sad about this	sadness
I am really afraid that this will happen	fear
Assessment: For Option 1 - AI Graded Submission and Evaluation: Copy and paste the code from the test_emotion_detection.py file showing the required unit tests in a text file and save it as 5a_unit_testing for the Final project submission and evaluation.

For Option 2 -Peer-Graded Submission and Evaluation: Take a screenshot of the code and save it as 5a_unit_testing.pngfor Peer Assignment.

Execute the test_emotion_detection.py file on terminal.

Check the unit test output to verify that the unit tests have passed.

Assessment: For Option 1 - AI Graded Submission and Evaluation: Copy and paste the terminal output showing that all unit tests passed in a text file and save it as 5b_unit_testing_result for the Final project submission and evaluation.

For Option 2 -Peer-Graded Submission and Evaluation: Take a screenshot of the code and save it as 5b_unit_testing_result.pngfor Peer Assignment.

Optional:

At any point of time if you want to push your code to your forked GitHub repository, you can do so by following the instructions provided in this link.

Task 6: Web deployment of the application using Flask
After all the tests are successfully completed, you need to deploy the application on the web. This will enable the customer to access and use the application.

Note: The index.html file in the templates folder and mywebscript.js file in the static folder have been provided as a part of the repo. These files do not need to be updated in this project.

You have to create the server.py file from scratch. Note the following requirements of this task.

Note: server.py is a part of final_project folder.

Make sure that the Flask decorator for the application calling function is /emotionDetector.

The customer has requested the output to be displayed in the format as displayed in the example below.

Example Output Let's say that you want to evaluate the statement I love my life. The statement is processed as follows:

json

{
"anger": 0.006274985, 
"disgust": 0.0025598293, 
"fear": 0.009251528, 
"joy": 0.9680386, 
"sadness": 0.049744144, 
"dominant_emotion":"joy"
}
The response is displayed as:

For the given statement, the system response is 'anger': 0.006274985, 'disgust': 0.0025598293, 'fear': 0.009251528, 'joy': 0.9680386 and 'sadness': 0.049744144. The dominant emotion is joy.

Application needs to be deployed on localhost:5000

Assessment:

For Option 1 - AI Graded Submission and Evaluation: Copy and paste the code from the server.py file showing the web deployment of the application using Flask in a text file and save it as 6a_server for the Final project submission and evaluation.

For Option 2 -Peer-Graded Submission and Evaluation: Take a screenshot of the final contents of server.py and name it 6a_server.png for Peer Assignment.

Assessment : Take a screenshot of the final deployed application, testing it for the statement "I think I am having fun". Name this image as 6b_deployment_test.png both for Option 1 -Final project submission and evaluation and For Option 2 -Peer-Graded Submission and Evaluation.

Optional:

At any point of time if you want to push your code to your forked GitHub repository, you can do so by following the instructions provided in this link.

Task 7: Incorporate Error handling
Incorporate the error handling capability in your function emotion_detector to manage blank entries from users, i.e. running the application without any input.

Access the status_code attribute of the server response to correctly display the system response for blank entries.

For status_code = 400, make the function return the same dictionary, but with values for all keys being None.

Assessment:

For Option 1 - AI Graded Submission and Evaluation: Copy and paste the code from the emotion_detection.py file showing the updated emotion_detector function for status code 400 in a text file and save it as 7a_error_handling_function for the Final project submission and evaluation.

For Option 2 -Peer-Graded Submission and Evaluation: Take a screenshot of the modified function and name it 7a_error_handling_function.pngfor Peer Assignment.

Modify server.py to incorporate error handling when the dominant_emotion is None. In this scenario, the response should display a message Invalid text! Please try again!.

Assessment:

For Option 1 - AI Graded Submission and Evaluation: Copy and paste the code from the server.py file showing the handling of blank input errors in a text file and save it as 7b_error_handling_server for the Final project submission and evaluation.

For Option 2 -Peer-Graded Submission and Evaluation: Take a screenshot of this edited file and save it as 7b_error_handling_server.png for Peer Assignment.

Deploy the application and test it for blank entries.

The output should display the error message, Invalid text! Please try again!.

Assessment:

Take a screenshot of the output displaying the error message and name it 7c_error_handling_interface.png both for Option 1 -Final project submission and evaluation and For Option 2 -Peer-Graded Submission and Evaluation.

Optional:

At any point of time if you want to push your code to your forked GitHub repository, you can do so by following the instructions provided in this link.

Task 8: Run static code analysis
Finally, its time to check code compliance.

Run static code analysis on the code you created. Use PyLint library on server.py file and try to generate a 10/10 score. You will have to modify the server.py file to get this score.

Assessment:

For Option 1 - AI Graded Submission and Evaluation: Copy and paste the code from the server.py file demonstrating the execution of static code analysis in a text file and save it as 8a_server_modified for the Final project submission and evaluation.

For Option 2 -Peer-Graded Submission and Evaluation: Take a screenshot of the modified file and name it as 8a_server_modified.png for Peer Assignment.

Note: The difference between a 9/10 score and a 10/10 score may be use of Docstrings. Include Docstrings in all functions of your codes.

Assessment :

For Option 1 - AI Graded Submission and Evaluation: Copy and paste the terminal output showing a perfect score for static code analysis in a text file and save it as 8b_static_code_analysis for the Final project submission and evaluation.

For Option 2 -Peer-Graded Submission and Evaluation: Take a screenshot of a 10/10 output on the terminal after running static code analysis. Name the screenshot as 8b_static_code_analysis.png for Peer Assignment.

Submission Checklist
Follow the checklist below to verify that your project meets all requirements before submission. Submit your work through either Option 1: AI-Graded Submission and Evaluation or Option 2: Peer-Graded Submission and Evaluation, depending on the submission path you choose for project evaluation.

Follow the submission checklist below if you are proceeding with Option 1: AI-Graded Submission and Evaluation:

-Task 1: Submit the GitHub repository URL

Submit the public GitHub repository URL of the README.md file, which contains the project name details.
-Task 2: Create an emotion detection application using the Watson NLP library

Activity 1: Submit the code from the emotion_detection.py file that shows the application function.
Activity 2: Submit the terminal output showing that the application was imported and tested without errors.
-Task 3: Format the output of the application

Activity 1: Submit the code from the emotion_detection.py file showing that the modified emotion_detector function returns the correct output format.
Activity 2: Submit the terminal output showing that the output format is accurate.
-Task 4: Validate the EmotionDetection package

Activity 1: Submit the public GitHub repository URL of the init.py file which includes the code to import the application module.
Activity 2: Submit the terminal output validating that EmotionDetection is a valid package.
-Task 5: Run unit tests on your application

Activity 1: Submit the code from the test_emotion_detection.py file showing the required unit tests.
Activity 2: Submit the terminal output showing that all unit tests passed.
-Task 6: Web deployment of the application using Flask

Activity 1: Submit the code from the server.py file showing the web deployment of the application using Flask.
Activity 2: Upload the screenshot named 6b_deployment_test.png showing the application deployment.
-Task 7: Incorporate error handling

Activity 1: Submit the code from the emotion_detection.py file showing the updated emotion_detector function for status code 400.
Activity 2: Submit the code from the server.py file showing the handling of blank input errors.
Activity 3: Upload the screenshot named 7c_error_handling_interface.png validating error handling functionality.
-Task 8: Run static code analysis

Activity 1: Submit the code from the server.py file demonstrating the execution of static code analysis.
Activity 2: Submit the terminal output showing a perfect score for static code analysis.