## run host

### Usage

`stack run host [host]... {command} [collate=string] [command=string] [delay=string] [managed=boolean] [num-threads=string] [timeout=string] [x11=boolean]`

### Description

Run a command for each specified host.

### Arguments

* `[host]`

   Zero, one or more host names. If no host names are supplied, the command
	is run on all 'managed' hosts. By default, all compute nodes are
	'managed' nodes. To determine if a host is managed, execute:
	'rocks list host attr hostname | grep managed'. If you see output like:
	'compute-0-0: managed true', then the host is managed.

* `{command}`

   The command to run on the list of hosts.


### Parameters
* `[collate=string]`

   Prepend the hostname to every output line if this parameter is set to
	'yes'. Default is 'yes'.
* `[command=string]`

   Can be used in place of the 'command' argument.
* `[delay=string]`

   Sets the time (in seconds) to delay between each executed command
	on multiple hosts. For example, if the command is run on two
	hosts and if the delay is 10, then the command will be executed on host
	1, then 10 seconds later, the command will be executed on host 2.
	Default is '0' (no delay).
* `[managed=boolean]`

   Run the command only on 'managed' hosts, that is, hosts that generally
	have an ssh login. Default is 'yes'.
* `[num-threads=string]`

   The number of threads to start in parallel. If num-threads is 0, then
	try to run the command in parallel on all hosts. Default is '128'.
* `[timeout=string]`

   Sets the maximum length of time (in seconds) that the command is
	allowed to run.
	Default is '30'.
* `[x11=boolean]`

   If 'yes', enable X11 forwarding when connecting to hosts.
	Default is 'no'.

### Examples

* `stack run host compute-0-0 command="hostname"`

   Run the command 'hostname' on compute-0-0.

* `stack run host compute "ls /tmp"`

   Run the command 'ls /tmp/' on all compute nodes.


