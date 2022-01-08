# nomad operator

Usage: nomad operator <subcommand> [options]

Provides cluster-level tools for Nomad operators, such as interacting with
the Raft subsystem. NOTE: Use this command with extreme caution, as improper
use could lead to a Nomad outage and even loss of data.

Please see the individual subcommand help for detailed usage information.

Subcommands:  
autopilot Provides tools for modifying Autopilot configuration  
debug Build a debug archive  
keygen Generates a new encryption key  
keyring Manages gossip layer encryption keys  
metrics Retrieve Nomad metrics  
raft Provides access to the Raft subsystem  
snapshot Saves and inspects snapshots of Nomad server state
