# nomad server

Usage: nomad server <subcommand> [options] [args]

This command groups subcommands for interacting with Nomad servers. Users can
list Servers, join a server to the cluster, and force leave a server.

List Nomad servers:

      $ nomad server members

Join a new server to another:

      $ nomad server join "IP:Port"

Force a server to leave:

      $ nomad server force-leave <name>

Please see the individual subcommand help for detailed usage information.

Subcommands:  
force-leave Force a server into the 'left' state  
join Join server nodes together  
members Display a list of known servers and their status
