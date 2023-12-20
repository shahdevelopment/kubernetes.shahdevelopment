Site CI/CD & Security Evolution

Project began with a simple static HTML, CSS, & JS site originally deployed on GitHub pages. Today the site is full CI/CD, KOPS Infrastructure as Code (IaC), microservices Kubernetes (K8s) deployment in AWS cloud!

Major revisions have been categorized into three categories:

    Web Development
    Site Reliability Engineering
    DevOps Engineering / Automation

Web Development

Portfolio site notable features include:

    Downloadable PDF Resume.
    Hover-sensing dynamic GUI including: opacity control, scaling, & drop-down lists.
    A selfie project that uses your computers camera to take pictures & data storing it in a NEDB database.
    Ability to view and delete saved posts.
    A geolocation API integration with GCP Maps API.
    ChatGPT clone using the ChatGPT API.

The application is containerized in Docker runtime with separate containers for the frontend and backend. To bolster security, keys are relocated to the backend Node server (facilitating frontend API calls). Docker images are archived on Docker Hub. Code is optimized for GitHub by concealing passwords & usernames for enhanced at-rest code security.
Site Reliability Engineering

Installed and setup a Jenkins server and automated the deployment pipeline from GitHub commit to Kubernetes cluster deployment on AWS cloud; This includes a multi-stage Jenkinsfile, local SonarQube server for code testing, Docker image builds, local container execution/ testing, build notifications on Slack, & image push to Docker Hub. Passwords and usernames are securely stored in Jenkins.

The application was adapted for Kubernetes with manually crafted definition files. Infrastructure as Code (IaC) AWS backend for the Kubernetes cluster was developed using KOPS in AWS.

Code and Jenkinsfile are updated and pushed to GitHub this triggers the Jenkins build.
DevOps Engineering / Automation

CI/CD pipeline script in Jenkins pipeline script (Jenkinsfile) involves workspace cleanup, code testing in SonarQube server, GitHub Code Pull, Docker image build, container execution/ testing on Jenkins slave, JS path operation validation, image push to Docker Hub, & Kubernetes build with Helm.

The live site is optimized for costs using KOPS (IaC) deployment in AWS that enables scaling of instances to zero when not in use, & scaling instances to default levels (Creates master & slave EC2 instances & updates DNS).
Security

The code maintains parameterized variables that are pulled and parsed from the builds centralized Jenkins multi line string object/file that protects at-rest code for:

    Dockerfiles
    Jenkinsfiles (Groovy)
    Helm
    Kubernetes secrets

JS programs parameterize and secure code by pulling variable values from container envrionment variables.

Also, there is proxy security over the web with Nginx Ingress Controller (AWS ELB) http origin security, redirects, & SSL.
