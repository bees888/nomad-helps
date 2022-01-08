# nomad volume

Usage: nomad volume <subcommand> [options]

volume groups commands that interact with volumes.

Register a new volume or update an existing volume:

      $ nomad volume register <input>

Examine the status of a volume:

      $ nomad volume status <id>

Deregister an unused volume:

      $ nomad volume deregister <id>

Detach an unused volume:

      $ nomad volume detach <vol id> <node id>

Create an external volume and register it:

      $ nomad volume create <input>

Delete an external volume and deregister it:

      $ nomad volume delete <external id>

Please see the individual subcommand help for detailed usage information.

Subcommands:  
create Create an external volume  
delete Delete a volume  
deregister Remove a volume  
detach Detach a volume  
init Create an example volume specification file  
register Create or update a volume  
snapshot  
status Display status information about a volume
