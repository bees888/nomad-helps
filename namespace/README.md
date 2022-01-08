# nomad namespace -help

Usage: nomad namespace <subcommand> [options] [args]

This command groups subcommands for interacting with namespaces. Namespaces
allow jobs and their associated objects to be segmented from each other and
other users of the cluster. For a full guide on namespaces see:
https://learn.hashicorp.com/tutorials/nomad/namespaces

Create or update a namespace:

      $ nomad namespace apply -description "My new namespace" <name>

List namespaces:

      $ nomad namespace list

View the status of a namespace:

      $ nomad namespace status <name>

Please see the individual subcommand help for detailed usage information.

Subcommands:  
apply Create or update a namespace  
delete Delete a namespace  
inspect Inspect a namespace  
list List namespaces  
status Display a namespace's status
