# oras manifest fetch-config

Fetch the config of a manifest from a remote registry.

```bash
oras manifest fetch-config [flags] <name>{:<tag>|@<digest>}
```

## Examples

Fetch the config:

```bash
oras manifest fetch-config localhost:5000/hello:v1
```

Fetch the config of certain platform:

```bash
oras manifest fetch-config --platform 'linux/arm/v5' localhost:5000/hello:v1
```

Fetch and print the prettified config:

```bash
oras manifest fetch-config --pretty localhost:5000/hello:v1
```

Fetch the config and save it to a local file:

```bash
oras manifest fetch-config --output config.json localhost:5000/hello:v1
```

Fetch the descriptor of the config:

```bash
oras manifest fetch-config --descriptor localhost:5000/hello:v1
```

Fetch and print the prettified descriptor of the config:

```bash
oras manifest fetch-config --descriptor --pretty localhost:5000/hello:v1
```


## Options

```
      --ca-file string                              server certificate authority file for the remote registry
  -d, --debug                                       debug mode
      --descriptor                                  output the descriptor
  -H, --header stringArray                          add custom headers to requests
  -h, --help                                        help for fetch
      --insecure                                    allow connections to SSL registry without certs
      --media-type strings                          accepted media types
      --oci-layout                                  set target as an OCI image layout
  -o, --output path                                 file path to write the fetched manifest to, use - for stdout
  -p, --password string                             registry password or identity token
      --password-stdin                              read password or identity token from stdin
      --plain-http                                  allow insecure connections to registry without SSL check
      --platform os[/arch][/variant][:os_version]   request platform in the form of os[/arch][/variant][:os_version]
      --pretty                                      prettify JSON objects printed to stdout
      --registry-config path                        path of the authentication file for registry
      --resolve host:port:address[:address_port]    customized DNS for registry, formatted in host:port:address[:address_port]
  -u, --username string                             registry username
  -v, --verbose                                     verbose output
```