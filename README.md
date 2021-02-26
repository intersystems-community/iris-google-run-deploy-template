## iris-google-run-deploy-template
This is a template to deploy InterSystems IRIS solution to Google Kubernetes Engine.
The template uses Github Actions and Google Cloud Run

## how it works
The worlfow deployes the IRIS with sample cls and with a static frontend with every push to the master branch.
The demo site is [available here](https://deploy.contest.community.intersystems.com/deploy/page17617906.html).

## How to use it
Take the [workflow file](https://github.com/intersystems-community/iris-google-run-deploy-template/blob/master/.github/workflows/build-push-gcr.yaml) to your repository
Change these lines to your options:
```
IMAGE_NAME:   iris-google-run-demo
SERVICE:      deploy-demo
DOMAIN_NAME:  deploy.contest.community.intersystems.com
```
Note, that IMAGE_NAME could be any name for the docker image of your app
SERVICE can be anything, but different from this file
and DOMAIN_NAME could be any 5-level dns name before contest.community.intersystems.com

Also, you need to request the service key to access the GCP cluster for deployemnt your app. Do it in the [discord](https://discord.gg/dzzPDvY) in the Open Exchange channel.
Add the Secret to your Github Repository in [Settings](https://github.com/intersystems-community/iris-google-run-deploy-template/settings)/Secrets section with SERVICE_ACCOUNT_KEY name and put the JSON key there.

After that your solution will be deployed into yourname.contest.community.intersystems.com with every push to master automatically.

You can check the deployment status in the [Actions](https://github.com/intersystems-community/iris-google-run-deploy-template/actions) section of your repository.

## Development 

Clone/git pull the repo into any local directory

```
$ git clone https://github.com/intersystems-community/objectscript-docker-template.git
```

Open the terminal in this directory and run:

```
$ docker-compose build
```

3. Run the IRIS container with your project:

```
$ docker-compose up -d
```

## How to start coding
This repository is ready to code in VSCode with ObjectScript plugin.
Install [VSCode](https://code.visualstudio.com/), [Docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker) and [ObjectScript](https://marketplace.visualstudio.com/items?itemName=daimor.vscode-objectscript) plugin and open the folder in VSCode.
Open /src/cls/PackageSample/ObjectScript.cls class and try to make changes - it will be compiled in running IRIS docker container.
![docker_compose](https://user-images.githubusercontent.com/2781759/76656929-0f2e5700-6547-11ea-9cc9-486a5641c51d.gif)

Feel free to delete PackageSample folder and place your ObjectScript classes in a form
/src/Package/Classname.cls
[Read more about folder setup for InterSystems ObjectScript](https://community.intersystems.com/post/simplified-objectscript-source-folder-structure-package-manager)

The script in Installer.cls will import everything you place under /src into IRIS.

### .vscode/settings.json

Settings file to let you immedietly code in VSCode with [VSCode ObjectScript plugin](https://marketplace.visualstudio.com/items?itemName=daimor.vscode-objectscript))

### .vscode/launch.json
Config file if you want to debug with VSCode ObjectScript

[Read about all the files in this artilce](https://community.intersystems.com/post/dockerfile-and-friends-or-how-run-and-collaborate-objectscript-projects-intersystems-iris)
