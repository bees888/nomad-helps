# nomad agent -help

Usage: nomad agent [options]

Starts the Nomad agent and runs until an interrupt is received.
The agent may be a client and/or server.

The Nomad agent's configuration primarily comes from the config
files used, but a subset of the options may also be passed directly
as CLI arguments, listed below.

General Options (clients and servers):

-bind=<addr>
The address the agent will bind to for all of its various network
services. The individual services that run bind to individual
ports on this address. Defaults to the loopback 127.0.0.1.

-config=<path>
The path to either a single config file or a directory of config
files to use for configuring the Nomad agent. This option may be
specified multiple times. If multiple config files are used, the
values from each will be merged together. During merging, values
from files found later in the list are merged over values from
previously parsed files.

-data-dir=<path>
The data directory used to store state and other persistent data.
On client machines this is used to house allocation data such as
downloaded artifacts used by drivers. On server nodes, the data
dir is also used to store the replicated log.

-plugin-dir=<path>
The plugin directory is used to discover Nomad plugins. If not specified,
the plugin directory defaults to be that of <data-dir>/plugins/.

-dc=<datacenter>
The name of the datacenter this Nomad agent is a member of. By
default this is set to "dc1".

-log-level=<level>
Specify the verbosity level of Nomad's logs. Valid values include
DEBUG, INFO, and WARN, in decreasing order of verbosity. The
default is INFO.

-log-json
Output logs in a JSON format. The default is false.

-node=<name>
The name of the local agent. This name is used to identify the node
in the cluster. The name must be unique per region. The default is
the current hostname of the machine.

-region=<region>
Name of the region the Nomad agent will be a member of. By default
this value is set to "global".

-dev
Start the agent in development mode. This enables a pre-configured
dual-role agent (client + server) which is useful for developing
or testing Nomad. No other configuration is required to start the
agent in this mode, but you may pass an optional comma-separated
list of mode configurations:

-dev-connect
Start the agent in development mode, but bind to a public network
interface rather than localhost for using Consul Connect. This
mode is supported only on Linux as root.

Server Options:

-server
Enable server mode for the agent. Agents in server mode are
clustered together and handle the additional responsibility of
leader election, data replication, and scheduling work onto
eligible client nodes.

-bootstrap-expect=<num>
Configures the expected number of servers nodes to wait for before
bootstrapping the cluster. Once <num> servers have joined each other,
Nomad initiates the bootstrap process.

-encrypt=<key>
Provides the gossip encryption key

-join=<address>
Address of an agent to join at start time. Can be specified
multiple times.

-raft-protocol=<num>
The Raft protocol version to use. Used for enabling certain Autopilot
features. Defaults to 2.

-retry-join=<address>
Address of an agent to join at start time with retries enabled.
Can be specified multiple times.

-retry-max=<num>
Maximum number of join attempts. Defaults to 0, which will retry
indefinitely.

-retry-interval=<dur>
Time to wait between join attempts.

-rejoin
Ignore a previous leave and attempts to rejoin the cluster.

Client Options:

-client
Enable client mode for the agent. Client mode enables a given node to be
evaluated for allocations. If client mode is not enabled, no work will be
scheduled to the agent.

-state-dir
The directory used to store state and other persistent data. If not
specified a subdirectory under the "-data-dir" will be used.

-alloc-dir
The directory used to store allocation data such as downloaded artifacts as
well as data produced by tasks. If not specified, a subdirectory under the
"-data-dir" will be used.

-servers
A list of known server addresses to connect to given as "host:port" and
delimited by commas.

-node-class
Mark this node as a member of a node-class. This can be used to label
similar node types.

-meta
User specified metadata to associated with the node. Each instance of -meta
parses a single KEY=VALUE pair. Repeat the meta flag for each key/value pair
to be added.

-network-interface
Forces the network fingerprinter to use the specified network interface.

-network-speed
The default speed for network interfaces in MBits if the link speed can not
be determined dynamically.

ACL Options:

-acl-enabled
Specifies whether the agent should enable ACLs.

-acl-replication-token
The replication token for servers to use when replicating from the
authoritative region. The token must be a valid management token from the
authoritative region.

Consul Options:

-consul-address=<addr>
Specifies the address to the local Consul agent, given in the format host:port.
Supports Unix sockets with the format: unix:///tmp/consul/consul.sock

-consul-auth=<auth>
Specifies the HTTP Basic Authentication information to use for access to the
Consul Agent, given in the format username:password.

-consul-auto-advertise
Specifies if Nomad should advertise its services in Consul. The services
are named according to server_service_name and client_service_name. Nomad
servers and clients advertise their respective services, each tagged
appropriately with either http or rpc tag. Nomad servers also advertise a
serf tagged service.

-consul-ca-file=<path>
Specifies an optional path to the CA certificate used for Consul communication.
This defaults to the system bundle if unspecified.

-consul-cert-file=<path>
Specifies the path to the certificate used for Consul communication. If this
is set then you need to also set key_file.

-consul-checks-use-advertise
Specifies if Consul heath checks should bind to the advertise address. By
default, this is the bind address.

-consul-client-auto-join
Specifies if the Nomad clients should automatically discover servers in the
same region by searching for the Consul service name defined in the
server_service_name option.

-consul-client-service-name=<name>
Specifies the name of the service in Consul for the Nomad clients.

-consul-client-http-check-name=<name>
Specifies the HTTP health check name in Consul for the Nomad clients.

-consul-key-file=<path>
Specifies the path to the private key used for Consul communication. If this
is set then you need to also set cert_file.

-consul-server-service-name=<name>
Specifies the name of the service in Consul for the Nomad servers.

-consul-server-http-check-name=<name>
Specifies the HTTP health check name in Consul for the Nomad servers.

-consul-server-serf-check-name=<name>
Specifies the Serf health check name in Consul for the Nomad servers.

-consul-server-rpc-check-name=<name>
Specifies the RPC health check name in Consul for the Nomad servers.

-consul-server-auto-join
Specifies if the Nomad servers should automatically discover and join other
Nomad servers by searching for the Consul service name defined in the
server_service_name option. This search only happens if the server does not
have a leader.

-consul-ssl
Specifies if the transport scheme should use HTTPS to communicate with the
Consul agent.

-consul-token=<token>
Specifies the token used to provide a per-request ACL token.

-consul-verify-ssl
Specifies if SSL peer verification should be used when communicating to the
Consul API client over HTTPS.

Vault Options:

-vault-enabled
Whether to enable or disable Vault integration.

-vault-address=<addr>
The address to communicate with Vault. This should be provided with the http://
or https:// prefix.

-vault-token=<token>
The Vault token used to derive tokens from Vault on behalf of clients.
This only needs to be set on Servers. Overrides the Vault token read from
the VAULT_TOKEN environment variable.

-vault-create-from-role=<role>
The role name to create tokens for tasks from.

-vault-allow-unauthenticated
Whether to allow jobs to be submitted that request Vault Tokens but do not
authentication. The flag only applies to Servers.

-vault-ca-file=<path>
The path to a PEM-encoded CA cert file to use to verify the Vault server SSL
certificate.

-vault-ca-path=<path>
The path to a directory of PEM-encoded CA cert files to verify the Vault server
certificate.

-vault-cert-file=<token>
The path to the certificate for Vault communication.

-vault-key-file=<addr>
The path to the private key for Vault communication.

-vault-tls-skip-verify=<token>
Enables or disables SSL certificate verification.

-vault-tls-server-name=<token>
Used to set the SNI host when connecting over TLS.
