## Problem Statement: Experiment with MongoDB and deploying Spring Boot application on K8s Cluster in Azure AKS

* This is to deploy Spring Boot application using MongoDB on AKS cluster.
      

This exercise contains the following: 

    - user-service      - A Spring Boot application 
    - k8s-manifests     - Contains following manifest files:    
        - mongodb.yml          - To create persistent volume, persistent volume claim, deployment, and service of type ClusterIP for mongodb.
        - userservice.yml      - To create the deployment, service of type LoadBalancer for user-service microservice.
      
Note: You need to go through the comments thoroughly and complete the exercise.

Understand and do the following steps to complete and verify the outcome:
    
    1. Make sure AKS cluster is created and is ready. 
    2. Define `mongodb.yml' following the comments given in the file.
    3. Run command `kubectl apply -f mongodb.yml` to create mongodb PV, PVC, Deployment and Service.
    4. Modify the properties in `application.yml` of  `user-service` following the comments given in the file.
    5. Push the docker image named `userservice-mongo` of user-service application to DockerHub.
    6. Define service of type LoadBalancer and deployment in `userservice.yml' following the comments given in the file.
    7. Run command `kubectl describe service <service name>` and look up for external IP.
    8. Open POSTMAN and hit the POST endpoint using `http://<external-ip>:<port>/api/v1/user` to save the user in database.
    9. Run command `kubectl exec -it <mongodb pod name> -- /bin/bash`  to get inside the mongo container.
        - Run mongo commands and verify if the data is inserted in the `User` collection of the userDb` database.
    10. Open POSTMAN and hit the GET endpoint using `http://<external-ip>:<port>/api/v1/users` to get all users from the database.
    11. To test if the data is persisted:
        - Run command `kubectl delete pod <mongo pod name>` to delete the pod.
        - Check Get API for persistence.    
    
### Instructions
 - Take care of whitespace/trailing whitespace
 - Do not change the provided code unless instructed
 - Ensure your code compiles without any errors/warning/deprecations 
 - Follow best practices while coding
