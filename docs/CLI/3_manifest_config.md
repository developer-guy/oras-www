# Manifest Config

According to [OCI Image Manifest Specification](https://github.com/opencontainers/image-spec/blob/master/manifest.md#image-manifest-property-descriptions),
the property `config` is required by an image manifest.
Since `oras` does not make use of the configuration object, an empty JSON object `{}` is used by default when pushing, and never being fetched when pulling.

The descriptor of the default configuration object is fixed as follows.

```json
{
    "mediaType": "application/vnd.oci.image.config.v1+json",
    "digest": "sha256:44136fa355b3678a1146ad16f7e8649e94fb4fc21fe77e8310c060f61caaff8a",
    "size": 2
}
```

## Customize config

Users can customize the configuration object by the `--manifest-config file[:type]` option. To push a file `hi.txt` with the custom manifest config file `config.json`, run

```
oras push --config config.json localhost:5000/hello:latest hi.txt
```

The media type of the config is set to the default value `application/vnd.unknown.config.v1+json`. 

Similar to the file reference, it is possible to change the media type of the manifest config. To push a file `hi.txt` with the custom manifest config file  `config.json` with the custom media type `application/vnd.oras.config.v1+json`, run

```
oras push --config config.json:application/vnd.oras.config.v1+json localhost:5000/hello:latest hi.txt
```

In addition, it is possible to pass a null device `/dev/null` (`NUL` on Windows) to `oras` for an empty config file.

```
oras push --config /dev/null:application/vnd.oras.config.v1+json localhost:5000/hello:latest hi.txt
```

## Docker behaviors

The config used by `oras` is not a real config.
Therefore, the pushed image cannot be recognized or pulled by `docker` as expected.
In this section, docker behaviors are shown given various configs.

### Empty config file

```
$ oras push --manifest-config /dev/null localhost:5000/hello:latest hi.txt
Uploading a948904f2f0f hi.txt
Pushed localhost:5000/hello:latest
Digest: sha256:34897815cbf060e1d11b4c2938c7476d9326269e2179aef3559ce25af11a9ced
$ docker pull localhost:5000/hello:latest
latest: Pulling from hello
a948904f2f0f: Extracting [==================================================>]      12B/12B
unexpected end of JSON input
```

### Empty JSON object

```
$ cat config.json
{}
$ oras push --config config.json localhost:5000/hello:latest hi.txt
Uploading a948904f2f0f hi.txt
Pushed localhost:5000/hello:latest
Digest: sha256:44d13da4d42a20ceed7ee3411b103a6f82ef02a2eac981d5e3d799c41e3015d7
$ docker pull localhost:5000/hello:latest
latest: Pulling from hello
a948904f2f0f: Pulling fs layer
invalid rootfs in image configuration
```

### Arbitrary OS

```
$ cat config.json
{
    "architecture": "cloud",
    "os": "oras"
}
$ oras push --config config.json localhost:5000/hello:latest hi.txt
Uploading a948904f2f0f hi.txt
Pushed localhost:5000/hello:latest
Digest: sha256:e6428c9cb88505a1859a01f4b7602bdb263d5f65399ef72d3397afd9bfb25b2c
$ docker pull localhost:5000/hello:latest
latest: Pulling from hello
a948904f2f0f: Extracting [==================================================>]      12B/12B
operating system is not supported
```

### Arbitrary config media type

```
$ oras push --artifact-type application/vnd.oras.config.v1+json localhost:5000/hello:latest hi.txt
Uploading a948904f2f0f hi.txt
Pushed localhost:5000/hello:latest
Digest: sha256:5d8ea018049870aab566350660b9a003c646a7f955f9996d35cc0c71bf41b3d0
$ docker pull localhost:5000/hello:latest
Error response from daemon: Encountered remote "application/vnd.oras.config.v1+json"(unknown) when fetching
```

Layers are not pulled in this case. Thus **it is encouraged to specify customized config media type**.

Additionally, the latest version of `dockerd` recognizes OCI manifests and does not verify the OCI config media type.

## Push / Pull config

As mentioned in the beginning of this doc, the manifest config is not used by `oras` and is not worth pulling in most scenarios.
However, it is still possible to push pullable config with the `oras` CLI by leveraging [Manifest Annotations](./4_manifest_annotations.md).

```
$ cat config.json
{
    "foo": "bar"
}
$ cat annotations.json
{
    "$config": {
        "org.opencontainers.image.title": "config.json"
    }
}
$ oras push --config config.json --annotation-file annotations.json localhost:5000/hello:latest hi.txt
Uploading a948904f2f0f hi.txt
Uploading 57f840b6073c config.json
Pushed localhost:5000/hello:latest
Digest: sha256:12e3de7e4a65ffc46a6158ac2df07ecc6fd1af8b0109b4c42a90067f7e907f43
$ oras pull -a localhost:5000/hello:latest
Downloaded a948904f2f0f hi.txt
Downloaded 57f840b6073c config.json
Pulled localhost:5000/hello:latest
Digest: sha256:12e3de7e4a65ffc46a6158ac2df07ecc6fd1af8b0109b4c42a90067f7e907f43
```
