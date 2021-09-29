# CS6620-Rapdev-Microservices-Observability-and-APM

** **

## 1. Vision and Goals Of The Project:

Goal of this project is to establish a CI/CD pipeline for Social Network microservice application which automates
testing, integration, deployment, and delivery.

High level Goals of this project are:

* Develop a CI/CD pipelines using Jenkins, AWS and Docker
* Create a dashboard using Datadog APM and OpenTelemetry, datadog exporter to monitor microservices, CI/CD
* Write test cases for the existing Social Network Microservices using Datadog Synthetic Monitoring.

## 2. Users/Personas Of The Project

Social Network-monitoring module will be used by the administrators of cloud services, DevOps engineers, network
engineers.
It does not target end users of the Social Network application.

## 3. Scope and Features Of The Project:

### Scope:

Our majors goals will be identifying the CICD options, hosting options for the containerized microservices in social networking application. 
In addition to this we will be working with Datadog APM to setup the monitoring for the microservices and creating Dashboard in Datadog.
We will be also doing synthetic testing using DataDog.

### Feature/ Outcomes:

1. Setup a CI/CD pipeline which automates the testing, building, and deployment phase.
2. Setup monitoring in Datadog for the microservices.
3. Create monitoring dashboards in Datadog.
4. Write synthetic test in datadog.


## 4. Solution Concept

### Solution Architecture

![alt text](https://github.com/ketakiu/CS6620-Rapdev-Microservices-Observability-and-APM/blob/main/Architecture.jpeg?raw=true)

1. CI/CD Pipeline:

    * We'll be using Jenkins for automating the CI/CD pipeline for our Social Network Microservices application. The
      application will be hosted on AWS EC2 instance. There will be two stages for deployment, Developer and Production.
      Once the changes successfully pass the tests for the Developer stage, they will be deployed to Production.
      Initially we'll be using AWS EC2's internal instance management but if time permits we will use Kubernetes for the
      same.

    * We'll be writing a Dockerfile for building the Social Network microservices image.

2. For Ingesting data to datadog for monitoring the application:

   Background about the current implementation:

   In the current setup we have Jaeger which helps in monitoring and tracing data, logs.

   Some important terms in the context:

    * SPAN:

      A span represents a logical unit of work in Jaeger that has an operation name, the start time of the operation,
      and the duration. Spans may be nested and ordered to model causal relationships

    * TRACE:

      A trace is a data/execution path through the system, and can be thought of as a directed acyclic graph of spans.

   In our current setup the Jaeger agent is present at each container level which collects data packets and send this
   data to Jaeger collector. The data is then send from the Jaeger collector to the Cassandra database.

   ![image](https://user-images.githubusercontent.com/55074591/134711163-414eb5bb-a3f6-4147-b953-3763816f91a2.png)

    * Our Solution:

      For exporting the logging and tracing data into Datadog APM we need to ingest the data using OpenTelemetary traces
      the with collector. There are couple of ways to accomplish this. But we will be needing the OpenTelemetary
      collector as it provides support to various SDKs and Jaeger is deprecated. The OpenTelemetary collector will use
      the Datadog exporter to send the trace data to the Datadog APM. Below is an example that we will be following to
      accomplish the same.

      * [Datadog Exporter](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/exporter/datadogexporter)
      * [Ingesting opentelemetry collector datadog exporter](https://docs.datadoghq.com/tracing/setup_overview/open_standards/)

3. DataDog Dashboard:

   We will be creating a dashboard to monitor the application. We haven't yet decided what it will be displaying. But
   will try to give an overview about the application's health.

## 5. Acceptance criteria

* Application with atleast two microservices
* Well working CI/CD pipeline configured using Terraform
* Code committed to the repo should be tested, built, and deployed
* Should include end-to-end testing either using Datadog Synthetic tests, or Selenium
* Ingesting OpenTelemetry traces with the collector into Datadog APM.
* Create a monitoring dashboard in Datadog

## 6. Release Planning

Release #1 (due by Week 5):

* POC on how to get export data using opentelementary collector to Datadog.
* POC on which tool to use for CI/CD and how to use it.
* Exploring the existing Social Network Application and deciding on atleast two microservices to be used in the project.
