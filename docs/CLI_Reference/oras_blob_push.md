# oras blob push

Push a blob to a remote registry.

```bash
oras blob push [flags] <name>[@digest] <file>
```

## Examples

Push blob "hi.txt":

```bash
oras blob push localhost:5000/hello hi.txt
```

Push blob "hi.txt" with the specific digest:

```bash
oras blob push localhost:5000/hello@sha256:9a201d228ebd966211f7d1131be19f152be428bd373a92071c71d8deaf83b3e5 hi.txt
```

Push blob from stdin with blob size and digest:

```bash
oras blob push --size 12 localhost:5000/hello@sha256:9a201d228ebd966211f7d1131be19f152be428bd373a92071c71d8deaf83b3e5 -
```

Push blob "hi.txt" and output the descriptor:

```bash
oras blob push --descriptor localhost:5000/hello hi.txt
```

Push blob "hi.txt" with the specific returned media type in the descriptor:

```bash
oras blob push --media-type application/vnd.oci.image.config.v1+json --descriptor localhost:5000/hello hi.txt
```

Push blob "hi.txt" and output the prettified descriptor:

```bash
oras blob push --descriptor --pretty localhost:5000/hello hi.txt
```

Push blob without TLS:

```bash
oras blob push --insecure localhost:5000/hello hi.txt
```

Push blob 'hi.txt' into an OCI layout folder 'layout-dir':

```bash
oras blob push --oci-layout layout-dir hi.txt
```

## Options

```
      --ca-file string                             server certificate authority file for the remote registry
  -d, --debug                                      debug mode
      --descriptor                                 output the descriptor
  -H, --header stringArray                         add custom headers to requests
  -h, --help                                       help for push
      --insecure                                   allow connections to SSL registry without certs
      --media-type string                          specify the returned media type in the descriptor if --descriptor is used (default "application/vnd.oci.image.layer.v1.tar")
      --oci-layout                                 set target as an OCI image layout
  -p, --password string                            registry password or identity token
      --password-stdin                             read password or identity token from stdin
      --plain-http                                 allow insecure connections to registry without SSL check
      --pretty                                     prettify JSON objects printed to stdout
      --registry-config path                       path of the authentication file for registry
      --resolve host:port:address[:address_port]   customized DNS for registry, formatted in host:port:address[:address_port]
      --size int                                   provide the blob size (default -1)
  -u, --username string                            registry username
  -v, --verbose                                    verbose output
```
