# nomad run -help

Usage: nomad job run [options] <path>
Alias: nomad run

Starts running a new job or updates an existing job using
the specification located at <path>. This is the main command
used to interact with Nomad.

If the supplied path is "-", the jobfile is read from stdin. Otherwise
it is read from the file at the supplied path or downloaded and
read from URL specified.

Upon successful job submission, this command will immediately
enter an interactive monitor. This is useful to watch Nomad's
internals make scheduling decisions and place the submitted work
onto nodes. The monitor will end once job placement is done. It
is safe to exit the monitor early using ctrl+c.

On successful job submission and scheduling, exit code 0 will be
returned. If there are job placement issues encountered
(unsatisfiable constraints, resource exhaustion, etc), then the
exit code will be 2. Any other errors, including client connection
issues or internal errors, are indicated by exit code 1.

If the job has specified the region, the -region flag and NOMAD_REGION
environment variable are overridden and the job's region is used.

The run command will set the consul_token of the job based on the following
precedence, going from highest to lowest: the -consul-token flag, the
$CONSUL_HTTP_TOKEN environment variable and finally the value in the job file.

The run command will set the vault_token of the job based on the following
precedence, going from highest to lowest: the -vault-token flag, the
$VAULT_TOKEN environment variable and finally the value in the job file.

When ACLs are enabled, this command requires a token with the 'submit-job'
capability for the job's namespace. Jobs that mount CSI volumes require a
token with the 'csi-mount-volume' capability for the volume's
namespace. Jobs that mount host volumes require a token with the
'host_volume' capability for that volume.

General Options:

-address=<addr>
The address of the Nomad server.
Overrides the NOMAD_ADDR environment variable if set.
Default = http://127.0.0.1:4646

-region=<region>
The region of the Nomad servers to forward commands to.
Overrides the NOMAD_REGION environment variable if set.
Defaults to the Agent's local region.

-namespace=<namespace>
The target namespace for queries and actions bound to a namespace.
Overrides the NOMAD_NAMESPACE environment variable if set.
If set to '\*', job and alloc subcommands query all namespaces authorized
to user.
Defaults to the "default" namespace.

-no-color
Disables colored command output. Alternatively, NOMAD_CLI_NO_COLOR may be
set. This option takes precedence over -force-color.

-force-color
Forces colored command output. This can be used in cases where the usual
terminal detection fails. Alternatively, NOMAD_CLI_FORCE_COLOR may be set.
This option has no effect if -no-color is also used.

-ca-cert=<path>
Path to a PEM encoded CA cert file to use to verify the
Nomad server SSL certificate. Overrides the NOMAD_CACERT
environment variable if set.

-ca-path=<path>
Path to a directory of PEM encoded CA cert files to verify
the Nomad server SSL certificate. If both -ca-cert and
-ca-path are specified, -ca-cert is used. Overrides the
NOMAD_CAPATH environment variable if set.

-client-cert=<path>
Path to a PEM encoded client certificate for TLS authentication
to the Nomad server. Must also specify -client-key. Overrides
the NOMAD_CLIENT_CERT environment variable if set.

-client-key=<path>
Path to an unencrypted PEM encoded private key matching the
client certificate from -client-cert. Overrides the
NOMAD_CLIENT_KEY environment variable if set.

-tls-server-name=<value>
The server name to use as the SNI host when connecting via
TLS. Overrides the NOMAD_TLS_SERVER_NAME environment variable if set.

-tls-skip-verify
Do not verify TLS certificate. This is highly not recommended. Verification
will also be skipped if NOMAD_SKIP_VERIFY is set.

-token
The SecretID of an ACL token to use to authenticate API requests with.
Overrides the NOMAD_TOKEN environment variable if set.

Run Options:

-check-index
If set, the job is only registered or updated if the passed
job modify index matches the server side version. If a check-index value of
zero is passed, the job is only registered if it does not yet exist. If a
non-zero value is passed, it ensures that the job is being updated from a
known state. The use of this flag is most common in conjunction with plan
command.

-detach
Return immediately instead of entering monitor mode. After job submission,
the evaluation ID will be printed to the screen, which can be used to
examine the evaluation using the eval-status command.

-hcl1
Parses the job file as HCLv1.

-hcl2-strict
Whether an error should be produced from the HCL2 parser where a variable
has been supplied which is not defined within the root variables. Defaults
to true.

-output
Output the JSON that would be submitted to the HTTP API without submitting
the job.

-policy-override
Sets the flag to force override any soft mandatory Sentinel policies.

-preserve-counts
If set, the existing task group counts will be preserved when updating a job.

-consul-token
If set, the passed Consul token is stored in the job before sending to the
Nomad servers. This allows passing the Consul token without storing it in
the job file. This overrides the token found in $CONSUL_HTTP_TOKEN environment
variable and that found in the job.

-vault-token
If set, the passed Vault token is stored in the job before sending to the
Nomad servers. This allows passing the Vault token without storing it in
the job file. This overrides the token found in $VAULT_TOKEN environment
variable and that found in the job.

-vault-namespace
If set, the passed Vault namespace is stored in the job before sending to the
Nomad servers.

-var 'key=value'
Variable for template, can be used multiple times.

-var-file=path
Path to HCL2 file containing user variables.

-verbose
Display full information.
