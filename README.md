# IAM Cloudformation Challenge
## Coding Challenge Guidelines
This "coding" challenge is intended to assess whether or not you have a basic understanding of fundamental AWS concepts and are able to follow proper Infrastructure-as-Code (IaC) techniques.
* While there is no actual code involved in this, there is a basic understanding of several AWS resources required, an understanding of _JSON_ or _YAML_ syntax, as well as the ability to navigate and understand AWS CloudFormation documentation
* Some aspects of the challenge can be addressed using different approaches, so there are mulitple correct solutions
  * We will also take comments you have left for us into consideration when evaluating your submission
* The final submission must be *CloudFormation compatible JSON or YAML template(s)*, you are free to use whatever means you wish to achieve that
  * Most people are more familiar with _JSON_ than _YAML_ (in general, not just in regards to CloudFormation), but _JSON_ does not support comments where _YAML_ does
* While access to an AWS account is not strictly required, you will likely find it helpful
* If you should choose to test your CloudFormation template in an AWS account, the requirements of this challenge should not require any AWS resources that incur costs
* If there is something you do not have experience with or do not understand, you should be able to research it quickly and easily
* This challenge should take anywhere from 30-120 minutes, depending on your level of domain knowledge

### Evaluation Criteria
Your solution will be evaluated against the following:
* **Functional**
  * Most importantly: Does it work?  Does it deploy successfully?
  * Did it satisfy all requirements in the challenge?
  * Did it meet all restrictions specified in the challenge?
* **Syntax and Formatting**
  * Is it formatted properly so that it can be validated by CloudFormation?  Is it in proper _YAML_ or _JSON_ syntax?
  * Is it readable and well organized?
  * Are there any interesting decisions you made that would benefit from a comment for future, possibly junior, DevOps engineers?  Were there any issues you faced or open items left to do that were included as comments?
* **Efficiency**
  * Is the template as streamlined as it can be?
  * Does the template make the best use of any predefined resources provided by AWS?
  * Are Cloudformation Parameters used where appropriate?
  * Did you determine that it was more efficient or otherwise advantageous to split this challenge into mulitple templates?  Why?
* **Maintainability**
  * Are there any decisions made that would require complex migrations to update the template?
  * If there are any parameters, and one of them needs to be changed, is the impact of that change kept to a minimum?  (It is understood that not all effects of parameter changes can be be fully eliminated)
  * Do you use any cross-stack exports/imports that would make upgrades a challenge?  These challenges are sometimes unavoidable but it's important to recognize what they are.

The challenge is not strictly pass or fail and there are multiple correct ways to address the challenge.  Please do your best to complete it and **whatever you submit will be evaluated, even if it is incomplete**.

## The Challenge
An Engineering team has recently gotten approval to have limited access to a sensitive AWS account.  In order to ensure that we are following best practices to manage what they have access to, we want to manage this access via Cloudformation.  It is up to you to decide the details of how to set up the access.
* There will be _multiple team members_ that need access, and there may be additional team members in the future that must be added or removed
  * You do not need to set up IAM accounts for each person in this exercise
* They require _ReadOnly_ access to all resources of the following services:
  * S3
  * CodePipeline
  * CloudFormation
  * CloudWatch Logs

In addition to the Engineers themselves needing access, they will need to be able to set up _cross-account access for an application_ which they are working on.  This application has the following requirements:
* The application is going to be housed in _another AWS account_, with an account ID that is currently unknown but will be known when the stack is being deployed
* The application will be passing an _External ID_ for extra security, but that value is currently unknown and may change over time, but will be known when the stack is being deployed or updated
* The application will need _ReadOnly_ access to all S3 resources
* The application will need to be able to _Read_ from and _Put_ to a Kinesis stream, but should not have any further Kinesis access
  * The Kinesis stream name will be variable depending on where this template is being deployed, exact values are currently unknown but will be known when stack is being deployed
  * It will be in the same account and region that the template is being deployed to

All of the above will need to be deployed to not only the sensitive account, but also to one or more Dev environments to provide equivalent access for Dev and QA testing, so please be sure the template is as portable as possible.
## Useful Links
* [AWS Cloudformation Resource and Property Types reference](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-template-resource-type-ref.html)
* [AWS CLI Cloudformation Reference](https://docs.aws.amazon.com/cli/latest/reference/cloudformation/index.html)
* [AWS CLI IAM Reference](https://docs.aws.amazon.com/cli/latest/reference/iam/)
### Tips
* If you're having trouble with _YAML_ Syntax and are more comfortable with _JSON_, there are ways to convert between the two
  * This may help with syntax/formatting but it _does_ come with some issues due to AWS naming convention capitalization inconsistencies between the two
* While the challenge involves a second account, there should not be anything stopping you from testing your solution using a single AWS account
* If you are new to any aspect of this challenge (IAM, CloudFormation, YAML, etc.), it is highly recommended that you develop iteratively and test along the way to ensure you don't introduce regressions

## Submission via CodeSubmit
Please organize, design, test and document your code as if it were going into Production - then push your changes to the `master` branch.

All the best,

The Uplift DevOps team
