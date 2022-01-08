# nomad acl -help

Usage: nomad acl <subcommand> [options] [args]

This command groups subcommands for interacting with ACL policies and tokens.
Users can bootstrap Nomad's ACL system, create policies that restrict access,
and generate tokens from those policies.

Bootstrap ACLs:

      $ nomad acl bootstrap

Please see the individual subcommand help for detailed usage information.

Subcommands:  
bootstrap Bootstrap the ACL system for initial token  
policy Interact with ACL policies  
token Interact with ACL tokens
