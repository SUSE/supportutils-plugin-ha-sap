SLES for SAP plugin for supportconfig

# Project status:

This project is currenlty development, there are not any ready to use pkgs. 


# Rpm and release:

For rpms pkg have look here: 

- devel: https://build.opensuse.org/package/show/network:ha-clustering:Unstable/supportutils-plugin-ha-sap
- stable:  https://build.opensuse.org/package/show/network:ha-clustering:Stable/supportutils-plugin-ha-sap 




### Manual installation

1. Extract and copy script [suse_SAP](suse_SAP) to `/usr/lib/supportconfig/plugins` directory.
   - Create the `plugins` directory if it does not exist
2. Set `suse_SAP` script to be executable.
2. When you run the normal supportconfig, it will run any plugins that it finds in these directories.

Supportconfig will create a `nts_*.tbz` file in `/var/log/ directory`. When the supportconfig tarball is extracted, the plugin output will be called `plugin-suse_SAP.txt`

You can run `supportconfig -F` to see list of keywords which can be used in the `-i` option below. 
Example:
```
supportconfig -F
AFP APPARMOR AUDIT AUTOFS BOOT BTRFS DAEMONS CIFS CIMOM CRASH CRON DFS DHCP DISK DNS DOCKER DRBD DSFW EDIR ENV ETC EVMS HA HAPROXY HISTORY IB IMAN ISCSI KVM LDAP LUM LVM LXC MEM MOD MPIO NCP NCS NET NFS NIT NSS NTP OCFS2 OES OFILES PAM PRINT PROC PROXY SAM SAR SLERT SLP SMT SMART SMB SMS SRAID SSH SSSD SYSCONFIG SYSFS UDEV UFILES UP UPD WEB X XEN aEDIR aFSLIST aLOGS aMINDISK aMAXYAST aRPMV aSLP aLOCAL_ONLY psuse_SAP
```
* Often times the `openfiles.txt` and `proc.txt` gathering process can take awhile and the output is very large. You can exclude these options by using the `-x` keyword options.

  Example: `supportconfig -x OFILES,PROC`

* If you want to run minimal supportconfig with HA and suse_SAP plugin script.

  Example: `supportconfig -i psuse_SAP,HA`
  
* To combine the options to exclude `openfiles` and `proc` and to run minimal gathering with the suse_SAP plugin.

  Example: `supportconfig -x OFILES,PROC -i psuse_SAP`
