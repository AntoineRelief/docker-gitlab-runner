# Docker Gitlab Runner

This simple project is about running Gitlab pipelines on a server not owned by Gitlab, or on your local machine.

It may be needed to disable shared runners ( provided by Gitlab ). To do that, got to the `Settings -> CI/CD` page of your repository, then to `Runners -> Shared runners` and disable them:

![image](Capture%20d%E2%80%99%C3%A9cran%202022-09-07%20%C3%A0%2016.20.54.png)

## Setup as follows:
- Pull code on target machine
- Setup the container : ``` docker-compose up -d ``` 
- Go to Gitlab, open target project
- Got to `Settings -> CI/CD` page, then `Runners` section
- You should find a registration token below `Specific runners`, copy it
- Register the runner: ``` docker-compose run --rm gitlab-runner register ```
  - Instance URL : https://gitlab.com
  - Registration token: the value you copied
  - Name: identifier, that would tell your machine is the runner, like antoine-macos
  - For other inputs, they should not be needed
- Check if you received successful message
- Try it, by executing one pipeline on Gitlab

## Work with local gitlab-runner
It is possible to enable / disable runners from the settings page of the repository. One way could be to only active your runner any time you need to execute a pipeline with it.

When local execution is needed, make sure that your docker-compose is running.
