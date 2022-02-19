ETAPI is Trilium's public/external REST API. It is available since Trilium v0.50.

The documentation is in OpenAPI format, available [here](https://github.com/zadam/trilium/blob/master/src/etapi/etapi.openapi.yaml).

[trilium-py](https://github.com/Nriver/trilium-py) is a third-party Python implementation for ETAPI client, you can use Python to communicate with Trilium.

## Authentication

All operations have to be authenticated using a token. You can get this token either from Options -> ETAPI or programmatically using the `/auth/login` REST call (see the [spec](https://github.com/zadam/trilium/blob/master/src/etapi/etapi.openapi.yaml)).