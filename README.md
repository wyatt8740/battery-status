# Battery Status

This is a bourne shell script (which should be "POSIX-compliant," at least
for the logic) for checking battery charge status on Linux machines. The main
upshot of this script (versus manually reading data from sysfs) is that this
script can give you charge information as a percentage of one hundred instead
of raw energy or charge values, and it also will check all batteries on systems
with more than one of them with one command.

## Example:

    wyatt@latitude-debian:~$ battery
    Battery #1:
    100%    Full
    Battery #2:
    90%     Charging
    
## Details:

It supports checking the states of multiple batteries. It is written to work
for ACPI platforms (status read from `/sys/class/power_supply/BAT*`) and Apple
PowerPC Macs (status read from `/sys/class/power_supply/PMU*`). I am unsure
how other platforms report battery information, but would love to add support
for them.

If you want another platform supported (say, another operating system/kernel,
or another architecture), point me to documentation or let me know how you can
get battery data out on your machine and I'll give it a shot. This will
be easiest if you can give me a readout of all the battery information reported
on your machine as well.

At one point, I had a version of this script for FreeBSD ACPI systems, but I
think that script got lost when I erased that installation. If I ever find it
saved somewhere else, I will merge it with this script.

I don't call the script as a whole "POSIX" because POSIX does not specify a
standardized method for polling battery information on computers. Thus, for
instance, FreeBSD uses `sysctl` to get battery information, Linux uses sysfs
(specifically, `/sys/class/power_supply/` directories), and I think OpenBSD
uses `sysctl` as well.

## License

This script is licensed under the "three-clause BSD" license.

Please refer to `LICENSE.txt` for the license terms.

If this license is unacceptable, feel free to drop me a line and let me know
why. I'll probably be willing to grant different terms if asked. Not that I
really anticipate any major problems with a BSD license.
