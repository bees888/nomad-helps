# nomad sentinel

Usage: nomad sentinel <subcommand> [options] [args]

This command groups subcommands for interacting with Sentinel policies.
Sentinel policies allow operators to express fine-grained policies as code and
have their policies automatically enforced. This allows operators to define a
"sandbox" and restrict actions to only those compliant with policy. The
Sentinel integration builds on the ACL System. Users can read existing
Sentinel policies, create new policies, delete and list existing policies, and
more. For a full guide on Sentinel policies see:
https://www.nomadproject.io/guides/sentinel-policy.html

Read an existing policy:

      $ nomad sentinel read <name>

List existing policies:

      $ nomad sentinel list

Create a new Sentinel policy:

      $ nomad sentinel apply <name> <path>

Please see the individual subcommand help for detailed usage information.

Subcommands:  
apply Create a new or update existing Sentinel policies  
delete Delete an existing Sentinel policies  
list Display all Sentinel policies  
read Inspects an existing Sentinel policies
