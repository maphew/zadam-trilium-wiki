ETAPI is Trilium's public/external REST API.

The documentation is in OpenAPI format available [here](https://github.com/zadam/trilium/blob/master/src/etapi/etapi.openapi.yaml).

## Authentication

All operations have to be authenticated using a token. You can get this token either from Options -> ETAPI or programatically using the `/auth/login` REST call (see the [spec](https://github.com/zadam/trilium/blob/master/src/etapi/etapi.openapi.yaml)).