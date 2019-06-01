# Prepare your development environment

## 1. Create Cloud9 instance for development

1.1\. Open the AWS Cloud9 console at https://console.aws.amazon.com/cloud9/.

1.2\. Click on **Create environment**.

![Cloud9 Create environment](images/cloud9-create.png)

1.3\. For the **Name** type `MyDevEnv`, and choose **Next step**.

![Cloud9 name environment](images/cloud9-name.png)

1.4\. For the **Environment settings** use the default values.

![Cloud9 Default Values](images/cloud9-default-settings.png)

1.5\. For the **Network settings (advanced)**, expand the section and select your **VPC ID** and **Public Subnet 01** and choose **Next step**. Identify your Subnet Id going back to your subnets list https://console.aws.amazon.com/vpc/home?region=us-east-1#subnets.

![Cloud9 Network Settings](images/cloud9-network-settings.png)

1.6\. For the **Review** page click on **Create environment**.

1.7\. Wait a few seconds until your development environment is ready, you will see the following screen.

![Cloud9 Env](images/cloud9-env.png)

## 2. Install requirements

2.1\. Inside the Cloud9 environment, in the **bash** terminal, execute the following command to clone the project repository.

``` bash
git clone https://github.com/aurbac/nodejs-back-and-angular-front.git
```

2.2\. Update the Node.js to version 10 required by Angular.

``` bash
nvm i v10
```

2.3\. Install the Angular CLI globally.

``` bash
npm install -g @angular/cli
```

2.4\. The execution of the following commands make sure that service linked roles exist for Load Balancers and ECS, if they do not exist they are created.

``` bash
aws iam get-role --role-name "AWSServiceRoleForElasticLoadBalancing" || aws iam create-service-linked-role --aws-service-name "elasticloadbalancing.amazonaws.com"
aws iam get-role --role-name "AWSServiceRoleForECS" || aws iam create-service-linked-role --aws-service-name "ecs.amazonaws.com"
```