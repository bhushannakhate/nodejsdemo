# README for SmartSpeechCoach


## Update .env files in both frontend and backend
Make sure your information is correct --like frontend .env has the Google Google Cloud Run deployed url for the backend.  There are 2 backend files one .env for local deployment and .env.cloudrun due to fact that CloudRun requires YAML formatting and no port specification.   See .env.example files for understanding needed content.
* frontend/.env
* backend/.env
* backend/.env.cloudrun


## Local Run Front End
```
cd frontend                   
npm.cmd run build                              
```
## Local Run Back End
```
cd C:\Grewe\Classes\CS351\VSCode\Lab2React\backend                                 npm.cmd start 
```                              

## Deploy &Launch Front End to Firebase
How to deploy to Firebase. Will deploy to [https://smartspeechcoach.web.app](https://smartspeechcoach.web.app)
```
cd C:\Grewe\Classes\CS351\VSCode\Lab2React\frontend
npm.cmd run build
cd ..
firebase.cmd deploy --only hosting
```

## Launch BackEnd on Google Cloud Run
will deploy to something like https://smart-speech-coach-backend-xxxxx-uw.a.run.app    in general : https://YOUR-CLOUD-RUN-URL/api/health is a url you can invoke to see if running.
```
cd C:\Grewe\Classes\CS351\VSCode\Lab2React\backend
gcloud config set project smart-speech-coach
gcloud run deploy smart-speech-coach-backend --source . --region us-west1 --allow-unauthenticated --env-vars-file .env.cloudrun
```