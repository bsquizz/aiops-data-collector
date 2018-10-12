# AI-Ops data collector

Fetch data from S3 bucket and pass it to AI service

## OpenShift Deployment

Please consult [`aiops-deploy` repository](https://github.com/tumido/aiops-deploy) for deployment scheme.

# Local build

If you would like to deploy the clustering service locally, you can build the container using [S2I](https://github.com/openshift/source-to-image)

```
❯ s2i build -c . centos/python-36-centos7 aiops-data-collector
```

For convenience you can store your desired environment variables in a separate file

```
❯ cat << EOT >> env.list
AI_MICROSERVICE_URL=<AI_SERVICE_HTTP_ENDPOINT>
EOT
```

And then run it as a Docker container

```
❯ docker run --env-file env.list -it aiops-data-collector
```

# Related projects

- [AI service](https://github.com/RedHatInsights/aicoe-insights-clustering)
