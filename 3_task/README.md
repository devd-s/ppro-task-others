How It Works

    Code is pushed to the main branch (for production) or the qa branch (for QA).
    The CI/CD pipeline builds a Docker image and pushes it to a Docker registry.
    The image's SHA is dynamically injected into the environment-specific Helm values (values.yaml).
    Helm templates the Kubernetes manifests, and kubeval validates them.
    The validated manifests are applied to the appropriate Kubernetes cluster (local or QA).
    The pipeline waits until all pods are up and healthy.


GitHub Secrets set up for DockerHub credentials and Kubeconfig:

    DOCKER_USERNAME
    DOCKER_PASSWORD
    QA_KUBECONFIG
Similarly for prod can be configured if want to deploy automatically. For now to have more control , I have not added the step.