# react-todo-app

# Pre-requisites:

Docker installed.
Kubernetes installed / managed k8s cluster (any kind).
Docker hub account with repository to store the image.

# STEPS:

## Clone the repository.

```$ git clone https://github.com/MaheshRautrao/React-Todo-list.git```

## Create a Dockerfile in the root directory of the application. Below is the link to the Dockerfile .

Ref: https://github.com/akshaykumart/react-todo-app/blob/main/Dockerfile

```$ cd React-Todo-list```
```$ vi Dockerfile```

Below Image is the file structure of the app with Dockerfile.

![image](https://github.com/user-attachments/assets/d7ab9a99-db4c-456c-8f3a-cf5f382238d7)

## Build the Docker Image out of Dockerfile.

```$ docker build -t apica-react-app .```

![image](https://github.com/user-attachments/assets/4953a780-2b24-4266-8ef5-9ee6c8f7ff84)

## Verify the Docker image created.

```$ docker images```

![image](https://github.com/user-attachments/assets/f637f787-fe03-467b-a901-4f76c213eb30)

## Push the image to registry ( Docker hub ).

```$ docker login```
```$ docker tag apica-react-app akshaykumart/apica-react-app:latest```
```$ docker push akshaykumart/apica-react-app:latest```

![image](https://github.com/user-attachments/assets/413ce455-ddf8-4a2a-92ba-ef3384ffab5e)

![image](https://github.com/user-attachments/assets/68f0ebeb-ecb4-4a81-83b0-91b941bec5dd)

Login to the docker hub and verify the image pushed .

![image](https://github.com/user-attachments/assets/0af3ff75-2349-4c39-b883-10e45031f10c)


## Create a Deployment and Service kubernetes manifests.

Ref: https://github.com/akshaykumart/react-todo-app/blob/main/deployment.yaml
        https://github.com/akshaykumart/react-todo-app/blob/main/service.yaml

```$ vi deployment.yaml```
```$ vi service.yaml```


## Create a namespace for application.

```$ microk8s kubectl create namespace apica```


## Apply Deployment and Service manifests.

```$ microk8s kubectl apply -f deployment.yaml -n apica```

![image](https://github.com/user-attachments/assets/2ea9ec05-c172-4a1f-a4e4-58c90054853f)

```$ microk8s kubectl apply -f service.yaml -n apica```

![image](https://github.com/user-attachments/assets/19bd477a-f511-43d0-b6ce-5c581c9bacb7)


## Verify the deployments, pods, service created in the previous step.

```$ microk8s kubectl get deployments -n apica```

![image](https://github.com/user-attachments/assets/ed86587c-4f52-4040-9980-6e333b00faa4)

```$ microk8s kubectl get pods -n apica```

![image](https://github.com/user-attachments/assets/106de3b3-8bec-489f-ba1c-e8e2be6b00f6)


```$ microk8s describe pod <podname> -n apica ```

![image](https://github.com/user-attachments/assets/f0d2a9b0-bd61-4a2f-a22f-290aaef1dc99)


```$ microk8s kubectl get service -n apica```

![image](https://github.com/user-attachments/assets/c0ae9bc1-f6c4-4568-8ec5-108a256c8dcb)


Try accessing the application using nodeport.

```$ http://<node_ip>:<node_port>```

For example: http://192.168.64.2:30519

![image](https://github.com/user-attachments/assets/e759ae87-f752-4e66-ba24-3ec949e4d0c5)

![image](https://github.com/user-attachments/assets/9bb10a91-7d0d-4b26-b871-c6d412681e1f)





