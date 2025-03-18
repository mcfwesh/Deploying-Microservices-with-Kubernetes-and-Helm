# Microservices Deployment with Kubernetes and Helm

A hands-on learning project demonstrating the progression from basic Kubernetes deployments to Helm-based microservices orchestration, using Google's microservices demo application.

## Related Tasks from Module 10

- **Create Helm Chart for Microservices**

  - Developed a Helm chart to manage microservices deployments
  - Reused common configurations for services

- **Deploy Microservices with Helmfile**

  - Utilized Helmfile to manage and deploy multiple services efficiently

- **Deploy Microservices with Production & Security Best Practices**
  - Implemented security best practices for Kubernetes deployments
  - Used DigitalOcean for the deployment environment

## Project Overview

This project documents the learning journey of deploying microservices using different approaches, from basic Kubernetes manifests to Helm charts. The implementation uses Google's [Online Boutique](https://github.com/GoogleCloudPlatform/microservices-demo) sample microservices application.

## Learning Progression

1. **Initial Setup**

   - Established a Kubernetes cluster on DigitalOcean:
     - Logged into the DigitalOcean dashboard
     - Navigated to the Kubernetes section
     - Clicked on "Create Cluster"
     - Selected the desired region and node specifications
     - Completed the setup by following the on-screen instructions
   - Downloaded the Kubernetes config file from the DigitalOcean dashboard
   - Assigned the config file to the `KUBECONFIG` environment variable:
     - **Command:**
       ```bash
       export KUBECONFIG=path/to/your/kubeconfig
       ```

2. **Basic Kubernetes Deployment**

   - Created and deployed microservices using raw Kubernetes manifests
     - **Command:**
       ```bash
       kubectl apply -f config.yaml
       ```
   - Implemented services like payment, email, currency, redis, and frontend
   - Configured appropriate probes, ports, and environment variables
     - **Command:**
       ```bash
       kubectl describe deployment <deployment-name>
       ```

3. **Helm Chart Migration**

   - Refactored deployments into reusable Helm charts
     - **Command:**
       ```bash
       helm create <chart-name>
       ```
   - Created shared templates for common configurations
   - Implemented two main charts:
     - `microservices`: Generic chart for application services
     - `redis`: Specialized chart for Redis deployment
   - **Command:**
     ```bash
     helm lint <chart-directory>
     ```

4. **Helmfile Integration**

   - Implemented Helmfile for orchestrating multiple Helm releases
     - **Command:**
       ```bash
       helmfile apply
       ```
   - Streamlined deployment process
     - **Command:**
       ```bash
       helmfile sync
       ```

5. **Accessing the Frontend Service**
   - The frontend service is exposed via a LoadBalancer
   - Accessible at `http://<LoadBalancerIP>:3000`

## Repository Structure

- `config.yaml`: Original Kubernetes manifests
- `helm-charts/`
  - `microservices/`: Common chart for application services
  - `redis/`: Specialized chart for Redis deployment

## Technologies Used

- Kubernetes
- Helm
- Helmfile
- DigitalOcean Kubernetes
- Google Cloud Microservices Demo Images

## Reference

- [Google Samples Repository](https://console.cloud.google.com/artifacts/docker/google-samples/us/gcr.io)
- [Original Microservices Demo](https://github.com/GoogleCloudPlatform/microservices-demo)
