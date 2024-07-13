# NYP - IT3531: Final Year Project - Secure DevOps
*Dylan-Liew GitLab : [Link](https://gitlab.com/Dylan-Liew)*

- [NYP - IT3531: Final Year Project - Secure DevOps](#nyp---it3531-final-year-project---secure-devops)
- [Introduction](#introduction)
  - [Project Background](#project-background)
  - [DevSecOps](#devsecops)
  - [Why do we need DevSecOps](#why-do-we-need-devsecops)
  - [Continuous Integration, Continuous Delivery & Continuous Deployment (CI/CD)](#continuous-integration-continuous-delivery--continuous-deployment-cicd)
- [GitLab](#gitlab)
  - [What is GitLab & How DevOps is better with GitLab](#what-is-gitlab--how-devops-is-better-with-gitlab)
  - [Git](#git)
  - [GitLab CI/CD](#gitlab-cicd)
  - [GitLab CI/CD Concepts](#gitlab-cicd-concepts)
  - [GitLab Runner](#gitlab-runner)
  - [GitLab CI/CD Features](#gitlab-cicd-features)
  - [GitLab Security Scanning Tools](#gitlab-security-scanning-tools)
  - [GitLab Security Dashboards and Security Center](#gitlab-security-dashboards-and-security-center)
    - [Pipeline Security](#pipeline-security)
    - [Project Security Dashboard](#project-security-dashboard)
    - [Vulnerability Report](#vulnerability-report)
  - [GitLab Services](#gitlab-services)
  - [CI/CD Pipeline Artifact](#cicd-pipeline-artifact)
  - [GitLab Pricing](#gitlab-pricing)
- [Use Cases](#use-cases)
  - [Create GitLab Project](#create-gitlab-project)
  - [AndroGoat - Android Kotlin Application](#androgoat---android-kotlin-application)
    - [CI/CD Configuration - AndroGoat](#cicd-configuration---androgoat)
    - [CI/CD Build Stage - AndroGoat](#cicd-build-stage---androgoat)
      - [Build cache - AndroGoat](#build-cache---androgoat)
    - [CI/CD Test Stage - AndroGoat](#cicd-test-stage---androgoat)
      - [Debug Tests/Unit Test - AndroGoat](#debug-testsunit-test---androgoat)
      - [Code Quality Scan - AndroGoat](#code-quality-scan---androgoat)
      - [Static Application Security Test - AndroGoat](#static-application-security-test---androgoat)
      - [Secret Detection - AndroGoat](#secret-detection---androgoat)
    - [CI/CD Package Stage - AndroGoat](#cicd-package-stage---androgoat)
    - [Conclusion - AndroGoat](#conclusion---androgoat)
  - [WebGoat.NET - ASP.NET Web Application](#webgoatnet---aspnet-web-application)
    - [CI/CD Configuration - WebGoat.NET](#cicd-configuration---webgoatnet)
    - [CI/CD Build Stage - WebGoat.NET](#cicd-build-stage---webgoatnet)
    - [CI/CD Test Stage - WebGoat.NET](#cicd-test-stage---webgoatnet)
      - [Container Scanning - WebGoat.NET](#container-scanning---webgoatnet)
    - [Conclusion - WebGoat.NET](#conclusion---webgoatnet)
  - [VAmPI - Python Web API](#vampi---python-web-api)
    - [CI/CD Configuration - VAmPI](#cicd-configuration---vampi)
    - [CI/CD Build Stage - VAmPI](#cicd-build-stage---vampi)
    - [CI/CD Fuzz Stage - VAmPI](#cicd-fuzz-stage---vampi)
      - [API Fuzzing - VAmPI](#api-fuzzing---vampi)
    - [Conclusion - VAmPI](#conclusion---vampi)
  - [NodeGoat - NodeJS Web Application](#nodegoat---nodejs-web-application)
    - [CI/CD Configuration - NodeGoat](#cicd-configuration---nodegoat)
    - [CI/CD Build Stage - NodeGoat](#cicd-build-stage---nodegoat)
    - [CI/CD Test Stage - NodeGoat](#cicd-test-stage---nodegoat)
      - [Unit Testing - NodeGoat](#unit-testing---nodegoat)
      - [Code Quality - NodeGoat](#code-quality---nodegoat)
      - [Secret Detection - NodeGoat](#secret-detection---nodegoat)
      - [Container Scanning](#container-scanning)
      - [Static Application Security Testing - NodeGoat](#static-application-security-testing---nodegoat)
      - [Dependency Scanning](#dependency-scanning)
      - [License Scanning](#license-scanning)
    - [CI/CD Dast Stage - NodeGoat](#cicd-dast-stage---nodegoat)
      - [Dynamic Application Security Testing](#dynamic-application-security-testing)
    - [CI/CD Deploy Stage - NodeGoat](#cicd-deploy-stage---nodegoat)
    - [Conclusion - NodeGoat](#conclusion---nodegoat)
- [Improvements](#improvements)
- [Conclusion](#conclusion)
- [Reference](#reference)

# Introduction 
## Project Background
The objective of this project is to research and evaluate the various enterprise DevSecOps models that can be built by open source tools as well as commercial offerings by cloud service providers and software development platforms.

> **NOTE** : Before starting on the project, there is some technology that you should be familiar with such as Docker, Kubernetes, and Git technology. Some tools that you can install on your device that may help you with your project：
> - GitHub Desktop 
> - Docker Desktop 
> - Visual Studio Code 

## DevSecOps 
![DevSecOps](./img/DevSecOps.png)

DevOps is a set of practices that works to automate and integrate the processes between software development and IT teams, so they can build, test, and release software faster and more reliably.
The term DevOps was formed by combining the words “development” and “operations” and signifies a cultural shift that bridges the gap between development and operation teams, which historically functioned in siloes. 

While the DevOps culture brought a lot of innovation to software development, security was often not able to keep up with the new speed at which code was being produced and released. DevSecOps is the attempt to correct that and fully integrate security testing into the continuous integration (CI) and continuous delivery (CD) pipelines, but also build up the knowledge and skills needed in the development team so that the results of testing and the fixing can also be done internally.

DevSecOps extends the DevOps workflow to include automated security processes and tooling, giving you continuous and frictionless security testing that replaces disruptive bottlenecks at the end of the development process. This tighter integration also leads to better security outcomes, such as fewer vulnerabilities and enhanced compliance.

## Why do we need DevSecOps
    - DevOps moves at rapid pace, traditional security just can’t keep up
    - DevSecOps makes it easier to manage rapid pace of development & large scale secure deployments
    - DevSecOps allows for much smoother scaling of process

## Continuous Integration, Continuous Delivery & Continuous Deployment (CI/CD)

CI/CD is a method to frequently deliver apps to customers by introducing automation into the stages of app development. The main concepts attributed to CI/CD are continuous integration, continuous delivery, and continuous deployment. CI/CD is a solution to the problems integrating new code can cause for development and operations teams (AKA "integration hell").

In modern application development, the goal is to have multiple developers working simultaneously on different features of the same app. However, if an organization is set up to merge all branching source code together on one day (known as “merge day”), the resulting work can be tedious, manual, and time-intensive. That’s because when a developer working in isolation makes a change to an application, there’s a chance it will conflict with different changes being simultaneously made by other developers. This problem can be further compounded if each developer has customized their own local integrated development environment (IDE), rather than the team agreeing on one cloud-based IDE.

Continuous Integration works by pushing small code chunks to your application’s codebase hosted in a Git repository, and to every push, run a pipeline of scripts to build, test, and validate the code changes before merging them into the main branch.

Continuous Delivery and Deployment consist of a step further CI, deploying your application to production at every push to the default branch of the repository.

These methodologies allow you to catch bugs and errors early in the development cycle, ensuring that all the code deployed to production complies with the code standards you established for your app.

# GitLab
Version : **13.12**

## What is GitLab & How DevOps is better with GitLab
GitLab is a complete DevOps platform, delivered as a single application that does everything from project planning and source code management to CI/CD, monitoring, and security. The advantages of a single application are listed in the following paragraphs. This makes GitLab unique and creates a streamlined software workflow, unlocking your organization from the constraints of a pieced together toolchain. GitLab is also the first single application platform that unifies
the DevSecOps toolchain for improved quality, security and developer productivity. 

Other vendors offer a kit plane you have to assemble yourself, GitLab is a type certified aircraft.
![Toolchain](./img/Toolchain.PNG)

[**Manage**](https://about.gitlab.com/stages-devops-lifecycle/manage/)

GitLab helps teams manage and optimize their software delivery lifecycle with metrics and value stream insight in order to streamline and increase their delivery velocity. Learn more about how GitLab helps to manage your end to end value stream.

[**Plan**](https://about.gitlab.com/stages-devops-lifecycle/plan/)

GitLab enables portfolio planning and management through epics, groups (programs) and milestones to organize and track progress. Regardless of your methodology from Waterfall to DevOps, GitLab’s simple and flexible approach to planning meets the needs of small teams to large enterprises. GitLab helps teams organize, plan, align and track project work to ensure teams are working on the right things at the right time and maintain end to end visibility and traceability of issues throughout the delivery lifecycle from idea to production.

[**Create**](https://about.gitlab.com/stages-devops-lifecycle/create/)

GitLab helps teams design, develop and securely manage code and project data from a single distributed version control system to enable rapid iteration and delivery of business value. GitLab repositories provide a scalable, single source of truth for collaborating on projects and code which enables teams to be productive without disrupting their workflows.

[**Verify**](https://about.gitlab.com/stages-devops-lifecycle/verify/)

GitLab helps delivery teams fully embrace continuous integration to automate the builds, integration and verification of their code. GitLab’s industry leading CI capabilities enables automated testing, Static Analysis Security Testing, Dynamic Analysis Security testing and code quality analysis to provide fast feedback to developers and testers about the quality of their code. With 
s that enable concurrent testing and parallel execution, teams quickly get insight about every commit, allowing them to deliver higher quality code faster.

[**Package**](https://about.gitlab.com/stages-devops-lifecycle/package/)

GitLab enables teams to package their applications and dependencies, manage containers, and build artifacts with ease. The private, secure, container and package registry are built-in and preconfigured out-of-the box to work seamlessly with GitLab source code management and CI/CD pipelines. Ensure DevOps acceleration and a faster time to market with automated software pipelines that flow freely without interruption.

[**Secure**](https://about.gitlab.com/stages-devops-lifecycle/secure/)

GitLab provides Static Application Security Testing (SAST), Dynamic Application Security Testing (DAST), Container Scanning, and Dependency Scanning to help you deliver secure applications along with license compliance.

[**Release**](https://about.gitlab.com/stages-devops-lifecycle/release/)

GitLab helps automate the release and delivery of applications, shortening the delivery lifecycle, streamlining manual processes, and accelerating team velocity. With zero-touch Continuous Delivery (CD) built right into the pipeline, deployments can be automated to multiple environments like staging and production, and the system just knows what to do without being told - even for more advanced patterns like canary deployments. With feature flags, built-in auditing/traceability, on-demand environments, and GitLab pages for static content delivery, you'll be able to deliver faster and with more confidence than ever before.

[**Configure**](https://about.gitlab.com/stages-devops-lifecycle/configure/)

GitLab helps teams to configure and manage their application environments. Strong integration to Kubernetes reduces the effort needed to define and configure the infrastructure required to support your application. Protect access to key infrastructure configuration details such as passwords and login information by using ‘secret variables’ to limit access to only authorized users and processes.

[**Monitor**](https://about.gitlab.com/stages-devops-lifecycle/monitor/)

Get feedback and the tools to help you reduce the severity and frequency of incidents so that you can release software frequently with confidence.

[**Protect**](https://about.gitlab.com/stages-devops-lifecycle/protect/)

GitLab provides cloud native protections, including unified policy management, container scanning, and container network and host security.

## Git
GitLab is a Git-based fully integrated platform for software development. Besides Git’s functionalities, GitLab has a lot of powerful features to enhance your workflow.

Git is a free, open source and most commonly used Distributed Version Control System designed to handle everything from small to large projects with speed and efficiency. It keeps a record of every change in a project by taking snapshots. It means that you can easily roll back to any previous version/state of a project.

## GitLab CI/CD
GitLab CI/CD is a tool built into GitLab for software development through the continuous methodologies:

- Continuous Integration (CI)
- Continuous Delivery (CD)
- Continuous Deployment (CD)

To use GitLab CI/CD, you need:
   - Ensure you have runners available to run your jobs. If you don’t have a runner, install GitLab Runner and register a runner for your instance, project, or group.
   - Application code hosted in a Git repository.
   - A file called ```.gitlab-ci.yml``` in the root of your repository, which contains the CI/CD configuration.
> **NOTE :** .yml file also known as YAML (a recursive acronym for "YAML Ain't Markup Language") is a human-readable data-serialization language. It is commonly used for configuration files and in applications where data is being stored or transmitted.

GitLab CI/CD is configured by ```.gitlab-ci.yml``` file placed at the repository’s root. This file creates a pipeline, which runs for changes to the code in the repository. Pipelines consist of one or more stages that run in order and can each contain one or more jobs that run in parallel. These jobs (or scripts) get executed by the GitLab Runner agent.

In the ```.gitlab-ci.yml``` file, you can define:

    - The scripts you want to run.
    - Other configuration files and templates you want to include.
    - Dependencies and caches.
    - The commands you want to run in sequence and those you want to run in parallel.
    - The location to deploy your application to.
    - Whether you want to run the scripts automatically or trigger any of them manually.

The scripts are grouped into jobs, and jobs run as part of a larger pipeline. You can group multiple independent jobs into stages that run in a defined order. The CI/CD configuration needs at least one job that is not hidden.

You should organize your jobs in a sequence that suits your application and is in accordance with the tests you wish to perform. To visualize the process, imagine the scripts you add to jobs are the same as CLI commands you run on your computer.

When you add a ```.gitlab-ci.yml``` file to your repository, GitLab detects it and an application called GitLab Runner runs the scripts defined in the jobs.

> **NOTE** : By default, the GitLab CI/CD executor pulls images from Docker Hub to perform the necessary task. You can also include links to the image. For more information about images and Docker Hub, see the [**Docker Fundamentals**](https://docs.docker.com/engine/understanding-docker/) documentation.

A job is defined as a list of keywords that define the job’s behavior.

The keywords available for jobs are:
| Keyword        | Description                                                                                                 |
|----------------|-------------------------------------------------------------------------------------------------------------|
| ```after_script```   | Override a set of commands that are executed after job.                                                     |
| ```allow_failure```  | Allow job to fail. A failed job does not cause the pipeline to fail.                                        |
| ```artifacts```      | List of files and directories to attach to a job on success.                                                |
| ```before_script```  | Override a set of commands that are executed before job.                                                    |
| ```cache```          | List of files that should be cached between subsequent runs.                                                |
| ```coverage```       | Code coverage settings for a given job.                                                                     |
| ```dependencies```   | Restrict which artifacts are passed to a specific job by providing a list of jobs to fetch artifacts from.  |
| ```environment```    | Name of an environment to which the job deploys.                                                            |
| ```except```         | Limit when jobs are not created.                                                                            |
| ```extends```        | Configuration entries that this job inherits from.                                                          |
| ```image```          | Use Docker images.                                                                                          |
| ```include```        | Include external YAML files.                                                                                |
| ```inherit```        | Select which global defaults all jobs inherit.                                                              |
| ```interruptible```  | Defines if a job can be canceled when made redundant by a newer run.                                        |
| ```needs```          | Execute jobs earlier than the stage ordering.                                                               |
| ```only```           | Limit when jobs are created.                                                                                |
| ```pages```          | Upload the result of a job to use with GitLab Pages.                                                        |
| ```parallel```       | How many instances of a job should be run in parallel.                                                      |
| ```release```        | Instructs the runner to generate a release object.                                                          |
| ```resource_group``` | Limit job concurrency.                                                                                      |
| ```retry```          | When and how many times a job can be auto-retried in case of a failure.                                     |
| ```rules```          | List of conditions to evaluate and determine selected attributes of a job, and whether or not it’s created. |
| ```script```         | Shell script that is executed by a runner.                                                                  |
| ```secrets```        | The CI/CD secrets the job needs.                                                                            |
| ```services```       | Use Docker services images.                                                                                 |
| ```stage```          | Defines a job stage.                                                                                        |
| ```tags```           | List of tags that are used to select a runner.                                                              |
| ```timeout```        | Define a custom job-level timeout that takes precedence over the project-wide setting.                      |
| ```trigger```        | Defines a downstream pipeline trigger.                                                                      |
| ```variables```      | Define job variables on a job level.                                                                        |
| ```when```           | When to run job                                                                                             |

## GitLab CI/CD Concepts
GitLab CI/CD uses a number of concepts to describe and run your build and deploy.
| Concept | Description |
|-|-|
| Pipelines | Structure your CI/CD process through pipelines. |
| CI/CD variables | Reuse values based on a variable/value key pair. |
| Environments | Deploy your application to different environments (e.g., staging, production). |
| Job artifacts | Output, use, and reuse job artifacts. |
| Cache dependencies | Cache your dependencies for a faster execution. |
| GitLab Runner | Configure your own runners to execute your scripts. |
| Pipeline efficiency | Configure your pipelines to run quickly and efficiently. |
| Test cases | Configure your pipelines to run quickly and efficiently. |

## GitLab Runner
To use Gitlab CI/CD, you need to ensure you have runners available. GitLab Runner is an application that works with GitLab CI/CD to run jobs in a pipeline.

    You might already have runners available for your project, including shared runners, which are available to all projects in your GitLab instance.

    To view available runners:

    - Go to Settings > CI/CD and expand Runners.
  
    As long as you have at least one runner that’s active, with a green circle next to it, you have a runner available to process your jobs.

If no runners are listed on the Runners page in the UI, you or an administrator must install GitLab Runner and register at least one runner by following the guide below. 

  Runner Installation Guide : [**Link**](https://docs.gitlab.com/runner/install/)

  Runner Registration Guide : [**Link**](https://docs.gitlab.com/runner/register/index.html)

You can install GitLab Runner on several different supported operating systems. Other operating systems may also work, as long as you can compile a Go binary on them. GitLab Runner can also run inside a Docker container or be deployed into a Kubernetes cluster.

In the GitLab UI there are three types of runners, based on who you want to have access:

    - Shared runners are available to all groups and projects in a GitLab instance.
    - Group runners are available to all projects and subgroups in a group.
    - Specific runners are associated with specific projects. Typically, specific runners are used for one project at a time.

Shared runners are available to every project in a GitLab instance. These runners are shared across this GitLab instance.

Shared Runners on ```GitLab.com``` run in auto-scale mode and are powered by Google Cloud Platform. Auto-scaling means reduced wait times to spin up builds, and isolated VMs for each project, thus maximizing security.

They're free to use for public open source projects and limited to 2000 CI minutes per month per group for private projects. 

## GitLab CI/CD Features
Use the vast GitLab CI/CD to easily configure it for specific purposes. Its feature set is listed on the table below according to DevOps stages. 

| Feature                                | Description                                                                                                                    |
|----------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| **Configure**                              |                                                                                                                                |
| Auto DevOps                            | Set up your app’s entire lifecycle.                                                                                            |
| ChatOps                                | Trigger CI jobs from chat, with results sent back to the channel.                                                              |
| Browser Performance Testing            | Quickly determine the browser performance impact of pending code changes.                                                      |
| Load Performance Testing               | Quickly determine the server performance impact of pending code changes.                                                       |
| CI services                            | Link Docker containers with your base image.                                                                                   |
| Code Quality                           | Analyze your source code quality.                                                                                              |
| GitLab CI/CD for external repositories | Get the benefits of GitLab CI/CD combined with repositories in GitHub and Bitbucket Cloud.                                     |
| Interactive Web Terminals              | Open an interactive web terminal to debug the running jobs.                                                                    |
| Unit test reports                      | Identify script failures directly on merge requests.                                                                           |
| Using Docker images                    | Use GitLab and GitLab Runner with Docker to build and test applications.                                                       |
| **Release**                                |                                                                                                                                |
| Auto Deploy                            | Deploy your application to a production environment in a Kubernetes cluster.                                                   |
| Building Docker images                 | Maintain Docker-based projects using GitLab CI/CD.                                                                             |
| Canary Deployments                     | Ship features to only a portion of your pods and let a percentage of your user base to visit the temporarily deployed feature. |
| Deploy Boards                          | Check the current health and status of each CI/CD environment running on Kubernetes.                                           |
| Feature Flags                          | Deploy your features behind Feature Flags.                                                                                     |
| GitLab Pages                           | Deploy static websites.                                                                                                        |
| GitLab Releases                        | Add release notes to Git tags.                                                                                                 |
| Review Apps                            | Configure GitLab CI/CD to preview code changes.                                                                                |
| Cloud deployment                       | Deploy your application to a main cloud provider.                                                                              |
| **Secure**                                 |                                                                                                                                |
| Container Scanning                     | Check your Docker containers for known vulnerabilities.                                                                        |
| Dependency Scanning                    | Analyze your dependencies for known vulnerabilities.                                                                           |
| License Compliance                     | Search your project dependencies for their licenses.                                                                           |
| Security Test reports                  | Check for app vulnerabilities.                                                                                                 |

## GitLab Security Scanning Tools
GitLab uses the following tools to scan and report known vulnerabilities found in your project. 

For more information, please visit [**HERE**](https://docs.gitlab.com/ee/user/application_security/index.html#security-scanning-tools).
| Secure Scanning Tool                         | Description                                                         |
|----------------------------------------------|---------------------------------------------------------------------|
| Container Scanning                           | Scan Docker containers for known vulnerabilities.                   |
| Dependency List                              | View your project’s dependencies and their known vulnerabilities.   |
| Dependency Scanning                          | Analyze your dependencies for known vulnerabilities.                |
| Dynamic Application Security Testing (DAST)  | Analyze running web applications for known vulnerabilities.         |
| API fuzzing                                  | Find unknown bugs and vulnerabilities in web APIs with fuzzing.     |
| Secret Detection                             | Analyze Git history for leaked secrets.                             |
| Security Dashboard                           | View vulnerabilities in all your projects and groups.               |
| Static Application Security Testing (SAST)   | Analyze source code for known vulnerabilities.                      |
| Coverage fuzzing                             | Find unknown bugs and vulnerabilities with coverage-guided fuzzing. |
<br>

## GitLab Security Dashboards and Security Center
Once we configure any one of the security scanner, we will be able to view the vulnerabilities found using GitLab. GitLab provides a comprehensive set of features for viewing and managing vulnerabilities:

- Security dashboards: An overview of the security status in your personal Security Center, groups, and projects.
- Vulnerability reports: Detailed lists of all vulnerabilities for the Security Center, group, project, or pipeline. This is where you triage and manage vulnerabilities.
- Security Center: A dedicated area for personalized vulnerability management. This includes a security dashboard, vulnerability report, and settings.

### Pipeline Security 
At the pipeline level, the Security section displays the vulnerabilities present in the branch of the project the pipeline ran against.
A pipeline consists of multiple jobs, including SAST and DAST scanning. If any job fails to finish for any reason, the security dashboard doesn’t show SAST scanner output. For example, if the SAST job finishes but the DAST job fails, the security dashboard doesn’t show SAST results. On failure, the analyzer outputs an exit code.

### Project Security Dashboard
A project’s Security Dashboard displays a chart with the total number of vulnerabilities over time. It updates daily with up to 365 days of historical data. By default, it shows statistics for all vulnerability severities.

To access the dashboard, from your project’s home page go to Security & Compliance > Security Dashboard.

### Vulnerability Report
The Vulnerability Report provides information about vulnerabilities from scans of the branch most recently merged into the default branch. It is available for groups, projects, and the Security Center.

At all levels, the Vulnerability Report contains:

- Totals of vulnerabilities per severity level.
- Filters for common vulnerability attributes.
- Details of each vulnerability, presented in tabular layout.

## GitLab Services
The ```services``` keyword defines a Docker image that runs during a ```job``` linked to the Docker image that the image keyword defines. This allows you to access the service image during build time.

The service image can run any application, but the most common use case is to run a database container, for example:

- MySQL
- PostgreSQL
- Redis

It’s easier and faster to use an existing image and run it as an additional container than to install ```mysql```, for example, every time the project is built.

You’re not limited to only database services. You can add as many services you need to ```.gitlab-ci.yml```. Any image found at Docker Hub or your private Container Registry can be used as a service.

Services inherit the same DNS servers, search domains, and additional hosts as the CI container itself.

Click [**HERE**](https://docs.gitlab.com/ee/ci/services/) for more information.
## CI/CD Pipeline Artifact
Jobs can output an archive of files and directories. This output is known as a job artifact. 

You can download job artifacts by using the [**API**](https://docs.gitlab.com/ee/api/job_artifacts.html#get-job-artifacts) or  the GitLab UI:

- On the Pipelines page, to the right of the pipeline

- On the Jobs page, to the right of the job

- On a job’s detail page. The Keep button indicates an expire_in value was set

- On a merge request, by the pipeline details

- When browsing an archive

## GitLab Pricing
GitLab comes with three different plans: 
- Free
- Premium
- Ultimate 

For more details, click [**HERE**](https://about.gitlab.com/pricing/) for GitLab Pricing.

# Use Cases
Each use case is used to demonstrate different DevSecOps features and workflow by using the security features from GitLab.

| Project | Feature | Pipeline Stages |
|-|-|-|
| [AndroGoat](#androgoat---android-kotlin-application) | Code Quality Scan<br>Static Application Security Testing (SAST)<br>Secret Detection | Build<br>Test<br>Package |
| [WebGoat.NET](#webgoat.net---asp.net-web-application) | Container Security | Build (Deploy to Container Registry)<br>Test |
| [VAmPI](#vampi---python-web-api) | API Fuzzing | Build (Deploy to Container Registry<br>Test |
| [NodeGoat](#nodegoat---nodejs-web-application) | Code Quality Scan<br>Static Application Security Testing (SAST)<br>Secret Detection<br>Container Scanning<br>Dependency Scanning<br>License Scanning<br>Dynamic Application Security Testing | Build (Deploy to Container Registry)<br>Test<br>DAST<br>Deploy (Azure Kubernetes Service) |

**GitLab Repository Links**
- [AndroGoat Use Case](https://gitlab.com/Dylan-Liew/androgoat_devsecops)
- [NodeGoat Use Case](https://gitlab.com/Dylan-Liew/nodegoat_devsecops)
- [VAmPI Use Case](https://gitlab.com/Dylan-Liew/vampi_devsecops)
- [WebGoat.NET Use Case](https://gitlab.com/Dylan-Liew/webgoat.net_devsecops)
## Create GitLab Project
1. Before configuring the CI/CD pipeline, we need to create a project.
2. Go to [GitLab Website](https://gitlab.com/users/sign_in) and sign in / register if you don't have an account. 
   
    ![GitLab Sign In](./img/Sign-In.PNG)
3. To start with DevOps on your project, you need a repository. Click the **New Project** Button at top right corner. Then, select the choice based on your needs from the following:
  
         - Create Blank Project
         - Create from template
         - Import Project
         - Run CI/CD for external repository 
  
    ![GitLab Projects](./img/Create-New-Project.PNG)
4. Where in our case, we just need to create a blank project. Once the project is created, you can start on your project directly from GitLab IDE / GitPod or upload your files **one by one** or you can refer to the **NOTE** below.
   
    So in our case, we will just download the project files from Github and clone our newly created repository using git client of your choice, add the files to the local repository and then push back to the remote repository.

    ![Repo](./img/Repo.PNG)

> **NOTE** : To upload multiple files on your GitLab repository, you will need to download an external git client like Source Tree, GitKraken, and GitHub Desktop, connect to your GitLab account, clone the repository to your PC, add your files to the local repository, then push back to the remote repository. 

## AndroGoat - Android Kotlin Application
*GitHub Repository: [Link](https://github.com/satishpatnayak/AndroGoat)*

AndroGoat is purposely developed open source vulnerable/insecure app using Kotlin. Security Testers/Professionals/Enthusiasts, Developers…etc. can use this application to understand and defend the vulnerabilities in Android platform. This is the first vulnerable app developed using Kotlin. This application also listed as reference in [OWASP Mobile Security Testing Guidelines](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x08-Testing-Tools.md#android).

### CI/CD Configuration - AndroGoat
1. To start on CI/CD configuration, you can simply click the ```Set Up CI/CD``` button in the UI under Project overview -> Details, then it will navigate to CI/CD editor click on ```Create new CI/CD pipeline``` and it will create a ```.gitlab-ci.yml``` file which is used for CI/CD pipeline configuration.
   ![CI/CD](./img/Set-Up.PNG)
   ![CI/CD](./img/CICD.PNG)

   Once created, you can directly edit using the editor provider. If you don't know how to start, you can look at some of these [templates](https://docs.gitlab.com/ee/ci/examples/README.html#cicd-templates) provided by GitLab.

2. Let's go straight into the configuration. There are three stages in our CI/CD pipeline :
   
        stages:
        - build
        - test
        - package
   
   - ```build``` stage ensures the app compiles
   - ```test``` stage runs our tests such as unit tests, security tests, etc.
   - ```package``` package the android application into APK.

3. Based on the ```build.gradle``` file found it states that the compile SDK version is 26. Hence, I can simply use this [**Docker Image**](https://hub.docker.com/r/androidsdk/android-26) from DockerHub that have the build tools preinstalled which will be used for build job or other job.

    To use the image, just include ```image: androidsdk/android-26``` in the ```.gitlab-ci.yml``` under ```default:```.
    
    You can set global defaults for some keywords. Jobs that do not define one or more of the listed keywords use the value defined in the ```default:``` section.

    These job keywords can be defined inside a ```default:``` section:

        - after_script
        - artifacts
        - before_script
        - cache
        - image
        - interruptible
        - retry
        - services
        - tags
        - timeout
  
    ![SDK 26](./img/26.PNG)

4. Once we planned the stages and decide image to be used for most of the jobs, we can start configuring each stage to include the necessary jobs.

    CI/CD Pipeline:
    | Build          | Test              | Package |
    |----------------|-------------------|---------|
    | assemble debug | code quality scan | package |
    | lint debug     | debug tests       |         |
    |                | mobsf sast        |         |
    |                | secret detection  |         |

### CI/CD Build Stage - AndroGoat
Under the build stage, there are two jobs under build stage :
- ```Assemble debug``` : Build a debug apk for Immediate app build testing and debugging. The debug APK is signed with a debug key provided by the SDK tools and allows debugging through adb. The debug is cached for packaging later.
  
- ```Lint debug``` : The lint tool checks your Android project source files for potential bugs and optimization improvements for correctness, security, performance, usability, accessibility, and internationalization.

      assembleDebug:
        stage: build
        script:
          - ./gradlew assembleDebug
        cache:
          key: "$CI_JOB_NAME"
          paths:
            - .gradle/wrapper
            - .gradle/caches
            - app/build/outputs/
        artifacts:
          paths:
          - app/build/outputs/

      lintDebug:
        stage: build
        script:
          - ./gradlew -Pci --console=plain lintDebug -PbuildDir=lint
        artifacts: 
          paths:
            - app/lint/reports/lint-results-debug.xml

#### Build cache - AndroGoat
Most of the jobs defined in the pipeline require at least a JVM (for running gradle) or even parts of the Android SDK. The recommended way to run gradle is via the gradle wrapper. The gradle wrapper ensures that the requested version of gradle is used and downloads it, if required. As we are running the jobs in a docker container, gradle would be downloaded each time, a job requires it, which is very time-lasting and inefficient.

For this cases, GitLab provides the option to cache the contents specified directories between jobs. Once a job has been finished the contents of the specified folders are zipped. When the build executes the next time, the cache files are unzipped prior running the job. 

It is possible to define a cache-key per job to control the cache sharing. The job name can be used as cache key, which results in separate caches for each job, meaning that the same jobs shared its cache with subsequent/previous runs of the job.

The following added to ```.gitlab-ci.yml``` enables caching of the gradle files on a per-job basis:

      cache:
        key: "$CI_JOB_NAME"
        paths:
          - .gradle/wrapper
          - .gradle/caches
          - app/build/outputs/
    
### CI/CD Test Stage - AndroGoat
Under the test stage, there are four jobs:
#### Debug Tests/Unit Test - AndroGoat
This job runs the unit tests which are the fundamental tests in your app testing strategy, from which you can verify that the logic of individual units is correct. They are a fantastic way to catch regressions when making changes to your app. 
- To configure this test, you just need to include this in your CI configuration:

      debugTests:
        stage: test
        script:
          - ./gradlew -Pci --console=plain testDebug
  
#### Code Quality Scan - AndroGoat
Ensuring your project’s code stays simple, readable and easy to contribute to can be problematic. With the help of GitLab CI/CD, you can analyze your source code quality using GitLab Code Quality.
- Uses Engines supported by Code Climate, which are free and open source. Code Quality does not require a Code Climate subscription.
- Runs in pipelines using a Docker image built in the GitLab Code Quality project using default Code Climate configurations.
- To enable code quality scan, you simply include the Code Quality template in your CI configuration:

      include:
        - template: Code-Quality.gitlab-ci.yml

- By default, report artifacts are not downloadable. it is possible to generate an HTML report file by setting the REPORT_FORMAT CI/CD variable to html. This is useful if you just want to view the report in a more human-readable format or to publish this artifact on GitLab Pages for even easier reviewing.

      code_quality:
        variables:
          REPORT_FORMAT: html
        artifacts:
          paths: [gl-code-quality-report.html]

- The included ```code_quality``` job is running in the ```test``` stage, so it needs to be included in your CI configuration, like so:

      stages:
        - test

- For more information, you can look at the [**Official Documentation**](https://docs.gitlab.com/ee/user/project/merge_requests/code_quality.html).

#### Static Application Security Test - AndroGoat
If you’re using GitLab CI/CD, you can analyze your source code for known vulnerabilities using Static Application Security Testing (SAST). GitLab checks the SAST report and compares the found vulnerabilities between the source and target branches.
- To run SAST jobs, by default, you need GitLab Runner with the docker or Kubernetes executor. If you’re using the shared runners on GitLab, this is enabled by default. Our SAST jobs require a Linux container type. Windows containers are not yet supported.

- GitLab SAST supports a variety of languages, package managers, and frameworks. For the supported language and framworks, you can refer [**HERE**](https://docs.gitlab.com/ee/user/application_security/sast/#supported-languages-and-frameworks).
- GitLab's SAST security scanners also feature automatic language detection which works even for mixed-language projects. If any supported language is detected in project source code GitLab automatically run the appropriate SAST analyzers. 

- Since our use case is Kotlin (Android) Application, GitLab will be using [MobSF](https://github.com/MobSF/Mobile-Security-Framework-MobSF) to perform our security test.

- To enable GitLab SAST Feature, just include the SAST template in your CI configuration, 
  
      include:
        - template: Security/SAST.gitlab-ci.yml

- However, scanning of iOS and Android apps using the MobSF analyzer is still in beta which is one of the experimental features that might be added, removed, or promoted to regular features at any time. 

- To enable MobSF scanning for our android application, you will just need to include this in the configuration yml file: 

      include:
        - template: Security/SAST.gitlab-ci.yml

      variables:
        SAST_EXPERIMENTAL_FEATURES: "true"

- For more information, you can read the [**Official Documentation**](https://docs.gitlab.com/ee/user/application_security/sast/).

#### Secret Detection - AndroGoat
A recurring problem when developing applications is that developers may unintentionally commit secrets and credentials to their remote repositories. If other people have access to the source, or if the project is public, the sensitive information is then exposed and can be leveraged by malicious users to gain access to resources like deployment environments.

- GitLab 11.9 includes a new check called Secret Detection. It scans the content of the repository to find API keys and other information that should not be there.

- Secret Detection detects a variety of common secrets by default. You can also customize the secret detection patterns using custom rulesets.

- The default ruleset provided by Gitleaks includes the following key types:
  - Cloud services:
    - Amazon Web Services (AWS)
    - Google Cloud Platform (GCP)
    - Heroku API
  - Encryption keys:
    - PKCS8
    - RSA
    - SSH
    - PGP
    - DSA
    - EC
  - Social media platforms:
    - Facebook API
    - Twitter API
    - Cloud SaaS vendors:
    - GitHub API
    - Shopify API
    - Slack Token
    - Slack Webhook
    - Stripe API
    - Twilio API
    - Generic API key strings starting with ```api-```
  - Password in URL
  - U.S. Social Security Number
- To enable secret detection, simply add the following to your ```.gitlab-ci.yml``` file:

      include:
        - template: Security/Secret-Detection.gitlab-ci.yml

- To perform a single or recurring scan of the full history of your repository for secrets. You will need to add the following to your configuration:

      secret_detection:
        variables:
          SECRET_DETECTION_HISTORIC_SCAN: "true"

- For more information, you can refer to the [**Official Documentation**](https://docs.gitlab.com/ee/user/application_security/secret_detection/).

- To test out the secret detection, some sample secrets are added to the source code under ```app/src/androidTest/java/owasp/sat/agoat/ExampleInstrumentedTest.kt```

### CI/CD Package Stage - AndroGoat
The package job is simply giving the debug apk a proper name and putting it in a separate folder which was cached from assemble debug job. Then, You can download this apk through job artifacts by using the GitLab UI or the API. 

- CI configuration for the package job :

      package:
        stage: package
        dependencies: 
          - assembleDebug
        script:
          - mv app/build/outputs/apk/debug/app-debug.apk ./AndroGoat-debug.apk
        artifacts:
          paths:
          - AndroGoat-debug.apk

### Conclusion - AndroGoat
Once the CI/CD is configured, the pipeline will runs whenever there is a new change in source code/merge request in the project. The configuration and pipeline are shown below:

Final ```.gitlab-ci.yml``` configuration:

    include:
      - template: Security/SAST.gitlab-ci.yml
      - template: Security/Secret-Detection.gitlab-ci.yml
      - template: Code-Quality.gitlab-ci.yml

    variables:
      SAST_EXPERIMENTAL_FEATURES: "true"

    stages:
      - build
      - test
      - package

    default:
      image: androidsdk/android-26
      before_script:
        - chmod +x ./gradlew

    assembleDebug:
      stage: build
      script:
        - ./gradlew assembleDebug
      cache:
        key: "$CI_JOB_NAME"
        paths:
          - .gradle/wrapper
          - .gradle/caches
          - app/build/outputs/
      artifacts:
        paths:
        - app/build/outputs/

    lintDebug:
      stage: build
      script:
        - ./gradlew -Pci --console=plain lintDebug -PbuildDir=lint
      artifacts: 
        paths:
          - app/lint/reports/lint-results-debug.xml

    debugTests:
      stage: test
      script:
        - ./gradlew -Pci --console=plain testDebug

    secret_detection:
      variables:
        SECRET_DETECTION_HISTORIC_SCAN: "true"

    package:
      stage: package
      dependencies: 
        - assembleDebug
      script:
        - mv app/build/outputs/apk/debug/app-debug.apk ./AndroGoat-debug.apk
      artifacts:
        paths:
        - AndroGoat-debug.apk

## WebGoat.NET - ASP.NET Web Application
*GitHub Repository: [Link](https://github.com/jerryhoff/WebGoat.NET)*

This web application is a learning platform that attempts to teach about
common web security flaws. It contains generic security flaws that apply to
most web applications. It also contains lessons that specifically pertain to the .NET framework. 

### CI/CD Configuration - WebGoat.NET
1. Ensure you have read the [GitLab CI/CD](#gitlab-cicd) before starting with the CI/CD configuration. To start on CI/CD configuration, you can simply click the ```Set Up CI/CD``` button in the UI under Project overview > Details, then it will navigate to CI/CD editor click on ```Create new CI/CD pipeline``` and it will create a ```.gitlab-ci.yml``` file which is used for CI/CD pipeline configuration.
   ![CI/CD](./img/Set-Up.PNG)
   ![CI/CD](./img/CICD.PNG)

   Once created, you can directly edit using the editor provider. If you don't know how to start, you can look at some of these [templates](https://docs.gitlab.com/ee/ci/examples/README.html#cicd-templates) provided by GitLab.

2. Let's go straight into the configuration. There are two stages in our CI/CD pipeline :
   
        stages:
        - build
        - test
   
   - ```build``` stage build the container image and deploy to container registry
   - ```test``` stage runs our tests

3. Once we planned the stages, we can start configuring each stage to include the neccessary jobs. 
   
   Since we are using this project to demonstrate container scanning, it only contains the minimal jobs to perform container scanning however you can add in your own test.

    CI/CD Pipeline:
    | Build          | Test              |
    |----------------|-------------------|
    | Build and Deploy to container registry | container scanning |
    <br>
### CI/CD Build Stage - WebGoat.NET
Under the build stage, there is only one job under build stage :

- ```Build and Deploy to container registry``` : builds Docker images from a Dockerfile and deploy to GitLab Container Registry

> **NOTE** : Dockerfile is not provided by the Github Repository, so I download dockerfile from ```https://github.com/appsecco/owasp-webgoat-dot-net-docker/blob/master/Dockerfile```. However, the dockerfile was not well written as the command that run the application which stopped immediately after it runs which will cause the deployment to not work hence I added a ```--nonstop``` to the ```CMD[ "xsp4", "--printlog" ]``` to ```CMD [ "xsp4", "--printlog" ,"--nonstop"]```

The script below login to the container registry then build, tag and push the container image to gitlab container registry.

When running ```docker build```, each command in ```Dockerfile``` results in a layer. These layers are kept around as a cache and can be reused if there haven’t been any changes. Change in one layer causes all subsequent layers to be recreated.

You can specify a tagged image to be used as a cache source for the ```docker build``` command by using the --cache-from argument. Multiple images can be specified as a cache source by using multiple ```--cache-from``` arguments. Any image that’s used with the ```--cache-from``` argument must first be pulled (using ```docker pull```) before it can be used as a cache source.

      build_and_deploy_container_image:
        services:
        - name: docker:dind
          alias: dind
        image: docker:19.03.5
        stage: build
        before_script:
          - docker login -u gitlab-ci-token -p $CI_JOB_TOKEN $CI_REGISTRY
        script:
          - docker pull $CI_REGISTRY_IMAGE:latest || true
          - docker build --cache-from $CI_REGISTRY_IMAGE:latest --tag $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA --tag $CI_REGISTRY_IMAGE:latest .
          - docker push $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
          - docker push $CI_REGISTRY_IMAGE:latest
        after_script:
          - docker logout registry.gitlab.com
  
> **NOTE**: A container registry is a repository, or collection of repositories, used to store container images for Kubernetes deployment and container-based application development. 

### CI/CD Test Stage - WebGoat.NET
Under the test stage, there is only one job:
#### Container Scanning - WebGoat.NET
Container scanning scans your application docker image for known vulnerabilities.

The common vulnerability that can be found in a container image can be from 
- OS Packages/libraries: ssh (secure shell)
- Dependencies of software you develop yourself
- Every other component installed in the image: tomcat, mongodb or postgres

To configure this test, you just need to include this in your CI configuration:

      include:
        - template: Container-Scanning.gitlab-ci.yml

> However, GitLab 14.0 will replace its container scanning engine with Trivy. Currently, GitLab uses the open source Clair engine for container scanning. GitLab 13.9 deprecates Clair. Until GitLab 14.0, this is not a hard breaking change. Beginning in GitLab 14.0, GitLab will no longer update or maintain Clair. To ensure that you get regular updates and the latest features, you must use the Trivy container scanning engine beginning in GitLab 14.0. See the following sections for instructions on moving from Clair to Trivy.

As I am currently using Clair and want to migrate to Trivy before GitLab 14.0, I did the following steps:

- Set the variable ```CS_MAJOR_VERSION``` to 4. The job scope is global variables, or under ```.cs_common```.
- Remove the variable ```CS_PROJECT``` from your CI file. The job scope is container_scanning_new. Setting this variable to container-scanning under the correct scope has the same effect as removing it from your CI file.
- Remove any variables that are only applicable to Clair. For a complete list of these variables, see the available variables.

      variables:
        CS_MAJOR_VERSION: "4"
        GIT_STRATEGY: fetch
        DOCKER_IMAGE: $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
  
### Conclusion - WebGoat.NET
Once the CI/CD is configured, the pipeline will runs whenever there is a new change in source code/merge request in the project. The configuration and the pipeline is shown below:

Final ```.gitlab-ci.yml``` configuration:

    include:
      - template: Container-Scanning.gitlab-ci.yml

    stages: 
      - build
      - test

    variables:
      CS_MAJOR_VERSION: "4"
      GIT_STRATEGY: fetch
      DOCKER_IMAGE: $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA

    build_and_deploy_container_image:
      services:
      - name: docker:dind
        alias: dind
      image: docker:19.03.5
      stage: build
      before_script:
        - docker login -u gitlab-ci-token -p $CI_JOB_TOKEN $CI_REGISTRY
      script:
        - docker pull $CI_REGISTRY_IMAGE:latest || true
        - docker build --tag $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA --tag $CI_REGISTRY_IMAGE:latest .
        - docker push $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
        - docker push $CI_REGISTRY_IMAGE:latest
      after_script:
        - docker logout registry.gitlab.com

> **NOTE** : If a project is public, so is the Container Registry. To pull the image, you can use ```docker pull``` command with the link of the container image. For example, ```registry.gitlab.com/xxx/webgoat.net_devsecops:latest``` 

## VAmPI - Python Web API
*GitHub Repository: [Link](https://github.com/erev0s/VAmPI)*

VAmPI is a vulnerable API made with Flask and it includes vulnerabilities from the OWASP top 10 vulnerabilities for APIs. It was created as I wanted a vulnerable API to evaluate the efficiency of tools used to detect security issues in APIs. It includes a switch on/off to allow the API to be vulnerable or not while testing. This allows to cover better the cases for false positives/negatives. VAmPI can also be used for learning/teaching purposes. You can find a bit more details about the vulnerabilities in erev0s.com.

### CI/CD Configuration - VAmPI
1. Ensure you have read the [GitLab CI/CD](#gitlab-cicd) before starting with the CI/CD configuration. To start on CI/CD configuration, you can simply click the ```Set Up CI/CD``` button in the UI under Project overview -> Details, then it will navigate to CI/CD editor click on ```Create new CI/CD pipeline``` and it will create a ```.gitlab-ci.yml``` file which is used for CI/CD pipeline configuration.
   ![CI/CD](./img/Set-Up.PNG)
   ![CI/CD](./img/CICD.PNG)

   Once created, you can directly edit using the editor provider. If you don't know how to start, you can look at some of these [templates](https://docs.gitlab.com/ee/ci/examples/README.html#cicd-templates) provided by GitLab.

2. Let's go straight into the configuration. There are two stages in our CI/CD pipeline :
   
        stages:
        - build
        - fuzz

   - ```build``` stage build the container image and deploy to container registry
   - ```fuzz``` stage performs fuzz testing of API operation parameters.

3. Once we planned the stages and decide image to be used for most of the jobs, we can start configuring each stage to include the neccessary jobs.
   
    Since we are using this project to demonstrate API Fuzzing, it only contains the minimal jobs to perform API Fuzzing however you can add in your own test.

    CI/CD Pipeline:
    | Build          | Fuzz            |
    |----------------|-------------------|
    | build and deploy container image | apifuzzer fuzz |
    <br>
### CI/CD Build Stage - VAmPI
Under the build stage, there are two jobs under build stage :

- ```Build and Deploy to container registry``` : builds Docker images from a Dockerfile and deploy to GitLab Container Registry

The script below login to the container registry then build, tag and push the container image to gitlab container registry. This image will be use to set up a service which will be use for API fuzzing in the next stage. For more details, you can read from the previous use case, [WebGoat.NET](#cicd-build-stage---webgoatnet).

      build_and_deploy_container_image:
        services:
        - name: docker:dind
          alias: dind
        image: docker:19.03.5
        stage: build
        before_script:
          - docker login -u gitlab-ci-token -p $CI_JOB_TOKEN $CI_REGISTRY
        script:
          - docker pull $CI_REGISTRY_IMAGE:latest || true
          - docker build --cache-from $CI_REGISTRY_IMAGE:latest --tag $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA --tag $CI_REGISTRY_IMAGE:latest .
          - docker push $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
          - docker push $CI_REGISTRY_IMAGE:latest
        after_script:
          - docker logout registry.gitlab.com
  
### CI/CD Fuzz Stage - VAmPI
Under the fuzz stage, there is only one job:

#### API Fuzzing - VAmPI
Web API fuzzing performs fuzz testing of API operation parameters. Fuzz testing sets operation parameters to unexpected values in an effort to cause unexpected behavior and errors in the API backend. This helps you discover bugs and potential security issues that other QA processes may miss.

Web API fuzzing runs in the ```fuzz``` stage of the CI/CD pipeline. To ensure API fuzzing scans the latest code, your CI/CD pipeline should deploy changes to a test environment in one of the stages preceding the ```fuzz``` stage.

Note the following changes have been made to the API fuzzing template:

- In GitLab 14.0 and later, you must define a ```fuzz``` stage in your .gitlab-ci.yml file.
- In GitLab 13.12 and earlier, the API fuzzing template defines ```build```, ```test```, ```deploy```, and ```fuzz``` stages. The ```fuzz``` stage runs last by default. The predefined stages were deprecated, and removed from the ```API-Fuzzing.latest.gitlab-ci.yml``` template. They will be removed in a future GitLab version.

You can run a Web API fuzzing scan using the following methods:

- OpenAPI Specification - version 2.0 or 3.0
- HTTP Archive (HAR)
- Postman Collection - version 2.0 or 2.1 (We are using this)

To enable Web API fuzzing:
  
- Include the API fuzzing template in your .gitlab-ci.yml file.
- From GitLab 13.10 and later, use the Web API fuzzing configuration form.
- For manual configuration instructions, see the respective section, depending on the API type:
  - [OpenAPI Specification](https://docs.gitlab.com/ee/user/application_security/api_fuzzing/#openapi-specification)
  - [HTTP Archive (HAR)](https://docs.gitlab.com/ee/user/application_security/api_fuzzing/#http-archive-har)
  - [Postman Collection](https://docs.gitlab.com/ee/user/application_security/api_fuzzing/#postman-collection)
- Otherwise, see [Web API fuzzing configuration form](https://docs.gitlab.com/ee/user/application_security/api_fuzzing/#web-api-fuzzing-configuration-form)

To configure API fuzzing to use a Postman Collection file:
1. Add the ```fuzz``` stage to your ```.gitlab-ci.yml``` file.
2. Include the ```API-Fuzzing.gitlab-ci.yml``` template in your ```.gitlab-ci.yml``` file.
    
        include:
        - template: API-Fuzzing.gitlab-ci.yml

3. Provide the profile by adding the ```FUZZAPI_PROFILE CI/CD``` variable to your ```.gitlab-ci.yml``` file. The profile specifies how many tests are run. Substitute ```Quick-10``` for the profile you choose. For more details, see ```API fuzzing profiles```.

        variables:
          FUZZAPI_PROFILE: Quick-10

4. Provide the location of the Postman Collection specification. You can provide the specification as a file or URL. URL support was introduced in GitLab 13.10 and later. Specify the location by adding the ```FUZZAPI_POSTMAN_COLLECTION``` variable.

5. Provide the target API instance’s base URL. Use either the FUZZAPI_TARGET_URL variable or an environment_url.txt file.

> **NOTE** : When you export a Postman collection, only Postman collection variables are exported into the Postman file. For example, Postman does not export environment-scoped variables into the Postman file. 
> 
> By default, the API fuzzer uses the Postman file to resolve Postman variable values. If a JSON file is set in a GitLab CI/CD variable ```FUZZAPI_POSTMAN_COLLECTION_VARIABLES```, then the JSON file takes precedence to get Postman variable values. 
> 
> Although Postman can export environment variables into a JSON file, the format is not compatible with the JSON expected by ```FUZZAPI_POSTMAN_COLLECTION_VARIABLES```. 
> 
> As the postman collection use by VAmPI using environment variable for BaseURL as well, I created a ```variable-collection-dictionary.json``` under ```openapi_specs/ ```.

6. Follow up from the following steps, this is the current configuration, 
   
        variables:
          FUZZAPI_POSTMAN_COLLECTION: openapi_specs/VAmPI.postman_collection.json
          FUZZAPI_POSTMAN_COLLECTION_VARIABLES: openapi_specs/variable-collection-dictionary.json
          FUZZAPI_TARGET_URL: http://vulnapi:80/
          FUZZAPI_PROFILE: Medium-20

7. As you can see under the ```FUZZAPI_TARGET_URL```, the target URl is http://vulnapi:80. To perform API fuzzing, we need the API to be running and instead of having a testing environment, I leverage the use of [GitLab Services](#gitlab-services) which allow user to define a Docker image that runs during a job linked to the Docker image that the image keyword defines. This allows you to access the service image during build time. 

          services: 
          - name: $CI_REGISTRY_IMAGE:latest
            alias: vulnapi
    
    With this, we can run our application as service for us to perform API fuzzing, this service can be accessed by the service hostname which is defined by the alias so in this case the hostname for our application will be ```http://vulnapi:80/``` 

> **NOTE** : The dockerfile/app.py tell us that the application is running on port 80.

8. We can also add authentication to the fuzzer. Authentication is handled by providing the authentication token as a header or cookie. You can provide a script that performs an authentication flow or calculates the token.

    If the bearer token must be generated and doesn’t expire during testing, you can provide to API fuzzing a file containing the token. A prior stage and job, or part of the API fuzzing job, can generate this file.

    API fuzzing expects to receive a JSON file with the following structure:

        {
        "headers" : {
          "Authorization" : "Bearer xxxxxxxxxxxxxxxxxxxxx"
            }
        }
    
    This file can be generated by a prior stage and provided to API fuzzing through the FUZZAPI_OVERRIDES_FILE CI/CD variable.

    So to add authentication, I wrote a script (generate_token.py) that generate the authentication token json file and runs it before the job using ```before_script:``` keyword and set ```FUZZAPI_OVERRIDES_FILE``` in my ```.gitlab-ci.yml``` file:

    generate_token.py:

        import requests
        import json
        RegisterPayload = {
            "username": "Test",
            "password": "TestP@ssw0rd",
            "email": "Test@gmail.com"
        }

        LoginPayload = {
            "username": "Test",
            "password": "TestP@ssw0rd"
        }

        RegisterResp = requests.post("http://vulnapi:80/users/v1/register", json=RegisterPayload)
        LoginResp = requests.post("http://vulnapi:80/users/v1/login", json=LoginPayload)
        JsonResponse = LoginResp.json()
        data = dict()
        token = dict()
        token["Authorization"] = "Bearer " + JsonResponse["auth_token"]
        data["headers"] = token
        with open('token.json', 'w') as outfile:
        json.dump(data, outfile)

    Added to .gitlab-ci.yml:

          variables:
            FUZZAPI_OVERRIDES_FILE: token.json

          apifuzzer_fuzz:
            before_script:
              - python generate_token.py

9. The script that does the fuzzing job is shown below after adding each component from previous steps.

        include:
          - template: API-Fuzzing.gitlab-ci.yml

        services: 
          - name: $CI_REGISTRY_IMAGE:latest
            alias: vulnapi

        variables:
          FUZZAPI_POSTMAN_COLLECTION: openapi_specs/VAmPI.postman_collection.json
          FUZZAPI_POSTMAN_COLLECTION_VARIABLES: openapi_specs/variable-collection-dictionary.json
          FUZZAPI_TARGET_URL: http://vulnapi:80/
          FUZZAPI_PROFILE: Medium-20
          FUZZAPI_OVERRIDES_FILE: token.json

        stages:
          - fuzz

        apifuzzer_fuzz:
          before_script:
            - python generate_token.py

### Conclusion - VAmPI
Once the CI/CD is configured, the pipeline will runs whenever there is a new change in source code/merge request in the project. The configuration and pipeline are shown below:

Final ```.gitlab-ci.yml``` configuration:

    include:
      - template: API-Fuzzing.gitlab-ci.yml

    services: 
      - name: $CI_REGISTRY_IMAGE:latest
        alias: vulnapi

    variables:
      FUZZAPI_POSTMAN_COLLECTION: openapi_specs/VAmPI.postman_collection.json
      FUZZAPI_POSTMAN_COLLECTION_VARIABLES: openapi_specs/variable-collection-dictionary.json
      FUZZAPI_TARGET_URL: http://vulnapi:80/
      FUZZAPI_PROFILE: Medium-20
      FUZZAPI_OVERRIDES_FILE: token.json

    stages:
      - build
      - fuzz
      
    build_and_deploy_container_image:
      services:
        - name: docker:dind
          alias: dind
      image: docker:19.03.5
      stage: build
      before_script:
        - docker login -u gitlab-ci-token -p $CI_JOB_TOKEN $CI_REGISTRY
      script:
        - docker pull $CI_REGISTRY_IMAGE:latest || true
        - docker build --cache-from $CI_REGISTRY_IMAGE:latest --tag $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA --tag $CI_REGISTRY_IMAGE:latest .
        - docker push $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
        - docker push $CI_REGISTRY_IMAGE:latest
      after_script:
        - docker logout registry.gitlab.com

    apifuzzer_fuzz:
      before_script:
        - python generate_token.py

## NodeGoat - NodeJS Web Application
*GitHub Repository: [Link](https://github.com/OWASP/NodeGoat)*

Being lightweight, fast, and scalable, Node.js is becoming a widely adopted platform for developing web applications. This project provides an environment to learn how OWASP Top 10 security risks apply to web applications developed using Node.js and how to effectively address them.

We will be using this project to demonstrate the full DevSecOps workflow.

### CI/CD Configuration - NodeGoat
1. Ensure you have read the [GitLab CI/CD](#gitlab-cicd) before starting with the CI/CD configuration. To start on CI/CD configuration, you can simply click the ```Set Up CI/CD``` button in the UI under Project overview -> Details, then it will navigate to CI/CD editor click on ```Create new CI/CD pipeline``` and it will create a ```.gitlab-ci.yml``` file which is used for CI/CD pipeline configuration.
   ![CI/CD](./img/Set-Up.PNG)
   ![CI/CD](./img/CICD.PNG)

   Once created, you can directly edit using the editor provider. If you don't know how to start, you can look at some of these [templates](https://docs.gitlab.com/ee/ci/examples/README.html#cicd-templates) provided by GitLab.

2. Let's go straight into the configuration. There are four stages in our CI/CD pipeline :
   
        stages:
        - build
        - test
        - dast
        - deploy

   - ```build``` stage build the container image and deploy to container registry
   - ```test``` stage runs our unit tests and security tests
   - ```dast``` stage perform Dynamic Application Security Testing on our Web Application using services.
   - ```deploy``` stage deploy the application to Azure Kubernetes Service (AKS) 

3. Once we planned the stages, we can start configuring each stage to include the neccessary jobs. 
   
   CI/CD Pipeline:
  
    | Build | Test | Dast | Deploy |
    |-|-|-|-|
    | build and deploy container image | unit testing | dynamic application security testing | deploy |
    |  | code quality |  |  |
    |  | secret detection |  |  |
    |  | container scanning |  |  |
    |  | static application security testing |  |  |
    |  | dependency scanning |  |  |
    |  | license scanning |  |  |
    <br>

### CI/CD Build Stage - NodeGoat
Under the build stage, there are two jobs under build stage :

- ```Build and Deploy to container registry``` : builds Docker images from a Dockerfile and deploy to GitLab Container Registry

> **NOTE** : In the dockerfile, it is lack of ENTRYPOINT that execute command to run the application. Hence, I added the script below to run the shell script to run the application. 

      COPY entrypoint.sh /usr/local/bin/
      RUN ["chmod", "+x","/usr/local/bin/entrypoint.sh"]
      ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]

The ```entrypoint.sh``` shell script :

    #!/bin/sh

    until nc -z -w 2 mongo 27017 && echo 'mongo is ready for connections' && node artifacts/db-reset.js && npm start; do sleep 2; done

The script below login to the container registry then build, tag and push the container image to gitlab container registry. This image will be use to set up a service which will be use for DAST in the next stage as well as used for deployment later on.

      build_and_deploy_container_image:
        services:
        - name: docker:dind
          alias: dind
        image: docker:19.03.5
        stage: build
        before_script:
          - docker login -u gitlab-ci-token -p $CI_JOB_TOKEN $CI_REGISTRY
        script:
          - docker pull $CI_REGISTRY_IMAGE:latest || true
          - docker build --cache-from $CI_REGISTRY_IMAGE:latest --tag $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA --tag $CI_REGISTRY_IMAGE:latest .
          - docker push $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
          - docker push $CI_REGISTRY_IMAGE:latest
        after_script:
          - docker logout registry.gitlab.com
  
### CI/CD Test Stage - NodeGoat
Under the test stage, there are seven jobs:

#### Unit Testing - NodeGoat
This job runs the preconfigured unit tests which are the fundamental tests in your app testing strategy, from which you can verify that the logic of individual units is correct. They are a fantastic way to catch regressions when making changes to your app. 
- To configure this test, you just need to include this in your CI configuration:

      unitTesting:
          image: node:latest
          cache: 
            paths:
              - node_modules/
          before_script:
            - npm ci
          stage: test
          script: 
            - npm run test

#### Code Quality - NodeGoat
From the [AndroGoat](#code-quality-scan---androgoat) use case, we learn how we can include code quality to our project. So to add code quality to our NodeGoat project, we simply the following script to our CI configuration yml file:

      include:
        - template: Code-Quality.gitlab-ci.yml

#### Secret Detection - NodeGoat
Same from secret detection, from the [AndroGoat](#secret-detection---androgoat) use case, we understand how we can include secret detection to our NodeGoat project, we simply include the template with full history scan enabled: 

      include:
        - template: Security/Secret-Detection.gitlab-ci.yml

      secret_detection:
        variables:
          SECRET_DETECTION_HISTORIC_SCAN: "true"

#### Container Scanning
From the [WebGoat.NET](#container-scanning---webgoatnet) use case, we also learn to include container scanning to our project to scan our containerized application. To add container sccaning to our NodeGoat project, we simply include the following to our yml file:

      include:
        - template: Container-Scanning.gitlab-ci.yml

      variables:
        CS_MAJOR_VERSION: "4"
        GIT_STRATEGY: fetch
        DOCKER_IMAGE: $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
  
> **NOTE** : When you review the container scanning report, it may shows 0 vulnerability found and this is because the container image is build on an alphine image where the minimal library of the latest version is installed.
> 
>  Alpine Linux is a Linux distribution built around musl libc and BusyBox. The image is only 5 MB in size and has access to a package repository that is much more complete than other BusyBox based images. This makes Alpine Linux a great image base for utilities and even production applications. For more information, you can read [**HERE**](https://hub.docker.com/_/alpine)
#### Static Application Security Testing - NodeGoat
As mentioned in [AndroGoat](#static-application-security-test---androgoat) use case, GitLab supports a variety of languages, package managers, and frameworks. So for NodeJS, they uses eslint, semgrep and nodejs scan. They are all enabled on default, you can exclude the analyzer using ```SAST_EXCLUDED_ANALYZERS``` variable.

So to add SAST to our NodeGoat project, we just need to add the following script: 

    include:
      - template: Security/SAST.gitlab-ci.yml

    variables:
      SAST_EXCLUDED_ANALYZERS: "eslint, semgrep"

#### Dependency Scanning
The Dependency Scanning feature can automatically find security vulnerabilities in your dependencies while you’re developing and testing your applications. For example, dependency scanning lets you know if your application uses an external (open source) library that is known to be vulnerable. You can then take action to protect your application.

If you’re using GitLab CI/CD, you can use dependency scanning to analyze your dependencies for known vulnerabilities. GitLab scans all dependencies, including transitive dependencies (also known as nested dependencies). You can take advantage of dependency scanning by either:

- Including the dependency scanning template in your existing .gitlab-ci.yml file.

      include:
        - template: Dependency-Scanning.gitlab-ci.yml
  
- Implicitly using the auto dependency scanning provided by Auto DevOps.

> **NOTE** : The Dependency Scan may trigger multiple analyzer, you can override the names of the official default images by using ```DS_DEFAULT_ANALYZERS``` (DEPRECATED - use ```DS_EXCLUDED_ANALYZERS``` instead)

    variables:
      ### Dependency Scannig Variables
      # DS_DEFAULT_ANALYZERS: "gemnasium"
      DS_DEFAULT_ANALYZERS: "retire.js"

For information, you can click [**HERE**](https://docs.gitlab.com/ee/user/application_security/dependency_scanning).

#### License Scanning
If you’re using GitLab CI/CD, you can use License Compliance to search your project’s dependencies for their licenses. You can then decide whether to allow or deny the use of each license. For example, if your application uses an external (open source) library whose license is incompatible with yours, then you can deny the use of that license.

You can take advantage of License Compliance by either:

- Including the job in your existing ```.gitlab-ci.yml``` file.
  
        include:
        - template: Security/License-Scanning.gitlab-ci.yml
        
- Implicitly using Auto License Compliance, provided by Auto DevOps.

The License Finder scan tool runs as part of the CI/CD pipeline, and detects the licenses in use. GitLab checks the License Compliance report, compares the licenses between the source and target branches, and shows the information right on the merge request. Denied licenses are indicated by a x red icon next to them as well as new licenses that need a decision from you. In addition, you can manually allow or deny licenses in your project’s license compliance policy section. If a denied license is detected in a new commit, GitLab blocks any merge requests containing that commit and instructs the developer to remove the license.

For more information, you can click [**HERE**](https://docs.gitlab.com/ee/user/compliance/license_compliance/).

### CI/CD Dast Stage - NodeGoat
#### Dynamic Application Security Testing
Under the dast stage, there is only one job which is Dynamic Application Security Testing (DAST).

If you deploy your web application into a new environment, your application may become exposed to new types of attacks. For example, misconfigurations of your application server or incorrect assumptions about security controls may not be visible from the source code.

Dynamic Application Security Testing (DAST) examines applications for vulnerabilities like these in deployed environments. DAST uses the open source tool [OWASP Zed Attack Proxy](https://www.zaproxy.org/) for analysis.

To enable DAST, either:
  
- Enable Auto DAST (provided by Auto DevOps).
- Manually include the DAST template in your existing .gitlab-ci.yml file

To include the DAST template:

1. Select the CI/CD template you want to use:

   - DAST.gitlab-ci.yml: Stable version of the DAST CI/CD template.
   - DAST.latest.gitlab-ci.yml: Latest version of the DAST template. (Introduced in GitLab 13.8).
> **NOTE** : The latest version of the template may include breaking changes. Use the stable template unless you need a feature provided only in the latest template.

2. Add a dast stage to your GitLab CI stages configuration:

        stages:
          - dast

3. Add the template to ```.gitlab-ci.yml```

        include:
          - template: DAST.gitlab-ci.yml

    The included template creates a dast job in your CI/CD pipeline and scans your project’s running application for possible vulnerabilities.

    The results are saved as a DAST report artifact that you can later download and analyze. Due to implementation limitations, we always take the latest DAST artifact available. Behind the scenes, the GitLab DAST Docker image is used to run the tests on the specified URL and scan it for possible vulnerabilities.

    By default, the DAST template uses the latest major version of the DAST Docker image.

4. Define the URL to be scanned by DAST by using one of these methods:
   - Set the ```DAST_WEBSITE``` CI/CD variable. If set, this value takes precedence. 
  
          variables:
            DAST_WEBSITE: http://example.com:80/
    
   - Add the URL in an ```environment_url.txt``` file at the root of your project. This is useful for testing in dynamic environments. To run DAST against an application dynamically created during a GitLab CI/CD pipeline, a job that runs prior to the DAST scan must persist the application’s domain in an ```environment_url.txt``` file. DAST automatically parses the ```environment_url.txt``` file to find its scan target.

5. Depending on the complexity of the target application, there are a few options as to how to deploy and configure the DAST template. Since our application utilizes Docker containers, we have another option for deploying and scanning with DAST. After our Docker build job completes and the image is added to the container registry, we can utilize the image as a [service](#gitlab-services).

    By using ```service``` definitions in your ```gitlab-ci.yml```, we can scan services (The Application) with the DAST analyzer.

            services: 
              - name: mongo:latest
                alias: mongo
              - name: $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
                alias: nodegoat
            
            variables:
                FF_NETWORK_PER_BUILD: "true"

    With this, we can run our application as service for us to perform DAST, this service can be accessed by the service hostname which is defined by the alias so in this case the hostname for our application and our mongodb will be ```http://nodegoat:4000/``` and ```mongodb://mongo:27017/```.

    By default the application will be hosted on port 4000 and will connect to a MongoDB instance at localhost:27017. To change this set the environment variables ```PORT``` and ```MONGODB_URI```. For the service and deployment later on, the MongoDB instance is at mongo:27017/ hence we will need to edit the config file (config/env/all.js) to change the MONGODB_URI.

    Since our applications depend on multiple services such as databases (mongodb) or caching services. By default, services defined in the services fields cannot communicate with each another. To allow communication between services, enable the ```FF_NETWORK_PER_BUILD``` feature flag.

    DAST can be configured to perform ZAP Full Scan, which includes both passive and active scanning against the same target website which is ```http://nodegoat:4000/```. I also set ```DAST_USE_AJAX_SPIDER``` to true to use the AJAX spider in addition to the traditional spider, useful for crawling sites that require JavaScripy.

          variables:
              FF_NETWORK_PER_BUILD: "true" # enable network per build so all services can communicate on the same network
              DAST_FULL_SCAN_ENABLED: "true" # do a full scan
              DAST_ZAP_USE_AJAX_SPIDER: "true" # use the ajax spider
              DAST_WEBSITE: "http://nodegoat:4000/" # set the target website

6. It’s also possible to authenticate the user before performing the DAST checks.
   
    Create masked CI/CD variables to pass the credentials that DAST uses. To create masked variables for the username and password, see [Create a custom variable](https://docs.gitlab.com/ee/ci/variables/README.html#custom-cicd-variables) in the UI. Note that the key of the username variable must be ```DAST_USERNAME``` and the key of the password variable must be ```DAST_PASSWORD```.

    We can use the variable to create a sample user which will be use for the DAST job by using ```before_script``` keyword under ```dast``` job to create user.

          dast:
            before_script: 
              - curl -v -d 'userName=$GOAT_USERNAME&firstName=test&lastName=test&password=$GOAT_PASSWORD&verify=$GOAT_PASSWORD&email=&_csrf=' "http://nodegoat:4000/signup"

    After DAST has authenticated with the application, all cookies are collected from the web browser. For each cookie a matching session token is created for use by ZAP. This ensures ZAP is recognized by the application as correctly authenticated.

    Other variables that are related to authenticated scans are:

        variables:
          DAST_WEBSITE: "http://nodegoat:4000/" # set the target website
          DAST_AUTH_URL: "http://nodegoat:4000/login" # set the target authentication URL
          # Use CI/CD variables to protect the password (Settings -> CI/CD -> Variables)
          DAST_USERNAME: $GOAT_USERNAME  
          DAST_PASSWORD: $GOAT_PASSWORD
          # Find the username and password fields in the /login page
          DAST_USERNAME_FIELD: "userName"
          DAST_PASSWORD_FIELD: "password"

> **NOTE** : GitLab highly recommended that you configure the scanner to authenticate to the application, otherwise it cannot check most of the application for security risks, as most of your application is likely not accessible without authentication. It is also recommended that you periodically confirm the scanner’s authentication is still working as this tends to break over time due to authentication changes to the application.

7. So the DAST is fully configured and the full configuration for the dast job is shown below :

        include:
          - template: DAST.gitlab-ci.yml

        services:
          - name: mongo:latest
            alias: mongo
          - name: $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
            alias: nodegoat

        variables:
          ### DAST Variables
          FF_NETWORK_PER_BUILD: "true" # enable network per build so all services can communicate on the same network
          DAST_FULL_SCAN_ENABLED: "true" # do a full scan
          DAST_ZAP_USE_AJAX_SPIDER: "true" # use the ajax spider
          DAST_WEBSITE: "http://nodegoat:4000/" # set the target website
          DAST_AUTH_URL: "http://nodegoat:4000/login" # set the target authentication URL
          # Use CI/CD variables to protect the password (Settings -> CI/CD -> Variables)
          DAST_USERNAME: $GOAT_USERNAME  
          DAST_PASSWORD: $GOAT_PASSWORD
          # Find the username and password fields in the /login page
          DAST_USERNAME_FIELD: "userName"
          DAST_PASSWORD_FIELD: "password"

        stages: 
          - dast

        dast:
          # Register the user first, note this assumes the application is up and running for registration to succeed
          before_script: 
            - curl -v -d 'userName=$GOAT_USERNAME&firstName=test&lastName=test&password=$GOAT_PASSWORD&verify=$GOAT_PASSWORD&email=&_csrf=' "http://nodegoat:4000/signup"
  
### CI/CD Deploy Stage - NodeGoat
This stage does the deploy job to Azure Kubernetes Service.

> AKS and its dependent resources are created by another student through Azure CLI. There are different ways to create the AKS Cluster. You can use Azure Portal (User Interface) or Azure CLI (Command Line Interface) or Terraform (Infrastructure as Code) to create AKS Cluster and its dependent resources

1. Knowing that our Azure Kubernetes Service is ready, we can connect GitLab to Azure Kubernetes Service for GitLab project Kubernetes integration. In your Gitlab project, navigate to Operations > Kubernetes > Integrate with a cluster certificate > Add Existing Cluster.

    Using this form, we will supply the credentials we need to reach our Kubernetes cluster.

2. Required Configuration Parameters
    | Required Field | Example |
    |:-:|:-:|
    | Kubernetes cluster name | aks-accelerator-aks |
    | Environment scope | staging |
    | API URL | https://aks-accelerator-xxxxxxxx.hcp.$REGION.azmk8s.io:443 |
    | CA Certificate | A PEM (plaintext) x509 certificate |
    | Token | The token for a Kubernetes ServiceAccount called gitlab-admin that has been granted the cluster-admin role |
    | Project namespace (optional, unique) | Can be left blank to ask Gitlab to create a Kubernetes namespace for the project |
    | RBAC-enabled cluster | Specified when creating the cluster |
    <br>

    - **Kubernetes Cluster Name**
    
      Specified when creating the cluster. Can be retrieved with the Azure CLI using ```az aks list --o=table``` or ```kubectl config current-context``` once you login using ```az login```
    
    - **Environment Scope**

      Environment Scope is used to tell Gitlab how to use the Cluster (e.g. for Dev, Staging, Prod or for all workloads). For the purposes of this repo, we have declared ```production```, you will need ensure that ```.gitlab-ci.yml``` declares the environment specified for the cluster.

    - **API URL**
  
      The Kubernetes API server, visible as the ```fqdn``` in ```az aks list --o=table```. Remember to prefix with ```https:```.

    - **CA Certificate**

      The AKS API Server endpoint is secured with a self-signed TLS certificate. Gitlab must be provided with the CA cert so that it can trust it.

      Following GitLab instructions: 
      - List the available secrets with ```kubectl get secrets```; one should have name matching default-token-xxxxx.
      - Using ```kubectl get secret``` and the name of this token, lookup the certificate in the config map, and decode.

            kubectl get secret default-token-abcde -o jsonpath="{['data']['ca\.crt']}" | base64 --decode

      OR you can just look for it under ```C:\Users\xxx\.kube```, ```certificate-authority-data```.

    - **Token**

      GitLab authenticates against Kubernetes using service tokens, which are scoped to a particular namespace. The token used should belong to a service account with cluster-admin privileges. The ```gitlab-admin-service-account.yaml``` file referenced below can be found in the ```/kubernetes``` folder of the project repository. 

      - Create a ```ServiceAccount``` called ```gitlab-admin```:
  
            kubectl apply -f gitlab-admin-service-account.yaml
      
      - Acquire the ```token``` for the ```gitlab-admin``` ServiceAccount and copy the token:
  
            kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep gitlab-admin | awk '{print $1}')

3. Now the cluster is connected once the configuration is done, we will just need to create a new job, ```deploy``` under our ```deploy``` stage.
  
        deploy:
          stage: deploy
          environment:
            name: production
    
    Next, we just need an image that contains ```kubectl```. We could roll our own, and may wish to do so in environments where security is paramount. For the purposes of this example, we will leverage Dockerhub:

        image:
          name: lachlanevenson/k8s-kubectl
          entrypoint: [""]
    
    All that remains is to instruct ```kuberctl``` to create our deployments:

        script:
          - kubectl apply -f ./kubernetes/mongo-deployment.yaml,./kubernetes/mongo-service.yaml,./kubernetes/web-deployment.yaml,./kubernetes/web-service.yaml
          - kubectl set image deployment/web web=$CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
        when: manual

    Since the cluster is already integrated with GitLab, special deployment variables are made available to your job and configuration is not required. You can immediately begin interacting with the cluster from your jobs using tools such as ```kubectl``` or ```helm```.

    I also make the deployment job manual by adding ```when: manual``` to its configuration. To deploy, you simply click on the play button in the pipeline. Once deployed, you can locate your deployment with ```kubectl get services -n gitlab-managed-apps``` and the IP address you can use to access the web application is the ```EXTERNAL_IP``` or obtain from Azure Portal.

> **NOTE** : The kubernetes deployment and service yaml file require you to write yourself if it wasn't provided where in my case i leverage the use of kompose to convert docker-compose script to kubernetes yaml file which includes the deployment for the application and MongoDB as well as service for the application and the MongoDB. Some editing is required as it only provides you an template to start on the configuration.

Final configuration for deployment:

    stages: 
      - deploy

    deploy:
      stage: deploy
      environment:
        name: production
      image:
        name: lachlanevenson/k8s-kubectl
        entrypoint: [""]
      script:
        - kubectl apply -f ./kubernetes/mongo-deployment.yaml,./kubernetes/mongo-service.yaml,./kubernetes/web-deployment.yaml,./kubernetes/web-service.yaml
        - kubectl set image deployment/web web=$CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
      when: manual
      
### Conclusion - NodeGoat
Once the CI/CD is configured, the pipeline will runs whenever there is a new change in source code/merge request in the project. The configuration and pipeline are shown below:

Final ```.gitlab-ci.yml``` configuration:

        include:
          - template: Security/SAST.gitlab-ci.yml
          - template: Security/Secret-Detection.gitlab-ci.yml
          - template: Code-Quality.gitlab-ci.yml
          # # GitLab Ultimate Only
          - template: Dependency-Scanning.gitlab-ci.yml
          - template: Security/License-Scanning.gitlab-ci.yml
          - template: DAST.gitlab-ci.yml
          - template: Container-Scanning.gitlab-ci.yml

        services: # use services to link the nodegoat container to the dast job
          - name: mongo:latest
            alias: mongo
          - name: $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
            alias: nodegoat

        variables:
          ### Dependency Scannig Variables
          # DS_DEFAULT_ANALYZERS: "gemnasium"
          DS_DEFAULT_ANALYZERS: "retire.js"

          ### DAST Variables
          FF_NETWORK_PER_BUILD: "true" # enable network per build so all services can communicate on the same network
          DAST_FULL_SCAN_ENABLED: "true" # do a full scan
          DAST_ZAP_USE_AJAX_SPIDER: "true" # use the ajax spider
          DAST_WEBSITE: "http://nodegoat:4000/" # set the target website
          DAST_AUTH_URL: "http://nodegoat:4000/login" # set the target authentication URL
          # Use CI/CD variables to protect the password (Settings -> CI/CD -> Variables)
          DAST_USERNAME: $GOAT_USERNAME  
          DAST_PASSWORD: $GOAT_PASSWORD
          # Find the username and password fields in the /login page
          DAST_USERNAME_FIELD: "userName"
          DAST_PASSWORD_FIELD: "password"

          # Container Scanning Variables
          CS_MAJOR_VERSION: "4"
          GIT_STRATEGY: fetch
          DOCKER_IMAGE: $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA

          SAST_EXCLUDED_ANALYZERS: "eslint, semgrep"

        stages: 
          - build
          - test
          - dast
          - deploy

        unitTesting:
            image: node:latest
            cache: 
              paths:
                - node_modules/
            before_script:
              - npm ci
            stage: test
            script: 
              - npm run test

        secret_detection:
          variables:
            SECRET_DETECTION_HISTORIC_SCAN: "true"

        build_and_deploy_container_image:
          services:
          - name: docker:dind
            alias: dind
          image: docker:19.03.5
          stage: build
          before_script:
            - docker login -u gitlab-ci-token -p $CI_JOB_TOKEN $CI_REGISTRY
          script:
            - docker pull $CI_REGISTRY_IMAGE:latest || true
            - docker build --cache-from $CI_REGISTRY_IMAGE:latest --tag $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA --tag $CI_REGISTRY_IMAGE:latest .
            - docker push $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
            - docker push $CI_REGISTRY_IMAGE:latest
          after_script:
            - docker logout registry.gitlab.com

        # container_scanning:
        #   variables:
        #     DOCKER_IMAGE: $CI_REGISTRY_IMAGE:latest
        #     CLAIR_TRACE: "true"

        dast:
          # Register the user first, note this assumes the application is up and running for registration to succeed
          before_script: 
            - curl -v -d 'userName=$GOAT_USERNAME&firstName=test&lastName=test&password=$GOAT_PASSWORD&verify=$GOAT_PASSWORD&email=&_csrf=' "http://nodegoat:4000/signup"

        deploy:
          stage: deploy
          environment:
            name: production
          image:
            name: lachlanevenson/k8s-kubectl
            entrypoint: [""]
          script:
            - kubectl apply -f ./kubernetes/mongo-deployment.yaml,./kubernetes/mongo-service.yaml,./kubernetes/web-deployment.yaml,./kubernetes/web-service.yaml
            - kubectl set image deployment/web web=$CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
          when: manual

# Improvements
- Explore GitLab AutoDevOps feature
- DAST API can be added to VAmPI pipeline (New Feature for GitLab 14.0)
- Use Terraform to set up AKS infrastructure

# Conclusion
DevSecOps extends the DevOps workflow to include automated security processes and tooling, giving you continuous and frictionless security testing that replaces disruptive bottlenecks at the end of the development process. This tighter integration also leads to better security outcomes, such as fewer vulnerabilities and enhanced compliance.

**Image Source** : https://blog.sqreen.com/secdevops/

# Reference
- https://www.atlassian.com/devops
- https://www.checkpoint.com/cyber-hub/cloud-security/what-is-devsecops/
- https://www.redhat.com/en/topics/devops/what-is-ci-cd
- https://i.blackhat.com/USA-19/Thursday/us-19-Shrivastava-DevSecOps-What-Why-And-How.pd
- https://medium.com/@matuzg/testing-docker-cve-scanners-part-1-false-negatives-and-what-they-mean-for-your-security-77fc4eb1b2cf
- https://about.gitlab.com/what-is-gitlab/
- https://about.gitlab.com/stages-devops-lifecycle/
- https://docs.gitlab.com/
- https://about.gitlab.com/blog/2018/10/24/setting-up-gitlab-ci-for-android-projects/
- https://gitlab.com/citihub/aks-accelerator/-/tree/master
- https://gitlab.com/gitlab-org/security-products/demos/dast/nodegoat
- https://blog.sqreen.com/secdevops/
- https://hub.docker.com/_/alpine
