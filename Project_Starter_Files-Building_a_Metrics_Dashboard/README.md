**Note:** For the screenshots, you can store all of your answer images in the `answer-img` directory.

## Verify the monitoring installation

*TODO:* run `kubectl` command to show the running pods and services for all components. Take a screenshot of the output and include it here to verify the installation

![monitoring_svc_pods_screenshot](answer-img/getpodssvcPrometheus.png)

![observability_svc_pods_screenshot](answer-img/getpodssvcobservability.png)

## Setup the Jaeger and Prometheus source
*TODO:* Expose Grafana to the internet and then setup Prometheus as a data source. Provide a screenshot of the home page after logging into Grafana.

![grafana login](answer-img/grafanalogin.png)

![prometheus data source](answer-img/grafanadatasource.png)


## Create a Basic Dashboard
*TODO:* Create a dashboard in Grafana that shows Prometheus as a source. Take a screenshot and include it here.

![create dashboard](answer-img/grafanacreatedashboard.png)

## Describe SLO/SLI
*TODO:* Describe, in your own words, what the SLIs are, based on an SLO of *monthly uptime* and *request response time*.

```
SLO - The end goal of a standard level of performance in a measurable period of time for e.g. 99.5% server uptime in a month

SLI - A Service-Level Indicator (SLI) is a specific metric used to measure the performance of a service.
Measuring the objective we set in SLO measurable.  for e.g. number of server error causing unplanned reboot.

```

## Creating SLI metrics.
*TODO:* It is important to know why we want to measure certain metrics for our customer. Describe in detail 5 metrics to measure these SLIs. 

```
- The SLO will be latency. The SLI will be the response time of requests.
- The SLO will be Failure rate. The SLI for that will be the amount of failures in a unit of time - Error rate.
- The SLO will be uptime. The SLI for that will be time a service is active - Availability.
- The SLO will be Network capcity. The SLI indicates the average bandwidth in a specified period of time.
- The SLO will be Resource capcity. The SLI for that will be the amount of CPU and RAM usage.
- Latency
- Throughput

```

## Create a Dashboard to measure our SLIs
*TODO:* Create a dashboard to measure the uptime of the frontend and backend services We will also want to measure to measure 40x and 50x errors. Create a dashboard that show these values over a 24 hour period and take a screenshot.

![dashboardforsli](answer-img/dashboardsli.png)

## Tracing our Flask App
*TODO:*  We will create a Jaeger span to measure the processes on the backend. Once you fill in the span, provide a screenshot of it here. Also provide a (screenshot) sample Python file containing a trace and span code used to perform Jaeger traces on the backend service.

![jaegar flaskapp](answer-img/jaeger_flaskapp.png)

![flaskapp](answer-img/flaskapp.png)

## Jaeger in Dashboards
*TODO:* Now that the trace is running, let's add the metric to our current Grafana dashboard. Once this is completed, provide a screenshot of it here.

![jaegergrafana](answer-img/jaegergrafana.png)


## Report Error
*TODO:* Using the template below, write a trouble ticket for the developers, to explain the errors that you are seeing (400, 500, latency) and to let them know the file that is causing the issue also include a screenshot of the tracer span to demonstrate how we can user a tracer to locate errors easily.

TROUBLE TICKET

Name: Error 500 while trying to visit /trace

Date: 29th September 2023 , 21:33

Subject: Trial service route /trace showing internal error 500

Affected Area: Trial service

Severity: High Severity

Description: Accessing /trace route in trial service get error 500.

![jaegar trace error](answer-img/trialserviceerror.png)

![Alt text](answer-img/trialserviceerror_analysis.png)

## Creating SLIs and SLOs
*TODO:* We want to create an SLO guaranteeing that our application has a 99.95% uptime per month. Name four SLIs that you would use to measure the success of this SLO.

- Resource consumption - CPU and memory usage
- Service availability - Backend/Frontend availability
- Response error occurence - HTTP 4xx and 5xx status code
- Service reponse - Number of request and Response time


## Building KPIs for our plan
*TODO*: Now that we have our SLIs and SLOs, create a list of 2-3 KPIs to accurately measure these metrics as well as a description of why those KPIs were chosen. We will make a dashboard for this, but first write them down here.

1. Server CPU and memory usage, sufficient resources is provided to the application to minimize potential issue.
    - Server CPU usage
    - Server Memory Usage

2. Mesure the availability of services to ensure it is accessible to the endpoints access.
    - Measure Backend Availability
    - Measure Frontend Availability

3. Track and measure potential non-sucessful request obtained (any status code that is not 200)
    - Error 4xx mesure
    - Error 5xx mesure
    
4. Services Request and response time averagely needed per request.
    - Total requests per minute
    - Average response

## Final Dashboard
*TODO*: Create a Dashboard containing graphs that capture all the metrics of your KPIs and adequately representing your SLIs and SLOs. Include a screenshot of the dashboard here, and write a text description of what graphs are represented in the dashboard.  

![final daskboard](answer-img/finaldashboard.png)

The topmost row of the dashboard show the total CPU usage and Memory usage from the current resources.


Second row left diagram show endpoint request per minute for different route and status return.

Second row right diagram show Backend Availability. 

Third row right shows Frontend availability.

Third row left shows the backend 40X error count over 24 hours period.

Fourth row right shows the frontend 40X error count over 24 hours period.

Last row shows jaeger frontend homepage response time.
