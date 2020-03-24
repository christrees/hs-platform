# Note from Dr. Paul Gray

Hey Chris,

### tl;dr
I'd recommend doing PXE installs of base debian systems and
doing a proxmox overlay afterward.  It's a lot easier to configure than
depending on the proxmox installer, which was meant to be an idiot-proof
install tool.

## Detail
As you correctly assessed, I had indeed done similar deployments.  My
preference was to push a base Debian installation over PXE, which allows
the customization of LVM volumes across mdraid-supported RAID arrays
(something the base Proxmox installer didn't support).  This afforded
quite a bit of customization for "non DRAC" raid setups, which meant
that I didn't need to use a high-$$ raid controller nor depend on Dell's
raid add-ons.

It also afforded the opportunity to push all of this on top of a
cryptographic root filesystem -- no usable data on any physical disk at
any time.

## In summary - the base was PXE-based installation using:
- mdraid for arbitrary (useful) raid topologies
- cryptsetup with full disk encryption
- lvm volumes
    * proxmox likes lvm for snapshots, although I also used zfs
- then using debootstrap, push a minimal Debian system.
- then using `dpkg --set-selections < package.lst` push up the full
enterprise system.

^^^^^ All of the above is performed from a basic PXE-booted Debian OS.

The latter components allow for fine-tuning Proxmox.  For example, I use
qmail instead of postgres, and add a lot of packages for kvm/vz management.

The key to getting all of this working together is adding
mdraid+lvm+cryptfs support to both Grub and to your initrd, which is
easy to do with the mkinitrd helper scripts.

If your deployment is in a remote datacenter, you can set up cryptofs
with one-time passwords for booting the system up when hands-on recover
is required by the local staff.

That addresses the proxmox installation (but not the automated addition
to the cluster -- noted) ... You also mentioned subsequent vm instances:

Once the proxmox cluster is established, you can use a similar PXE boot
paradigm, but now with NFS root, to deploy your student PXE boxes.  I
had done that in spades as well.  I had a previous infrastructure where
a client would PXE-boot, get its NFS-root mount from the server, get a
unique slice to hold its root filesystem and then could subsequently be
booted up anywhere on the network to its previous state.  That was all
accomplished using PXE magic.
