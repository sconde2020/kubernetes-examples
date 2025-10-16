# Kubernetes Learning Plan: Tutorials Overview

This 12-week plan guides you through Kubernetes fundamentals to advanced production skills via hands-on mini projects.

## Phase 1 – Foundations (Weeks 1–3)
**Goal:** Get familiar with core Kubernetes objects by deploying simple apps.

- **Project 1: Hello Kubernetes**
    - Deploy Nginx Pod, expose via NodePort Service, scale with Deployment
    - *Skills:* Pods, Deployments, Services, scaling

- **Project 2: Configured Web App**
    - Create backend web app (Spring Boot)
    - Deploy backend app, use ConfigMap for configs, Secret for DB password
    - *Skills:* ConfigMaps, Secrets, app configuration

- **Project 3: Persistent Database**
    - Deploy Postgres with PersistentVolume & PVC, connect backend app
    - *Skills:* Persistent storage, app-to-DB communication

---

## Phase 2 – Intermediate (Weeks 4–6)
**Goal:** Build a multi-tier app with networking and background tasks.

- **Project 4: Full-Stack Application**
    - Deploy frontend, backend, database; expose frontend via Ingress; use ClusterIP services
    - *Skills:* Multi-tier apps, Ingress, service discovery

- **Project 5: Health & Security**
    - Add readiness/liveness probes; restrict DB access with NetworkPolicy
    - *Skills:* Pod health checks, network policies

- **Project 6: Scheduled Jobs**
    - Add CronJob for DB cleanup; set resource requests/limits
    - *Skills:* Jobs, CronJobs, resource management

---

## Phase 3 – Advanced (Weeks 7–9)
**Goal:** Add monitoring, autoscaling, and security best practices.

- **Project 7: Logging & Monitoring with EFK**
    - Deploy Fluentbit, Elasticsearch, Kibana; install Prometheus & Grafana
    - *Skills:* EFK stack, observability

- **Project 8: Autoscaling**
    - Deploy load testing tool; configure HPA; add PodDisruptionBudget
    - *Skills:* Autoscaling, resiliency

- **Project 9: RBAC & Secrets Management**
    - Create read-only developer role; secure secrets with SealedSecrets/Vault
    - *Skills:* RBAC, secrets management

---

## Phase 4 – Mastery (Weeks 10–12)
**Goal:** Production-level deployments with GitOps and service mesh.

- **Project 10: GitLab CI/CD & Helm**
    - Set up GitLab CI/CD pipelines for Kubernetes deployments; write and deploy Helm charts with templating
    - *Skills:* GitLab CI/CD, Helm syntax, chart templating

- **Project 11: GitOps Pipeline**
    - Install ArgoCD; auto-deploy manifests from GitHub
    - *Skills:* GitOps, CI/CD

- **Project 12: Service Mesh**
    - Install Istio/Linkerd; add canary deployment (traffic shifting)
    - *Skills:* Service mesh, traffic shifting

- **Project 13: Cloud Cluster**
    - Deploy on AWS EKS/GKE/AKS; enable Cluster Autoscaler; backup/restore DB & etcd
    - *Skills:* Cloud Kubernetes, node autoscaling, disaster recovery

---

## Final Capstone Project (Week 12+)
- Multi-tier microservices app
- Ingress + Service Mesh
- CI/CD with ArgoCD
- Monitoring (Prometheus, Grafana)
- Logs (EFK: Fluentbit, Elasticsearch, Kibana)
- Tracing (Jaeger)
- Security (RBAC, NetworkPolicies, Secrets)
- Autoscaling (HPA + Cluster Autoscaler)
- Cloud deployment (EKS/GKE/AKS)

---

**Next Steps:**  
Each tutorial will provide step-by-step instructions, YAML manifests, and explanations for the concepts and skills covered.