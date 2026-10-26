# NodeJS + Express (w/EJS) Code to exercise reading in form data and returning a response

This code has a / path (mapped to index.js --> index.ejs) which displays 3 forms each mapped to a different 
uri path in index.js that executes different controller code (for simplicity --as this is simple code, left controller
code in index.js rather than in the controllers directory --which is a better MVC code styling format).   Here is the interface
After hitting the Go button on the first form this is what the results will look like (notice it has read in the form data)

# Lab 3.3
We created the Google Cloud project `subtle-task-508217-b2` and configured the Google Cloud CLI for deployment from WebStorm.

First, we authenticated and selected the project:


gcloud auth login
gcloud config set project subtle-task-508217-b2

From the backend directory, we deployed the backend to Google Cloud Run:
gcloud run deploy smart-speech-coach-backend --source . --region us-west1 --allow-unauthenticated --env-vars-file .env.cloudrun
We retrieved the deployed service URL with:
gcloud run services describe smart-speech-coach-backend --region us-west1 --format="value(status.url)"
The frontend was then built and deployed to Firebase Hosting:
cd frontend
npm run build
npx firebase-tools deploy --only hosting --project subtle-task-508217-b2

# Lab 3.4
The Lab 3.4 deployment reused the Node.js/Express backend from Lab 3.3. Only the deployment configuration and frontend API URL needed to be updated.
### Deployment Process

1. Configured AWS credentials using the AWS CLI.
2. Initialized the backend for Elastic Beanstalk:

   ```bash
   eb init smart-speech-coach-backend --platform node.js --region us-west-2
3. Selected the Elastic Beanstalk environment:
  eb use smart-speech-coach-env
4. Added the required environment variables in the Elastic Beanstalk environment properties, including:
    GEMINI_API_KEY
    geminiAskAnythingModel
    askAnythingPrompt
    allowedOrigins
  The Gemini API key was stored in AWS environment settings and was not committed to GitHub.  
5. Added an .ebignore file to exclude node_modules, environment files, logs, and other unnecessary files.
6. Deployed the backend:
7. Added an AWS CloudFront distribution using the Elastic Beanstalk URL as its origin. The /api/* behavior was configured to support POST and OPTIONS requests, forward CORS headers, and disable API response caching.
8. Updated the frontend remote API URL to use the CloudFront HTTPS URL.
9. Rebuilt and redeployed the frontend to Firebase Hosting.

# Deployment Comparison
| Category | Google Cloud Run | AWS Elastic Beanstalk |
|---|---|---|
| Deployment | `gcloud run deploy --source .` | `eb deploy` |
| Application code | Node.js/Express backend | Same Node.js/Express backend |
| Infrastructure | Managed serverless container service | Managed Node.js environment using AWS resources |
| HTTPS | Automatically provided by the Cloud Run service URL | Provided through CloudFront in front of the Elastic Beanstalk HTTP endpoint |
| Backend URL | [Cloud Run service](https://smart-speech-coach-backend-1025835365254.us-west1.run.app) | [CloudFront HTTPS endpoint](https://d2jvxmo54ed3y.cloudfront.net) |
| Frontend | [Firebase Hosting](https://subtle-task-508217-b2.web.app) | Same Firebase frontend, configured to call the AWS backend |
| Code changes | Frontend `fetch()` calls the Cloud Run backend | Added AWS environment configuration, `.ebignore`, CloudFront routing, CORS settings, and changed the frontend API URL |
Both deployments use the same Node.js/Express backend and Gemini API integration. The main AWS-specific work involved configuring Elastic Beanstalk environment properties, deploying the backend, placing CloudFront in front of Elastic Beanstalk for HTTPS access, and updating the Firebase frontend to use the CloudFront API URL.
