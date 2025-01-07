# Project: Operationalizing a Coworking Space Microservice

## Coworking Space Service Extension

The Coworking Space Service comprises a suite of APIs that enable users to request one-time tokens and allow administrators to manage access to coworking spaces. Following a microservice architecture, each service is designed to be deployed and managed independently.

In this project, as the DevOps engineer, you will collaborate with a team responsible for developing an API that delivers key analytics on user activity within the service. Although the application runs smoothly in a local environment, your primary task is to create a pipeline for its deployment in a Kubernetes cluster.

## Getting Started

### Dependencies

#### Local Environment
1. **Python Environment**: Required to run Python 3.6+ applications and install Python dependencies using `pip`.
2. **Docker CLI**: Essential for building and running Docker images locally.
3. **kubectl**: Necessary to execute commands against a Kubernetes cluster.
4. **helm**: Needed to apply Helm Charts to a Kubernetes cluster.

#### Remote Resources

1. **AWS CodeBuild**: Used for remote Docker image builds.
2. **AWS ECR**: Hosts Docker images.
3. **Kubernetes Environment with AWS EKS**: Deploys applications in Kubernetes.
4. **AWS CloudWatch**: Monitors activity and logs in EKS.
5. **GitHub**: Pulls and clones the code repository.


#### Project Structure
```shell
├── README.md
├── analytics
│   ├── Dockerfile
│   ├── __init__.py
│   ├── app.py
│   ├── config.py
│   ├── model.py
│   └── requirements.txt
├── buildspec.yml
├── db
│   ├── 1_create_tables.sql
│   ├── 2_seed_users.sql
│   └── 3_seed_tokens.sql
├── deploy
│   ├── configmap.yaml
│   ├── coworking.yaml
│   └── secret.yaml
└── scripts
    ├── create_cluster.sh
    ├── create_ecr.sh
    └── helm_sql.sh
```

- `scripts`: Bash scripts to facilitate project tasks.
- `db`: SQL scripts for seeding data.
- `deploy`: Kubernetes YAML files for deployment and configuration.

#### How to Run

1. Run `./scripts/cluster.sh <cluster_name> <region>`: Create a Kubernetes cluster and update `kubectl` configuration.
2. Run `./scripts/helm.sh`: Create a PostgreSQL database service.
3. To deploy application
    ```bash
    kubectl apply -f deploy/coworking.yaml
    kubectl apply -f deploy/configmap.yaml
    kubectl apply -f deploy/secret.yaml

