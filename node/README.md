# nomad node -help

Usage: nomad node <subcommand> [options] [args]

This command groups subcommands for interacting with nodes. Nodes in Nomad are
agent's that can run submitted workloads. This command can be used to examine
nodes and operate on nodes, such as draining workloads off of them.

Examine the status of a node:

      $ nomad node status <node-id>

Mark a node as ineligible for running workloads. This is useful when the node
is expected to be removed or upgraded so new allocations aren't placed on it:

      $ nomad node eligibility -disable <node-id>

Mark a node to be drained, allowing batch jobs four hours to finish before
forcing them off the node:

      $ nomad node drain -enable -deadline 4h <node-id>

Please see the individual subcommand help for detailed usage information.

Subcommands:  
config View or modify client configuration details  
drain Toggle drain mode on a given node  
eligibility Toggle scheduling eligibility for a given node  
status Display status information about nodes
