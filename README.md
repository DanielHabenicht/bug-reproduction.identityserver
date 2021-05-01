# Reproduction of [5235](https://github.com/IdentityServer/IdentityServer4/issues/5235)

1. `docker compose up --build` 

Navigate to [http://localhost:8000](http://localhost:8000)

To fix the error add this to [`appsettings.json`](./WebApplication1/Server/appsettings.json) `"IdentityServer"` section
```json
 "Key": {
      "Type": "Development"
    }
```

Thats just for showing that the error goes away by specifiyng a `Key` of course you would set them in production as described here: https://docs.microsoft.com/en-us/aspnet/core/security/authentication/identity-api-authorization?view=aspnetcore-5.0#example-deploy-to-a-non-azure-web-hosting-provider