# Hamilton-combined v11.1 - 11/21/2017

11.1 adds a small xtimer fix.

Readme for 11.0:

Board support for the Hamilton mote is maintained as a set of rebasing branches
that will at some stage be pushed upstream. At intervals, a "combined" branch
is created so that working with the hamilton is as easy as cloning this repo.
The v10.0 branch was created with the following commands

```bash
git clone https://github.com/hamilton-mote/RIOT-OS.git
cd RIOT-OS
git checkout master
git pull https://github.com/RIOT-OS/RIOT.git master # 2e0917cd8115073e5f
git remote add upstream https://github.com/RIOT-OS/RIOT.git
git checkout -b hamilton-combined-v11.0

git merge --no-ff origin/hamilton-board
git merge --no-ff origin/hamilton-clock
git merge --no-ff origin/hamilton-xtimer-improvement
git merge --no-ff origin/hamilton-adc
git merge --no-ff origin/hamilton-lasmac


git merge --no-ff origin/hamilton-pushbutton
git merge --no-ff origin/hamilton-fxos8700
# some conflicts
git merge --no-ff origin/hamilton-ekmb
git merge --no-ff origin/hamilton-apds9007
git merge --no-ff origin/hamilton-hdc1000
# Some trivial conflicts
git merge --no-ff origin/hamilton-tmp006

# merge in endianness fix
git merge --no-ff origin/hamilton-radio-extra

# add in this readme and commit
# then push
git push --set-upstream origin hamilton-combined-v11.0


If you want to contribute, please consider contributing upstream. If that is
not appropriate (you have hamilton-specific changes) please submit a PR
as changes on top of master (which will track upstream) as this makes rebasing
easier. If that is not possible (you are editing hamilton-specific files) you
can base your PR on a combined branch, but please make clear which version
you used. We recommend including this information in your branches, such as
`c11.0-my-feature`.

upstream readme:
                          ZZZZZZ
                        ZZZZZZZZZZZZ
                      ZZZZZZZZZZZZZZZZ
                     ZZZZZZZ     ZZZZZZ
                    ZZZZZZ        ZZZZZ
                    ZZZZZ          ZZZZ
                    ZZZZ           ZZZZZ
                    ZZZZ           ZZZZ
                    ZZZZ          ZZZZZ
                    ZZZZ        ZZZZZZ
                    ZZZZ     ZZZZZZZZ       777        7777       7777777777
              ZZ    ZZZZ   ZZZZZZZZ         777      77777777    77777777777
          ZZZZZZZ   ZZZZ  ZZZZZZZ           777     7777  7777       777
        ZZZZZZZZZ   ZZZZ    Z               777     777    777       777
       ZZZZZZ       ZZZZ                    777     777    777       777
      ZZZZZ         ZZZZ                    777     777    777       777
     ZZZZZ          ZZZZZ    ZZZZ           777     777    777       777
     ZZZZ           ZZZZZ    ZZZZZ          777     777    777       777
     ZZZZ           ZZZZZ     ZZZZZ         777     777    777       777
     ZZZZ           ZZZZ       ZZZZZ        777     777    777       777
     ZZZZZ         ZZZZZ        ZZZZZ       777     777    777       777
      ZZZZZZ     ZZZZZZ          ZZZZZ      777     7777777777       777
       ZZZZZZZZZZZZZZZ            ZZZZ      777      77777777        777
         ZZZZZZZZZZZ               Z
            ZZZZZ

The friendly Operating System for IoT!

RIOT is a real-time multi-threading operating system that supports a range of
devices that are typically found in the Internet of Things (IoT): 
8-bit, 16-bit and 32-bit microcontrollers.

RIOT is based on the following design principles: energy-efficiency, real-time
capabilities, small memory footprint, modularity, and uniform API access,
independent of the underlying hardware (this API offers partial POSIX
compliance).

RIOT is developed by an international open source community which is
independent of specific vendors (e.g. similarly to the Linux community).
RIOT is licensed with LGPLv2.1, a copyleft license which fosters
indirect business models around the free open-source software platform
provided by RIOT, e.g. it is possible to link closed-source code with the
LGPL code.

## FEATURES

RIOT is based on a microkernel architecture, and provides features including,
but not limited to:

* a preemptive, tickless scheduler with priorities
* flexible memory management
* high resolution, long-term timers
* support for AVR, MSP430, MIPS, ARM7, and ARM Cortex-M on over 80 boards
* the native port allows to run RIOT as-is on Linux, BSD, and MacOS. Multiple
  instances of RIOT running on a single machine can also be interconnected via
  a simple virtual Ethernet bridge
* IPv6
* 6LoWPAN (RFC4944, RFC6282, and RFC6775)
* UDP
* RPL (storing mode, P2P mode)
* CoAP
* CCN-Lite


## GETTING STARTED
* You want to start the RIOT? Just follow our [quickstart guide](http://doc.riot-os.org/index.html#the-quickest-start) or the [getting started documentation](http://doc.riot-os.org/getting-started.html).
* The RIOT API itself can be built from the code using doxygen. The latest
  version is uploaded daily to http://riot-os.org/api.

### USING THE NATIVE PORT WITH NETWORKING
If you compile RIOT for the native cpu and include the `netdev_tap` module,
you can specify a network interface like this: `PORT=tap0 make term`

#### SETTING UP A TAP NETWORK
There is a shellscript in `RIOT/dist/tools/tapsetup` called `tapsetup` which
you can use to create a network of tap interfaces.

*USAGE*
To create a bridge and two (or count at your option) tap interfaces:

    ./dist/tools/tapsetup/tapsetup [-c [<count>]]

## CONTRIBUTE

To contribute something to RIOT, please refer to the [development
procedures](https://github.com/RIOT-OS/RIOT/wiki/Development-procedures) and
read all notes for best practice.

## MAILING LISTS
* RIOT OS kernel developers list
 * devel@riot-os.org (http://lists.riot-os.org/mailman/listinfo/devel)
* RIOT OS users list
 * users@riot-os.org (http://lists.riot-os.org/mailman/listinfo/users)
* RIOT commits
 * commits@riot-os.org (http://lists.riot-os.org/mailman/listinfo/commits)
* Github notifications
 * notifications@riot-os.org
   (http://lists.riot-os.org/mailman/listinfo/notifications)

## LICENSE
* Most of the code developed by the RIOT community is licensed under the GNU
  Lesser General Public License (LGPL) version 2.1 as published by the Free
  Software Foundation.
* Some external sources, especially files developed by SICS are published under
  a separate license.

All code files contain licensing information.

For more information, see the RIOT website:

http://www.riot-os.org
