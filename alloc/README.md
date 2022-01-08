# nomad alloc -help

Usage: nomad alloc <subcommand> [options] [args]

This command groups subcommands for interacting with allocations. Users can
inspect the status, examine the filesystem or logs of an allocation.

Examine an allocations status:

      $ nomad alloc status <alloc-id>

Stream a task's logs:

      $ nomad alloc logs -f <alloc-id> <task>

Please see the individual subcommand help for detailed usage information.

Subcommands:  
exec Execute commands in task  
fs Inspect the contents of an allocation directory  
logs Streams the logs of a task.  
restart Restart a running allocation  
signal Signal a running allocation  
status Display allocation status information and metadata  
stop Stop and reschedule a running allocation
