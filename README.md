# Run nihiluxorg/roon-web-stack with Tailscale

**PLEASE NOTE: this does not currently work!**

A simple docker compose file that runs
(nihiluxorg/roon-web-stack)[https://github.com/nihilux-org/roon-web-stack]
on your Tailscale tailnet, which will connect to a
(Roon appliance)[https://roon.app/en/nucleus] or a
(Roon ROCK server)[https://help.roonlabs.com/portal/en/kb/articles/rock-install-guide]
using its built-in Tailscale service.

## Setup

Copy `.env.sample` to `.env`.

Edit `.env` and change the `TAILSCALE_HOSTNAME` variable to something unique
within your tailnet.

Start up the tailscale container in the foreground:

```
docker compose up tailscale
```

Paste the URL that appears in the logs into a browser and follow the steps to
authorise the tailscale container to connect to your tailnet.

Exit the container then start the stack in the background:

```
docker compose up -d
```

Open your browser and go to `https://<tailscale hostname>.<your tailnet>.ts.net/`
and wait for Tailscale to generate the required certificates. Once the Roon Web Stack
page appears, follow the
(nihiluxorg/roon-web-stack)[https://github.com/nihilux-org/roon-web-stack/blob/main/README.md]
instructions to connect it to your Roon Server.
