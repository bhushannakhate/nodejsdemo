# NodeJS + Express (w/EJS) Code to exercise reading in form data and returning a response

This code has a / path (mapped to index.js --> index.ejs) which displays 3 forms each mapped to a different 
uri path in index.js that executes different controller code (for simplicity --as this is simple code, left controller
code in index.js rather than in the controllers directory --which is a better MVC code styling format).   Here is the interface
After hitting the Go button on the first form this is what the results will look like (notice it has read in the form data)

# Lab 3.3
We started this off by creating a Google Cloud project that went by the ID: subtle-task-508217-b2. In Webstorm we used the CLI to install the Google Cloud CLI to be able to deploy the backend onto Google Cloud right from our workspace. We used these commands to login to our accounts and configure the project: gcloud auth login, 
gcloud config set project subtle-task-508217-b2. We didn't include the .env files for obvious reasons, but we put in our Gemini API key and the Google Cloud webapp link to our file. We also had to swap gemini 2.5 flash, to gemini 3.8 flash because it was no longer working. This introduced a problem where if we tested the deployed app too many times we would run out of our daily uses. We deployed the backend using this command: gcloud run deploy smart-speech-coach-backend --source . --region us-west1 --allow-unauthenticated --env-vars-file .env.cloudrun. And received the URL using gcloud run services describe smart-speech-coach-backend --region us-west1 --format="value(status.url)". From there the backend worked. For the frontend we deployed it to Firebase. We went into the frontend folder and used npm run build, then used npx firebase-tools deploy --only hosting --project subtle-task-508217-b2 to deploy it. After getting the link, we tested it and it worked just fine. We were able to get a response after asking Gemini a question. 
# Lab 3.4
