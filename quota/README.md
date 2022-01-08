# nomad quota

Usage: nomad quota <subcommand> [options] [args]

This command groups subcommands for interacting with resource quotas. Resource
quotas allow operators to restrict the aggregate resource usage of namespaces.
Users can inspect existing quota specifications, create new quotas, delete and
list existing quotas, and more. For a full guide on resource quotas see:
https://www.nomadproject.io/guides/quotas.html

Examine a quota's status:

      $ nomad quota status <name>

List existing quotas:

      $ nomad quota list

Create a new quota specification:

      $ nomad quota apply <path>

Please see the individual subcommand help for detailed usage information.

Subcommands:  
apply Create or update a quota specification  
delete Delete a quota specification  
init Create an example quota specification file  
inspect Inspect a quota specification  
list List quota specifications  
status Display a quota's status and current usage
