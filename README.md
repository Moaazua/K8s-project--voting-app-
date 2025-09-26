Voting App on Minikube (Kubernetes)
📌 Overview

This project demonstrates how to deploy a containerized microservices voting application on a Kubernetes cluster running on Minikube.
The application is fully managed using declarative YAML manifests, showcasing a complete pipeline that includes frontend, backend, cache, and database layers.

🧩 Application Components

The system is composed of multiple microservices, each defined in its own deployment manifest:

vote-deployment.yaml → Python-based frontend where users can cast their votes.

result-deployment.yaml → Node.js frontend that displays the voting results in real-time.

worker-deployment.yaml → Background service responsible for processing and transferring votes.

redis-deployment.yaml → In-memory database (Redis) used for temporary vote storage.

db-deployment.yaml → PostgreSQL database for persistent storage of voting data.

ingress.yaml → NGINX Ingress resource that exposes the services externally and routes traffic to the appropriate frontend.

⚙️ Implementation Details

All microservices were deployed using:

kubectl apply -f *.yaml


ClusterIP Services were configured to enable communication between Pods internally within the cluster.

Ingress Controller was set up with the hostname voting.local to route traffic:

/vote → Python voting frontend.

/result → Node.js results frontend.

Verified Pod-to-Pod communication using environment variables, kubectl exec, and kubectl logs.

Troubleshot common deployment issues such as 500 Internal Server Error caused by database connection problems.

✅ Outcome

Successfully deployed and tested the Voting App end-to-end on Minikube.

Gained hands-on experience with:

Kubernetes Deployments

Services (ClusterIP)

Ingress routing with NGINX

Debugging and troubleshooting Pods

Built a complete microservices pipeline integrating frontend, backend, cache, and persistent storage.

🚀 Key Learnings

Working with declarative Kubernetes manifests for reproducible deployments.

Understanding microservices communication using Kubernetes Services.

Managing application exposure with Ingress Controllers.

Hands-on troubleshooting in real-world deployment scenarios.
