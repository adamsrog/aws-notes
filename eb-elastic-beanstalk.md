# Elastic Beanstalk

AWS re:Invent 2015 | (DVO201) Scaling Your Web Applications with AWS Elastic Beanstalk - https://www.youtube.com/watch?v=nkj0GXgaRv8

## Elastic Beanstalk vs DIY
* Just need to bring your code, no need to build everything else manually
* Provisions necessary infrastructure resources (load baslances, auto-scaling group, security groups, database, etc)
* Provides unique domain name project.elasticbeanstalk.com
* Supports Java, Node.js, PHP, Docker, .NET, Python, Ruby, Go
* Don't use Beanstalk to spin up RDS database unless its for dev purposes (its lifecycle is tied to the application in Elastic Beanstalk)

## Configuring options
* Don't use 'latest' for versions on dependencies for production servers - specify exact versions.
* Customize application stack using .ebextensions and .config files

## Best Practices
* Pick performance metrics to optimize for (latency, concurrent users, number of web requests, etc).
* Load test the application to understand how auto-scaling will operate
* Configure auto-scaling to optimize for performance metrics (number of instances to add on scale out, breach duration, metric to scale on)
* Turn the back end (RDS) for optimal performance; leave enough headroom for full scale out.
* 100 web server instances hitting one backend will cause problems

## Deployment options
* Rolling deployments are fast (20-60 seconds)
* Rolling deployments rollback is slower because previous application must be redeployed. Possibility of state build-up on long-running environments.
* Blue/Green deployments pros: fast rollback because environment running in previous version has not been modified and it ensures no state build up on environments
* Blue/Green cons is that deployments take longer than rolling deployments (2-5 mins) because a new environment must be created

## Logs, Metrics and Alarms
* Enable log rotation to automatically publish logs to S3
* Understand metrics available for your environment and what they mean
* Set up alarms to automatically monitor critical metrics and send notifications when metrics are outside normal operating rages
* Enable Amazon Route 53 health checks and alarms

## Tags
* Make it easy to identify costs belonging to specific resources

AWS re:Invent 2014 | (WEB302) Best Practices for Running WordPress on AWS - https://www.youtube.com/watch?v=kEelxH6dGFY

## Offload static content
* Serve directly from Amazon S3