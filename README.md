# Multiplayer-Game
AWS Node.js SDK


npm install --prefix scripts/ && npm install --prefix application

echo "export AWS_REGION=us-east-1" >> env.sh && source env.sh

bash scripts/create-table.sh

node scripts/createGame.js

node scripts/performMove.js

echo "export PHONE_NUMBER=+15555555555" >> env.sh && source env.sh

node scripts/sendMessage.js

bash scripts/create-user-pool.sh

User Pool created with id <user-pool-id>

bash scripts/create-user-pool-client.sh

User Pool Client created with id <client-id>

bash scripts/create-lambda.sh

bash scripts/create-rest-api.sh

source env.sh

curl -X GET ${BASE_URL}/games/5b5ee7d8

curl -X POST ${BASE_URL}/users \
  -H 'Content-Type: application/json' \
  -d '{
	"username": "myfirstuser",
	"password": "Password1",
	"phoneNumber": "'${PHONE_NUMBER}'",
	"email": "test@email.com"
}'

export FIRST_ID_TOKEN=<idToken>

export SECOND_ID_TOKEN=<idToken>

curl -X POST ${BASE_URL}/games \
 -H 'Content-Type: application/json' \
  -H "Authorization: ${FIRST_ID_TOKEN}" \
  -d '{
	"opponent": "theseconduser"
}'

export GAME_ID=<yourGameId>

curl -X POST ${BASE_URL}/games \
 -H 'Content-Type: application/json' \
  -d '{
	"opponent": "theseconduser"
}'

curl -X GET ${BASE_URL}/games/${GAME_ID}

curl -X POST ${BASE_URL}/games/${GAME_ID} \
  -H "Authorization: ${SECOND_ID_TOKEN}" \
  -H 'Content-Type: application/json' \
  -d '{
	"changedHeap": "heap1",
	"changedHeapValue": 0
}'

curl -X POST ${BASE_URL}/games/${GAME_ID} \
  -H "Authorization: ${SECOND_ID_TOKEN}" \
  -H 'Content-Type: application/json' \
  -d '{
	"changedHeap": "heap3",
	"changedHeapValue": 0
}'


bash scripts/delete-resources.sh