# IAM Access Analyzer

- Enables per region
- Supports Organizations
- Discovers cross-account access permissions
- Support both identity and resource permissions, like S3 bucket policies.

# AWS Config

- Enables per region
- Supports Organizations
- Not just a security service, it's designed around compliance.
- It can identify non-compliant resources.
- It has the ability to identify a resource and pull up all of the resources that are associated with it.
- Visualize resource changes as a timeline.
- Create rules to identify non-compliant resources.
- Support proactive and reactive mitigation. Proactive mitigation only works for resources configured using CloudFormation. 

# AWS Macie

- Designed around data classification and identifying improper permissions.
- Enables per region.
- Supports Organizations.
- Classifies data.
- Identifies sensitive data according to data privacy frameworks.
- Analyze data access permissions.
- Generates findings and organize by severity or bucket.

# Guard Duty

- Machine learning based service that establishes a normal behavior baseline in different areas of your account so that it can generate findings based on anomalies.
-  Enables per region
- Supports Organizations
- Protects AWS workloads, credentials and data.
- Ingests from several event and data sources. **Three are default** and the rest you have to opt into. Everything else besides these three is opt-in.
	- CloudTrail logs. Regardless of whether a trail exists or not. It looks at the 90 day history you have available in the region.
	- VPC Flow logs. Regardless of whether they're enabled or not.
	- VPC DNS logs. Regardless of whether resolver endpoints or Route53 firewall is configured.
- S3 data and event logs pairs well with Macie.
- EKS workload audit log and runtime monitoring.
- Malware protection on EBS volumes (attached to EC2 instances). It does not scan existing volumes, it creates a snapshot of an existing volume and scans that instead.
- Aurora analysis and profiling of login activity.
- Lambda function network activity if they are deployed in a VPC.
- EC2 runtime monitoring and runtime for ECS.

# Inspector

- Designed around vulnerability management for compute resources in AWS.
- Enables per region.
- Supports Organizations.
- Discovers and scans AWS workloads for software vulnerabilites.
- It is not ML based but is really strict in the rules it looks at.
- Also scans for unintended network exposure.
- Different scans that are available.
	- Standard inspection only scans OS packages.
	- Deep inspection looks at programming language packages.
	- ECR container images. Not running containers.
	- Lambda function standard scan.
	- Lambda function code scan.
- To perform a scan the following is needed.
	- To scan EC2 instances, Inspector requires the Systems Manager Agent on each instance.
	- Each instance also requires and IAM role. An Instance profile with permissions to be able to perform these actions.
	- It requires network access. 
	- The communication is always initiated from the EC2 instances and never from the AWS services.