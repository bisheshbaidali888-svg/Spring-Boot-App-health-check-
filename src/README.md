STEP 1: Project made through
Spring Initializr (start.spring.io) bata naya project banako
Dependencies: Spring Web, Spring Data JPA, PostgreSQL Driver, Actuator
VS Code ma open gareko.

STEP 2: Configuration Gareko
application.yaml ma DB config haleko
.env file banako — credentials store gareko
.gitignore ma .env add gareko **security ko lagi**


STEP 3: Docker Setup
Dockerfile banako
mvn clean package — JAR file banako
docker build — Docker image banako
docker push — DockerHub ma upload gareko

STEP 4: Kubernetes Setup **manage the docker app**
k8s/namespace.yaml — dev namespace banako 
k8s/secret.yaml — DB credentials secret ma store gareko
k8s/deployment.yaml — 2 replicas deploy gareko
k8s/service.yaml — ClusterIP service banako
Minikube ma sabai apply gareko

#note: kubernetes (big building)
Namespace(building ko sepret sepret room)
dev(Deployment team room)
staging(Testing team room)
prod(Live room)

STEP 5: GitHub Actions CI/CD
.github/workflows/deploy.yaml banako
GitHub Secrets add gareko:
DOCKER_USERNAME
DOCKER_PASSWORD
Push garda automatically build + push huncha **No more manually typing**

STEP 6: Verification
kubectl get ns — dev namespace 
kubectl get pods -n dev 
kubectl get deployment -n dev 
kubectl get svc -n dev 
kubectl get secret -n dev 

##some commands uses in this project!!
          FOR DOCKER 
postSQL run = docker run --name my-postgres -e POSTGRES_USER=admin -e POSTGRES_PASSWORD=secret123 -e POSTGRES_DB=testdb -p 5432:5432 -d postgres:15
build image= mvn clean package -DskipTests
docker build -t bisheshbaidali/spring-postgres-app:latest .
push dockerhub= docker push bisheshbaidali/spring-postgres-app:latest
DB stop/start= docker start my-postgres *status UP*
               docker stop my-postgres   *status DOWN*

FOR KUBERNETES
kubectl apply -f k8s/namespace.yaml
kubectl apply -f k8s/secret.yaml
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml

pushing in github account
git init
git add .
git commit -m "valid message"
git remote add origin url
git push -u origin main

