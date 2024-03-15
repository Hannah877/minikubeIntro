# minikubeIntro

# Create 3 node
minikube start --nodes 3

# Build image and deploy
Go to db directory:
docker build -t your-docker-username/mysql-sakila:latest .

docker push your-docker-username/mysql-sakila:latest

kubectl apply -f db-deployment.yaml

Go to backend directory:
docker build -t your-docker-username/nextjs-frontend:latest .

docker push your-docker-username/fastapi:latest

kubectl apply -f be-deployment.yaml

Go to frontend directory:
docker build -t your-docker-username/fastapi:latest .

docker push your-docker-username/nextjs-frontend:latest

kubectl apply -f fe-deployment.yaml

minikube dashboard: all three services running

# Run the app
kubectl port-forward svc/fastapi 8080:8000

minikube service nextjs-frontend-service

