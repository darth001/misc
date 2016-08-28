#


## Cannot delete file as root

The most common reason for rm complaining that you don't have permission to delete a file, is that the permissions on the directory forbid you from deleting the file. in order to delete a file, you need write permission on the directory. The permissions on the file are irrelevant(rm without -f prompts for confirmation before deleting a read-only file, but that's just a confirmation, not a limitation).

On some Unix variants such as OS X(but not Linux, the ACL on a file can prevent its deletion; `ls -l` would a @ at the end of the permission field if there was an ACL entry on the file.

Access as root bypasses permissions, so root can delete files even in a read-only directory.

The output from `ls -l` shows a `.` at the end of the permission column. The indicates that the file has an SELinux security context. Unlike basic permissions and ACL, the SELinux security context on a file can control who is allowed to delete it. Furthermore SELinux cannot always be bypassed by root(it's possible to have a process running as user ID 0 but with as few rights as the SELinux policy designer close). To see what the SELinux context allows you to do, run `ls -lZ .`.

Another thing that can prevent a file from being deleted is if it or the directory that contains it has the append-only or immutable Linux attribute. Run `lsattr -d .` to view the Linux attributes. If the `a` or `i` attribute is on, you'll need to remove it(`chattr -a -i .`) in order to delete the file; only root can do that. Root cannot bypass these attributes to delete a file, the attributes have to be turned off first.

Yet another thing that prevents a file from being deleted is if the filesystem is mounted read-only, but you'd get a different error message in that case.

-- from StackOverflow(http://unix.stackexchange.com/quections/206594/why-cant-i-delete-this-file-as-root/)


##

##

http://www.cyberciti.biz/faq/find-hard-disk-hardware-specs-on-linux/
http://www.ibm.com/developernetworks/library/l-lpic1-102-1/
http://www.ibm.com/developernetworks/linux/library/l-lpic1-104-1/index.html
http://www.ibm.com/developernetworks/linux/library/l-lpic1-104-2/index.html
http://www.ibm.com/developernetworks/linux/library/l-lpic1-104-3/index.html
http://www.ibm.com/developernetworks/linux/library/l-lpic1-104-4/index.html
http://www.ibm.com/developernetworks/linux/library/l-4kb-sector-disks/index.html

