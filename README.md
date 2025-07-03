# AWS Beanstalk Example Node Js app with Splunk instrumentation and Splunk Otel Collector installation.

This is a Node Js app provided by [AWS](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/nodejs-quickstart.html) with added [Zero code instrumentation](https://help.splunk.com/en/splunk-observability-cloud/manage-data/available-data-sources/supported-integrations-in-splunk-observability-cloud/apm-instrumentation/instrument-a-node.js-application/instrument-your-node.js-application). The deployment also includes installation of the [Splunk OTel Collector](https://github.com/signalfx/splunk-otel-collector) as a ebextension.  

## Installation

See [QuickStart: Deploy a Node.js application to Elastic Beanstalk](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/nodejs-quickstart.html)

```bash
~/eb-nodejs$ eb init -p node.js nodejs-tutorial --region us-east-2
```

## Configurations 
See 00-environment.config for environment properties needed by the Splunk OTel Collector 

### --- Zero-Code Instrumentation Settings ---
    OTEL_SERVICE_NAME: "eb-nodejs-app" 
    OTEL_EXPORTER_OTLP_ENDPOINT: "http://localhost:4318"
    OTEL_RESOURCE_ATTRIBUTES: 'deployment.environment=dev,service.version=1'
    OTEL_EXPORTER_OTLP_PROTOCOL: "http/protobuf"

### --- Splunk OTel Collector Configurations ---- 
You will need to configure or manually add these configurations to your EB environment.

    SPLUNK_ACCESS_TOKEN: ""
    SPLUNK_REALM: ""
    SPLUNK_HEC_URL: "https://<ip>:8088/services/collector/event"
    SPLUNK_HEC_TOKEN: ""