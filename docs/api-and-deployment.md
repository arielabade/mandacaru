# API and Deployment Guide

## Integration Model

Project delivery material describes an API that accepts PDF documents and returns structured records. The API-oriented design is intended for external systems that need to automate document processing instead of using the web interface.

The conceptual exchange is:

```text
Client system
  -> PDF upload request
  -> Mandacaru validation and extraction pipeline
  -> structured response
```

The exact endpoint, authentication policy, and deployment address depend on the target environment and must be configured by the deployment owner.

## Application Deployment

The documented web deployment uses:

- A managed runtime compatible with the application.
- A web interface service.
- An environment containing the application dependencies.
- A supported language-model provider configured through a secret manager or protected environment configuration.
- A packaged deployment mechanism, when required by the target environment.

The web service port and network binding depend on the target environment. The deployment should bind the service to the host interface required by that environment and protect model credentials from source control.

## Configuration and Security

Model credentials must be supplied through protected environment configuration. Secret values must never be committed to the repository, embedded in documentation, or included in screenshots and logs.

Production deployments should also define file-size limits, request timeouts, logging retention, access control, and resource limits appropriate to the document collection being processed.

## Operational Considerations

Processing time depends on document size, number of files, extraction model, and available compute. Horizontal scaling is a deployment responsibility and should be evaluated with representative documents and concurrency tests before being treated as a production guarantee.
