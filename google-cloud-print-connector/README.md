This image only contains the binaries necessary to run/configure the GCP connector -- you'll want to read https://github.com/google/cloud-print-connector/wiki/Configuration for more information on how to configure and use it.

The easiest way to ensure your container can see your local printers is to use `--net=host` at runtime.

For example:

```console
$ docker run -dit \
	--name google-cloud-print-connector \
	--restart always \
	--net host \
	-v /var/run/dbus:/var/run/dbus:ro \
	-v /path/to/config/dir:/config \
	-w /config \
	--user 1000:1000 \
	tianon/google-cloud-print-connector \
	gcp-cups-connector --log-to-console
```
