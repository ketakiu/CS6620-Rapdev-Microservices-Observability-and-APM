# CS6620-Rapdev-Microservices-Observability-and-APM

** **
## 1. Vision and Goals Of The Project:

Goal of this project is to establish a CI/CD pipeline for Social Network microservice application which automates testing , integration, deployment, and delivery.
High level Goals of this project are:
* Monitoring microservices, CI/CD, and develop a dashboard using Datadog APM and Jaeger

* Write test cases for the exisiting Social Network Microservices using Datadog Synthetic Monitoring.


## 2. Users/Personas Of The Project

Social Network-monitoring module will be used by the administrators of cloud services, DEV-ops engineers, network engineers including researchers from BU, NU, MIT, HU and UMass, MGHPCC contributing companies, Commonwealth companies and government institutions, and paying users. 

It does not target:

* End users using the Social Network application.


## 3. Scope and Features Of The Project:

Social Network Application 

* The scope of the project includes exploring the CI/CD services, hosting options and deploying the Social networking application.
* We plan to implement the pipeline which automates the testing, build phase in the pipeline.
* We will be Monitoring the Social networking application which will include diving deep into DataDog APM. The existing code contains jaeger which acts like a dashboard contains the log data. We aim to export this data into DataDog and create dashboard for monitoring the micro services, overall application health check, CI/CD and perform tests.


## 4. Solution Concept


## 5. Acceptance criteria

* Application with atleast two microservices
* Well working CI/CD pipeline configured using Terraform.
* Code committed to the repo should test, build, and deploy
* Should include end to end testing either using Datadog Synthetic tests, or Selenium
* Using terraform, ingesting OpenTelemetry traces with the collector
* Create monitoring dashboard in Datadog.

## 6. Release Planning

Detailed user stories and plans are on the Trello board: https://trello.com/b/4EbylOXI/example-trello-board-for-moc-ui

Release #1 (due by Week 5): 

* POC on how to get data from Jaeger to Datadog.
* POC on which tool to use for CI/CD and how to use it.
* Exploring the exisiting Social Network Application and deciding on atleast two microservices to be used in the project.

