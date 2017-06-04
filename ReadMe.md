# Web Developer Exercise - Webhooks

## Introduction

For this exercise you need to build a webhook relay application using ASP.Net. The Rackspace Monitoring agent on our cloud platform can trigger a webhook in the event of an issue with our Elasticsearch cluster. e.g. *Cluster status is RED*. We'd like to publish the cluster status to our Slack channel so the team can be notified. Since the Rackspace Monitoring webhook format is different to Slack's format, it cannot post directly and you need to build a relay.

## Objective

Using the WebHookRelay solution as a starting point, build a web application which can receive an incoming webhook in the Rackspace Monitoring format, extract the necessary information from the payload and trigger a Slack webhook accordingly.

You're welcome to implement this using an ASP.Net technology of your choice (Web Forms, MVC, Web API, etc.). Pick whichever you think is best.

### Receiver

The web application should operate as a webhook receiver with a URL endpoint capable of accepting a JSON payload.

Please listen on `http://localhost:88/slack-relay`

The payload format it should expect is defined in the [Rackspace Monitoring API docs](https://developer.rackspace.com/docs/rackspace-monitoring/v1/api-reference/notification-type-operations/#webhook-notification-type). We've included a sample in RackspaceSample.json, which includes the Elasticsearch cluster status.

For testing, you can try POSTing this to your receiver using cUrl or Fiddler, etc.

`curl -X POST -d "@RackspaceSample.json" http://localhost:88/slack-relay`

In the payload, these fields are relevant

- details.timestamp
- details.state
- details.status
- entity.label
- check.label
- alarm.label

### Publisher

Upon receipt of an incoming webhook, the application should process the payload and forward relevant information to Slack's inbound webhook endpoint.

For the sake of testing, please make this endpoint configurable and assume it is `http://localhost:90/slack`

Please post a suitable message to the Slack channel, notifying the team of the current Elasticsearch cluster status. Slack's webhook format is defined in the [Slack API docs](https://api.slack.com/incoming-webhooks).

## Assessment

We'll carry out an automated test on your solution, followed by a manual code review. Please treat this as you would a normal programming task, and adhere to your normal coding standards.



`