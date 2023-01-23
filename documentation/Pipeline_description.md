# Pipeline Description
`CircleCI` is a continuous integration and continuous delivery (CI/CD) platform that allows developers to automate the building, testing, and deployment of their code. A pipeline in CircleCI refers to the set of steps that are executed automatically in response to a code change, such as a commit or a pull request.


## The pipeline is composed of several jobs that are executed in a specific order and can be visualized as a series of steps:

    1- The pipeline starts by installing Node.js and checking out the code from the source control repository.

    2- Next, it runs commands to install the frontend and backend dependencies by using npm run frontend:install and npm run api:install respectively.

    3- Then, it runs commands to lint and build the frontend by using npm run frontend:lint and npm run frontend:build.

    4- In the same way, it runs commands to build the backend by using npm run api:build.

    5- Once the build job is completed, the pipeline then waits for manual approval in order to continue to the deploy job. This is set in the workflows section using a job called hold that requires the build job to be completed.

    6- Once the hold job is completed, the pipeline then continues with the deploy job. This job updates the environment variables for the backend, deploys the backend by using npm run api:deploy, and deploys the frontend by using npm run frontend:deploy.

### It's worth noting that this pipeline is utilizing CircleCI orbs, which are pre-configured packages of CircleCI configuration that can be easily included in a config.yml file. These orbs include circleci/node, circleci/aws-elastic-beanstalk and circleci/aws-cli, which provide basic recipes and reproducible actions to install Node, AWS Elastic Beanstalk, and the AWS CLI, respectively.