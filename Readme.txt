
# Add a new Web application project to this solution file.
		The application should be developed in an ASP.NET technology of your choice (webforms, MVC, WebAPI etc...)

# The Web application should operate as a Web Hook receiver with a URL endpoint capable of accepting a JSON payload 
		Payload format it should expect can be found in the rackspacesample.json file under solution items.
			or reference https://developer.rackspace.com/docs/rackspace-monitoring/v1/api-reference/notification-type-operations/#webhook-notification-type
		
# The application should run under http://localhost:xxxxx/ 
		The endpoint accepting the JSON payload should be /webhook

# The application should also operate as a Web Hook publisher by processing the payload and forwarding relevant information to another (configurable) URL endpoint, http://localhost:yyyyy/slack
		The format of the payload to forward should be in slack format.
		https://api.slack.com/incoming-webhooks
		
		The relevant information includes:
			details.timestamp
			details.state
			details.status
			entity.label
			check.label
			alarm.label

# Development should follow your current practices for development, including if necessary unit tests, code comments etc...