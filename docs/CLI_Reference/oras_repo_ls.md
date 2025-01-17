## oras repo ls

List the repositories under the registry.

```bash
oras repo ls [flags] <registry>
```

## Examples

Example - List the repositories under the registry:

```bash
oras repo ls localhost:5000
```

Example - List the repositories under a namespace in the registry:

```bash
oras repo ls localhost:5000/example-namespace
```

Example - List the repositories under the registry that include values lexically after last:

```bash
oras repo ls --last "last_repo" localhost:5000
```

## Options

```bash
      --ca-file string                             server certificate authority file for the remote registry
  -d, --debug                                      debug mode
  -H, --header stringArray                         add custom headers to requests
  -h, --help                                       help for ls
      --insecure                                   allow connections to SSL registry without certs
      --last last                                  start after the repository specified by last
  -p, --password string                            registry password or identity token
      --password-stdin                             read password or identity token from stdin
      --plain-http                                 allow insecure connections to registry without SSL check
      --registry-config path                       path of the authentication file for registry
      --resolve host:port:address[:address_port]   customized DNS for registry, formatted in host:port:address[:address_port]
  -u, --username string                            registry username
  -v, --verbose                                    verbose output
```