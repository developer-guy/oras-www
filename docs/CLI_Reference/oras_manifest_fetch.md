## oras manifest fetch

Fetch manifest of the target artifact.

```bash
oras manifest fetch [flags] <name>{:<tag>|@<digest>}
```

## Examples

Fetch raw manifest from a registry:

```bash
oras manifest fetch localhost:5000/hello:v1
```

Fetch the descriptor of a manifest from a registry:

```bash
oras manifest fetch --descriptor localhost:5000/hello:v1
```

Fetch manifest from a registry with specified media type:

```bash
oras manifest fetch --media-type 'application/vnd.oci.image.manifest.v1+json' localhost:5000/hello:v1
```

Fetch manifest from a registry with certain platform:

```bash
oras manifest fetch --platform 'linux/arm/v5' localhost:5000/hello:v1
```

Fetch manifest from a registry with prettified json result:

```bash
oras manifest fetch --pretty localhost:5000/hello:v1
```

Fetch raw manifest from an OCI layout folder 'layout-dir':

```bash
oras manifest fetch --oci-layout layout-dir:v1
```

Fetch raw manifest from an OCI layout archive file 'layout.tar':

```bash
oras manifest fetch --oci-layout layout.tar:v1
```

## Options

```
      --ca-file string                              server certificate authority file for the remote registry
  -d, --debug                                       debug mode
      --descriptor                                  output the descriptor
  -h, --help                                        help for fetch
      --insecure                                    allow connections to SSL registry without certs
      --media-type strings                          accepted media types
      --oci-layout                                  set target as an OCI image layout.
  -o, --output path                                 file path to write the fetched manifest to, use - for stdout
  -p, --password string                             registry password or identity token
      --password-stdin                              read password or identity token from stdin
      --plain-http                                  allow insecure connections to registry without SSL check
      --platform os[/arch][/variant][:os_version]   request platform in the form of os[/arch][/variant][:os_version]
      --pretty                                      prettify JSON objects printed to stdout
      --registry-config path                        path of the authentication file
      --resolve host:port:address                   customized DNS formatted in host:port:address
  -u, --username string                             registry username
  -v, --verbose                                     verbose output
```