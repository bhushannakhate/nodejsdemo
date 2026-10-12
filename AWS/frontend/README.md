PORT=8080 npm start
https://formdata-808050614981.us-west1.run.app

For web storm:
git pull --ff-only origin main
npm ci
PORT=3001 npm start

cd "/Users/santossoto/Documents/School/Fall 2026/web systems/FormData"
PORT=3002 npm start

For cloud stopping:
gcloud run services update formdata \
--project=labn31 \
--region=us-west1 \
--scaling=0

Enable
gcloud run services update formdata \
--project=labn31 \
--region=us-west1 \
--scaling=auto

Forms
cd "/Users/santossoto/Documents/School/Fall 2026/web systems/FormData"
PORT=3002 npm start

Change: SmartSpeechCoach/frontend/.env

Backend
cd "/Users/santossoto/Documents/School/Fall 2026/web systems/SmartSpeechCoach/backend"
npm run dev

Front end
cd "/Users/santossoto/Documents/School/Fall 2026/web systems/SmartSpeechCoach/frontend"
npm run dev

https://smartspeechcoach-808050614981.us-west1.run.app/api/health

VITE_SERVER_REMOTE=Y
VITE_SERVER_URL_REMOTE=https://smartspeechcoach-808050614981.us-west1.run.app
VITE_SERVER_URL_LOCAL=http://localhost:3003

VITE_SERVER_REMOTE=Y
VITE_SERVER_URL_REMOTE=http://smartspeedcoachsantossoto-env.eba-qb9qw4fm.us-east-2.elasticbeanstalk.com
VITE_SERVER_URL_LOCAL=http://localhost:3003

Stop
gcloud run services update smartspeechcoach \
--project=labn31 \
--region=us-west1 \
--scaling=0

Enable
gcloud run services update smartspeechcoach \
--project=labn31 \
--region=us-west1 \
--scaling=auto

For frontend:
npm run dev inside SmartSpeechCoach/frontend, then open http://localhost:5173/
/api/health


// run my part of lab
cd AWS/backend
npm start

cd AWS/frontend
npm run dev
