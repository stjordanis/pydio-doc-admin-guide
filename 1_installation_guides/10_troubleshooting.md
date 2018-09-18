In this section, we gather known installation problems with strategies to fix them.

## Various Information

### Files location

On a linux-like system, using the `pydio` user, you will find the Pydio files at the following locations:

- **Configuration**: `/home/pydio/.config/pydio/cells/pydio.json`
- **Logs**: `/home/pydio/.config/pydio/cells/logs`.
- **Data**: `/home/pydio/.config/pydio/cells/data`

## Installation issues

### Progress freeses during browser install

- No progress appears during install

During the installation process, if there is no progress bar but the console is still showing some activities; it is OK. A manual refresh at the end of the install will load the login page.

[:image-popup:1_installation_guides/troubleshooting_install_no_progress.png]

- The wizard is stucked at the end of the install

After the install, if the page does not refresh automatically in ssl self-signed mode it is OK.  
A manual refresh will load the login page.

## Networking issues

### No private address

_ You got this kind of error: `ERROR   nats    Could not run   {“error”: “No private IP address found, and explicit IP not provided”}`_

This typically happens on small VPS that are hosted in the cloud and don't have a private address by default.

The simplest way is to create an alias on the network interface with a 10.0.X address.
For example, if the main interface is eth0, just add the following in the `/etc/network/interface` file.

```conf
auto eth0:1
allow-hotplug eth0:1
iface eth0:1 inet static
address 10.0.0.1
netmask 255.255.255.0
```

Then restart networking services.

### Unable to bind port 443

_You have configured the bind URL with port 443 and enable redirection of port 80. You get an error page "Unable to connect" when you try to connect_.

Check the error log, if you sse such an error:

```sh
2018-05-21T10:55:57.532+0200   ERROR   pydio.grpc.gateway.proxy   Could not run   {"error": "listen tcp :443: bind: permission denied"}
```

You probably did not give permission to the `cells` binary file to use reserved ports. To fix this:

```sh
sudo setcap 'cap_net_bind_service=+ep' cells
```