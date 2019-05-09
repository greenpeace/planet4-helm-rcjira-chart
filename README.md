# A helm chart for the RocketChat-Jira integration

This repository impelmements a helm chart that deploys the [RocketChat-Jira integration of Gustavkar](https://github.com/gustavkarlsson/rocketchat-jira-trigger)

Prerequisites: That you run the RocketChat on the same cluster, on the same namespace
## Instructions:

- Following the instructions on the [original repo](https://github.com/gustavkarlsson/rocketchat-jira-trigger#configuration-file) create a config.toml file
with the following data:
```
[jira]
uri = "https://jira.mycompany.com"
username = "someuser"
password = "somepassword"
```
- Base encode it using the following command: 
```
openssl enc -base64 < config.toml
```
- Copy the output
- Create a file called `values.yaml` and include the following line
```
configtoml: WHAT_YOU_COPIED_BEFORE
```
replacing the `WHAT_YOU_COPIED_BEFORE` with the outcome of the command you run on the previous step

- Deploy your chart in the same namespace as your RocketChat like that:
```
helm install --name rcjira --namespace rocketchat -f values.yaml https://github.com/greenpeace/planet4-helm-rcjira-chart
```
(Where `--namespace rocketchat` you should use your own namespace )
