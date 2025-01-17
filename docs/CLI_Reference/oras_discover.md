# oras discover

Discover referrers of a manifest in the remote registry.

```bash
oras discover [flags] <name>{:<tag>|@<digest>}
```

## Examples

Discover direct referrers of manifest 'hello:v1' in registry 'localhost:5000':

```bash
oras discover localhost:5000/hello:v1
```

Discover direct referrers via referrers API:

```bash
oras discover --distribution-spec v1.1-referrers-api localhost:5000/hello:v1
```

Discover direct referrers via tag scheme:

```bash
oras discover --distribution-spec v1.1-referrers-tag localhost:5000/hello:v1
```
Discover all the referrers of manifest 'hello:v1' in registry 'localhost:5000', displayed in a tree view:

```bash
oras discover -o tree localhost:5000/hello:v1
```

Discover all the referrers of manifest with annotations, displayed in a tree view:

```bash
oras discover -v -o tree localhost:5000/hello:v1
```

Discover referrers with type 'test-artifact' of manifest 'hello:v1' in registry 'localhost:5000':

```bash
oras discover --artifact-type test-artifact localhost:5000/hello:v1
```

Discover referrers of the manifest tagged 'v1' in an OCI layout folder 'layout-dir':

```bash
oras discover --oci-layout layout-dir:v1
oras discover --oci-layout -v -o tree layout-dir:v1
```

## Options

```
      --artifact-type string                        artifact type
      --ca-file string                              server certificate authority file for the remote registry
  -d, --debug                                       debug mode
      --distribution-spec string                    [Preview] set OCI distribution spec version and API option for target. options: v1.1-referrers-api, v1.1-referrers-tag
  -H, --header stringArray                          add custom headers to requests
  -h, --help                                        help for discover
      --insecure                                    allow connections to SSL registry without certs
      --oci-layout                                  set target as an OCI image layout
  -o, --output string                               format in which to display referrers (table, json, or tree). tree format will also show indirect referrers (default "table")
  -p, --password string                             registry password or identity token
      --password-stdin                              read password or identity token from stdin
      --plain-http                                  allow insecure connections to registry without SSL check
      --platform os[/arch][/variant][:os_version]   request platform in the form of os[/arch][/variant][:os_version]
      --registry-config path                        path of the authentication file for registry
      --resolve host:port:address[:address_port]    customized DNS for registry, formatted in host:port:address[:address_port]
  -u, --username string                             registry username
  -v, --verbose                                     verbose output
```