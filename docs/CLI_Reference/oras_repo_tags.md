## oras repo tags

Show tags of the target repository.

```bash
oras repo tags [flags] <name>
```

## Examples

Show tags of the target repository:

```bash
oras repo tags localhost:5000/hello
```

Show tags in the target repository with digest-like tags hidden:

```bash
oras repo tags --exclude-digest-tag localhost:5000/hello
```

Show tags of the target repository that include values lexically after last:

```bash
oras repo tags --last "last_tag" localhost:5000/hello
```

Show tags of the target OCI layout folder 'layout-dir':

```bash
oras repo tags --oci-layout layout-dir
```

Show tags of the target OCI layout archive 'layout.tar':

```bash
oras repo tags --oci-layout layout.tar
```

Show tags associated with a particular tagged resource:

```bash
oras repo tags localhost:5000/hello:latest
```

Show tags associated with a digest:

```bash
oras repo tags localhost:5000/hello@sha256:c551125a624189cece9135981621f3f3144564ddabe14b523507bf74c2281d9b
```

## Options

```
      --ca-file string                             server certificate authority file for the remote registry
  -d, --debug                                      debug mode
      --exclude-digest-tags                        [Preview] exclude all digest-like tags such as 'sha256-aaaa...'
  -H, --header stringArray                         add custom headers to requests
  -h, --help                                       help for tags
      --insecure                                   allow connections to SSL registry without certs
      --last last                                  start after the tag specified by last
      --oci-layout                                 set target as an OCI image layout
  -p, --password string                            registry password or identity token
      --password-stdin                             read password or identity token from stdin
      --plain-http                                 allow insecure connections to registry without SSL check
      --registry-config path                       path of the authentication file for registry
      --resolve host:port:address[:address_port]   customized DNS for registry, formatted in host:port:address[:address_port]
  -u, --username string                            registry username
  -v, --verbose                                    verbose output
```