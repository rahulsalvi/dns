# dns
My DNS setup. It's basically just technitium accessible over tailscale with a setup script.

## Running
```
make start
# follow the prompts
# you will need an oauth client ID and secret from tailscale
```

### Additional Config
Get the address of the new node with
```
source .env && tailscale ip $NAME
```
Connect to the node at http://<TAILSCALE_IP>:5380

Change the following settings:

 - Settings->Recursion->Randomize Name->Turn OFF
 - Settings->Recursion->NS Revalidation->Turn ON
 - Settings->Blocking->Quick Add->Whichever lists you want
 - Settings->DHCP->Disable anything that might be there

Install the following apps:
 - Query Logs (Sqlite)

### Configure clients to use this server
Use https://login.tailscale.com/admin/dns

## Updating
```
make update
# follow the prompts
# you will need an oauth client ID and secret from tailscale
```

## Stopping
```sh
# bring down containers
make down
# (optional) clean up all resources
# WARNING: this will prune docker volumes that aren't being used
make clean
```
