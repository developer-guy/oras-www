# oras pull

Pull files from remote registry.

```bash
oras pull [flags] <name>{:<tag>|@<digest>}
```

## Examples

Pull artifact files from a registry:

```bash
oras pull localhost:5000/hello:v1
```

Recursively pulling all files from a registry, including subjects of hello:v1:

```bash
oras pull --include-subject localhost:5000/hello:v1
```

Pull files from an insecure registry:

```bash
oras pull --insecure localhost:5000/hello:v1
```

Pull files from the HTTP registry:

```bash
oras pull --plain-http localhost:5000/hello:v1
```

Pull files from a registry with local cache:

```bash
export ORAS_CACHE=~/.oras/cache
oras pull localhost:5000/hello:v1
```

Pull files from a registry with certain platform:

```bash
oras pull --platform linux/arm/v5 localhost:5000/hello:v1
```

Pull all files with concurrency level tuned:

```bash
oras pull --concurrency 6 localhost:5000/hello:v1
```

Pull artifact files from an OCI layout folder 'layout-dir':

```bash
oras pull --oci-layout layout-dir:v1
```

Pull artifact files from an OCI layout archive 'layout.tar':

```bash
oras pull --oci-layout layout.tar:v1
```

## Options

```
  -T, --allow-path-traversal                        allow storing files out of the output directory
      --ca-file string                              server certificate authority file for the remote registry
      --concurrency int                             concurrency level (default 3)
      --config string                               output manifest config file
  -d, --debug                                       debug mode
  -h, --help                                        help for pull
      --include-subject                             recursively pull the subject of artifacts
      --insecure                                    allow connections to SSL registry without certs
  -k, --keep-old-files                              do not replace existing files when pulling, treat them as errors
      --oci-layout                                  set target as an OCI image layout.
  -o, --output string                               output directory (default ".")
  -p, --password string                             registry password or identity token
      --password-stdin                              read password or identity token from stdin
      --plain-http                                  allow insecure connections to registry without SSL check
      --platform os[/arch][/variant][:os_version]   request platform in the form of os[/arch][/variant][:os_version]
      --registry-config path                        path of the authentication file
      --resolve host:port:address                   customized DNS formatted in host:port:address
  -u, --username string                             registry username
  -v, --verbose                                     verbose output
```