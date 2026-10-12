# README for SmartSpeechCoach


## Update .env files in both frontend and backend
Make sure your information is correct --like frontend .env has the Google Google Cloud Run deployed url for the backend.  There are 2 backend files one .env for local deployment and .env.cloudrun due to fact that CloudRun requires YAML formatting and no port specification.   See .env.example files for understanding needed content.
* frontend/.env
* backend/.env
* backend/.env.cloudrun


## Run locally on macOS (including WebStorm)
Open two terminal tabs in the `AWS` folder.

Start the backend in the first tab:
```sh
cd backend
npm start
```
The backend URL uses `PORT` from `backend/.env` (currently `http://localhost:3003`).
Check it at `http://localhost:3003/api/health`.

Start the frontend in the second tab:
```sh
cd frontend
npm run dev -- --host 127.0.0.1 --port 5173 --strictPort
```
Open `http://localhost:5173` in your browser.

`frontend/.env.development.local` sets `VITE_SERVER_REMOTE=N` and
`VITE_SERVER_URL_LOCAL=http://localhost:3003` for local development.
If you change the backend port, update this URL too and restart Vite.
This override applies only to the development server. Production builds use
the deployment settings in `frontend/.env`.

If dependencies are missing, run `npm ci` in both `backend` and `frontend` first.
Stop each server with Control+C in its terminal.

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