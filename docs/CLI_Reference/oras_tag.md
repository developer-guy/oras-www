## oras tag

Tag a manifest in the remote registry.

```bash
oras tag [flags] <name>{:<tag>|@<digest>} <new_tag> [...]
```

## Examples

Tag the manifest 'v1.0.1' in 'localhost:5000/hello' to 'v1.0.2':

```bash
oras tag localhost:5000/hello:v1.0.1 v1.0.2
```

Tag the manifest with digest sha256:9463e0d192846bc994279417b50114606712d516aab45f4d8b31cbc6e46aad71 to 'v1.0.2':

```bash
oras tag localhost:5000/hello@sha256:9463e0d192846bc994279417b50114606712d516aab45f4d8b31cbc6e46aad71 v1.0.2
```

Tag the manifest 'v1.0.1' in 'localhost:5000/hello' to 'v1.0.2', 'latest':

```bash
oras tag localhost:5000/hello:v1.0.1 v1.0.2 latest
```

Tag the manifest 'v1.0.1' in 'localhost:5000/hello' to 'v1.0.1', 'v1.0.2', 'latest' with concurrency level tuned:

```bash
oras tag --concurrency 1 localhost:5000/hello:v1.0.1 v1.0.2 latest
```

Tag the manifest 'v1.0.1' to 'v1.0.2' in an OCI layout folder 'layout-dir':

```bash
oras tag layout-dir:v1.0.1 v1.0.2
```

## Options

```
      --ca-file string                             server certificate authority file for the remote registry
      --concurrency int                            concurrency level (default 5)
  -d, --debug                                      debug mode
  -H, --header stringArray                         add custom headers to requests
  -h, --help                                       help for tag
      --insecure                                   allow connections to SSL registry without certs
      --oci-layout                                 set target as an OCI image layout
  -p, --password string                            registry password or identity token
      --password-stdin                             read password or identity token from stdin
      --plain-http                                 allow insecure connections to registry without SSL check
      --registry-config path                       path of the authentication file for registry
      --resolve host:port:address[:address_port]   customized DNS for registry, formatted in host:port:address[:address_port]
  -u, --username string                            registry username
  -v, --verbose                                    verbose output
```
