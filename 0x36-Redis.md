#

## background save failure when running out of memory

Problem:

overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.

Solution:

This problem can be solved by setting vm.overcommit_memory=1 and then reboot, or with below methods at runtime:

* add vm.overcommit_memory=1 to /etc/sysctl.conf, then run command below:
    $ sysctl -p
* run command below directly:
    $ sysctl vm.overcommit_memory=1
* or run command below:
    $ echo 1 > /proc/sys/vm/overcommit_memory

You can verify the setting via command:
    $ sysctl -n vm.overcommit_memory

NOTE: Commands above are also general way to set other kernel parameters.
