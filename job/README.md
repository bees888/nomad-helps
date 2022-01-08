# nomad job -help

Usage: nomad job <subcommand> [options] [args]

This command groups subcommands for interacting with jobs.

Run a new job or update an existing job:

      $ nomad job run <path>

Plan the run of a job to determine what changes would occur:

      $ nomad job plan <path>

Stop a running job:

      $ nomad job stop <name>

Examine the status of a running job:

      $ nomad job status <name>

Please see the individual subcommand help for detailed usage information.

Subcommands:
allocs List allocations for a job
deployments List deployments for a job
dispatch Dispatch an instance of a parameterized job
eval Force an evaluation for the job
history Display all tracked versions of a job
init Create an example job file
inspect Inspect a submitted job
periodic Interact with periodic jobs
plan Dry-run a job update to determine its effects
promote Promote a job's canaries
revert Revert to a prior version of the job
run Run a new job or update an existing job
scale Change the count of a Nomad job group
scaling-events Display the most recent scaling events for a job
status Display status information about a job
stop Stop a running job
validate Checks if a given job specification is valid
