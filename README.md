SLES for SAP plugin for supportconfig

# Project status:

This project is currently released to SLE12 and SLE15 Codestream.

# Additional information:

Additional information can be found in the TID [000020279](https://www.suse.com/de-de/support/kb/doc/?id=000020279)

# Install, rpm and release:

Released rpms can be found in the official repositories.

For development related rpms pkg have a look here:

- devel: https://build.opensuse.org/package/show/network:ha-clustering:Unstable/supportutils-plugin-ha-sap

# Functionality:

This is a plugin for the supportconfig tool.
Supportconfig will create a `scc_<servername>_<date>*.txz` file in `/var/log/ directory`.
When the supportconfig tarball is extracted, the plugin output will be called `plugin-ha_sap.txt`
This plugin will collect informations related to SAP HA environmen:
* Searching for needed local groups and users
* State of sapconf and saptuned
* Get SAP Instances using saphostctrl function. Relies on sap interface to be working.

You can run `supportconfig -F` to see list of keywords which can be used in the `-i` option below. 
Example:
```
supportconfig -F
AFP APPARMOR AUDIT AUTOFS BOOT BTRFS DAEMONS CIFS CIMOM CRASH CRON DFS DHCP DISK DNS DOCKER DRBD DSFW EDIR ENV ETC EVMS HA HAPROXY HISTORY IB IMAN ISCSI KVM LDAP LUM LVM LXC MEM MOD MPIO NCP NCS NET NFS NIT NSS NTP OCFS2 OES OFILES PAM PRINT PROC PROXY SAM SAR SLERT SLP SMT SMART SMB SMS SRAID SSH SSSD SYSCONFIG SYSFS UDEV UFILES UP UPD WEB X XEN aEDIR aFSLIST aLOGS aMINDISK aMAXYAST aRPMV aSLP aLOCAL_ONLY pha_sap
```
* Often times the `openfiles.txt` and `proc.txt` gathering process can take awhile and the output is very large. You can exclude these options by using the `-x` keyword options.

  Example: `supportconfig -x OFILES,PROC`

* If you want to run minimal supportconfig with `HA` and `ha_sap` plugin script.

  Example: `supportconfig -i pha_sap,HA`
  
* To combine the options to exclude `openfiles` and `proc` and to run minimal gathering with the `ha_sap` plugin.

  Example: `supportconfig -x OFILES,PROC -i pha_sap`
