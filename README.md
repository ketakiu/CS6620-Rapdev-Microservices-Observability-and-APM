# CS6620-Rapdev-Microservices-Observability-and-APM

** **
## 1. Vision and Goals Of The Project:

Goal of this project is to establish a CI/CD pipeline for Social Network microservice application which automates testing, integration, deployment, and delivery.
High level Goals of this project are:
* Monitoring microservices, CI/CD, and develop a dashboard using Datadog APM and Jaeger

* Write test cases for the existing Social Network Microservices using Datadog Synthetic Monitoring.


## 2. Users/Personas Of The Project

Social Network-monitoring module will be used by the administrators of cloud services, DEV-ops engineers, network engineers including researchers from BU, NU, MIT, HU and UMass, MGHPCC contributing companies, Commonwealth companies and government institutions, and paying users. 

It does not target:

* End users using the Social Network application.


## 3. Scope and Features Of The Project:

Social Network Application 

* The scope of the project includes exploring the CI/CD services, hosting options and deploying the Social networking application.
* We plan to implement the pipeline which automates the testing, build phase in the pipeline.
* We will be Monitoring the Social networking application which will include diving deep into DataDog APM. The existing code contains jaeger which acts like a dashboard contains the log data. We aim to export this data into DataDog and create a dashboard for monitoring the microservices, overall application health check, CI/CD and perform tests.


## 4. Solution Concept

Solution Architecture
![alt text](https://github.com/ketakiu/CS6620-Rapdev-Microservices-Observability-and-APM/blob/main/Architecture.jpeg?raw=true)

1. CI/CD Pipeline:

  * We'll be using Jenkins for automated CI/CD pipeline for our Social Network Microservices application.The application will be hosted on AWS EC2 instance.
  There will be two stages for deployment, Developer and Production. Once the changes pass successfully the tests for the Developer stage, these changes are then         deployed to Production. Currently we'll be using AWS EC2's internal instance management but if time permits we will use Kubernetes for the same.
  
  * We'll be writing a Dockerfile for building the Social Network microservices image. 

2. For Ingesting data to datadog for monitoring the application:
Background about the current implementation:
In the current setup we have jaeger which helps in monitoring and tracing data, logs.

Some important terms in the context :

* SPAN:

A span represents a logical unit of work in Jaeger that has an operation name, the start time of the operation, and the duration. Spans may be nested and ordered to model causal relationships

* TRACE: 

A trace is a data/execution path through the system, and can be thought of as a directed acyclic graph of spans.

In our current setup the jaeger agent is present at each container level which collects data packets and send this data to jaeger collector.
The data is then send from the jaeger collector to the Cassandra database.

![image](https://user-images.githubusercontent.com/55074591/134711163-414eb5bb-a3f6-4147-b953-3763816f91a2.png)

* Our solution:
For exporting the logging, trace data into Datadog APM we need to ingest the data using opentelementary traces with collector.There are couple of ways to accomplish this. But we will be needing the OpenTelementary collector as it provides support to various sdks and jaeger is deprecated. The Open telementary collector will use the Datadog exporter to send the trace data to the Datadog APM. Below is an example that we will be following to accomplish the same.

https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/exporter/datadogexporter

3. DataDog Dashboard:
We will be creating dashboard to monitor the application. We havent yet decided what it will be showing. But will try to give an over about the application health.

## 5. Acceptance criteria

* Application with atleast two microservices
* Well working CI/CD pipeline configured using Terraform.
* Code committed to the repo should test, build, and deploy
* Should include end to end testing either using Datadog Synthetic tests, or Selenium
* Using terraform, ingesting OpenTelemetry traces with the collector
* Create monitoring dashboard in Datadog.

## 6. Release Planning

Release #1 (due by Week 5): 

* POC on how to get data from Jaeger to Datadog.
* POC on which tool to use for CI/CD and how to use it.
* Exploring the exisiting Social Network Application and deciding on atleast two microservices to be used in the project.

