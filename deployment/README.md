# nomad deployment -help

Usage: nomad deployment <subcommand> [options] [args]

This command groups subcommands for interacting with deployments. Deployments
are used to manage a transition between two versions of a Nomad job. Users
can inspect an ongoing deployment, promote canary allocations, force fail
deployments, and more.

Examine a deployments status:

      $ nomad deployment status <deployment-id>

Promote the canaries to allow the remaining allocations to be updated in a
rolling deployment fashion:

      $ nomad deployment promote <deployment-id>

Mark a deployment as failed. This will stop new allocations from being placed
and if the job's upgrade stanza specifies auto_revert, causes the job to
revert back to the last stable version of the job:

      $ nomad deployment fail <deployment-id>

Please see the individual subcommand help for detailed usage information.

Subcommands:  
fail Manually fail a deployment  
list List all deployments  
pause Pause a deployment  
promote Promote canaries in a deployment  
resume Resume a paused deployment  
status Display the status of a deployment  
unblock Unblock a blocked deployment
