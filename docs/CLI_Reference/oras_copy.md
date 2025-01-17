# oras copy

Copy artifacts from one target to another.

```bash
oras copy [flags] <from>{:<tag>|@<digest>} <to>[:<tag>[,<tag>][...]]
```

## Examples

Copy an artifact between registries:

```bash
oras cp localhost:5000/net-monitor:v1 localhost:6000/net-monitor-copy:v1
```

Download an artifact into an OCI layout folder:

```bash
oras cp --to-oci-layout localhost:5000/net-monitor:v1 ./downloaded:v1
```

Upload an artifact from an OCI layout folder:

```bash
oras cp --from-oci-layout ./to-upload:v1 localhost:5000/net-monitor:v1
```

Upload an artifact from an OCI layout tar archive:

```bash
oras cp --from-oci-layout ./to-upload.tar:v1 localhost:5000/net-monitor:v1
```

Copy an artifact and its referrers:

```bash
oras cp -r localhost:5000/net-monitor:v1 localhost:6000/net-monitor-copy:v1
```

Copy an artifact and referrers using specific methods for the Referrers API:

```bash
oras cp -r --from-distribution-spec v1.1-referrers-api --to-distribution-spec v1.1-referrers-tag \
    localhost:5000/net-monitor:v1 localhost:6000/net-monitor-copy:v1
```

Copy certain platform of an artifact:

```bash
oras cp --platform linux/arm/v5 localhost:5000/net-monitor:v1 localhost:6000/net-monitor-copy:v1
```

Copy an artifact with multiple tags:

```bash
oras cp localhost:5000/net-monitor:v1 localhost:6000/net-monitor-copy:tag1,tag2,tag3
```

Copy an artifact with multiple tags with concurrency tuned:

```bash
oras cp --concurrency 10 localhost:5000/net-monitor:v1 localhost:5000/net-monitor-copy:tag1,tag2,tag3
```

## Options

```
      --concurrency int                                 concurrency level (default 3)
  -d, --debug                                           debug mode
      --from-ca-file string                             server certificate authority file for the remote source registry
      --from-distribution-spec string                   [Preview] set OCI distribution spec version and API option for source target. options: v1.1-referrers-api, v1.1-referrers-tag
      --from-header stringArray                         add custom headers to source requests
      --from-insecure                                   allow connections to source SSL registry without certs
      --from-oci-layout                                 set source target as an OCI image layout
      --from-password string                            source registry password or identity token
      --from-plain-http                                 allow insecure connections to source registry without SSL check
      --from-registry-config path                       path of the authentication file for source registry
      --from-resolve host:port:address[:address_port]   customized DNS for source registry, formatted in host:port:address[:address_port]
      --from-username string                            source registry username
  -h, --help                                            help for cp
      --platform os[/arch][/variant][:os_version]       request platform in the form of os[/arch][/variant][:os_version]
  -r, --recursive                                       [Preview] recursively copy the artifact and its referrer artifacts
      --resolve host:port:address[:address_port]        base DNS rules formatted in host:port:address[:address_port] for --from-resolve and --to-resolve
      --to-ca-file string                               server certificate authority file for the remote destination registry
      --to-distribution-spec string                     [Preview] set OCI distribution spec version and API option for destination target. options: v1.1-referrers-api, v1.1-referrers-tag
      --to-header stringArray                           add custom headers to destination requests
      --to-insecure                                     allow connections to destination SSL registry without certs
      --to-oci-layout                                   set destination target as an OCI image layout
      --to-password string                              destination registry password or identity token
      --to-plain-http                                   allow insecure connections to destination registry without SSL check
      --to-registry-config path                         path of the authentication file for destination registry
      --to-resolve host:port:address[:address_port]     customized DNS for destination registry, formatted in host:port:address[:address_port]
      --to-username string                              destination registry username
  -v, --verbose                                         verbose output
```
