#


##

    $ ssh-keygen && for host in $(cat hosts.txt); do ssh-copy-id $host; done
    $ for host in $(cat hosts.txt); do ssh "$host" "$command" > "output.$host"; done

SSH BatchMode:

```
tmpdir=${TMPDIR:-/tmp}/pssh.$$
mkdir -p $tmpdir
count=0
while IFS= read -r userhost; do
    ssh -n -o BatchMode=yes ${userhost} "$command" > ${tmpdir}/${userhost} 2>&1 &
    count=`expr $count + 1`
done < userhost.txt
while [ $count -gt 0]; do
    wait $pids
    count=`expr $count - 1`
done
echo "Result for hosts are in $tmpdir"
```

SSH ForwardAgent:

Assuming you have the same public key present in ~/.ssh/authorized_keys on both servers, and that you are running some kind of agent locally, then you can use ForwardAgent mode:

    $ ssh -o ForwardAgent=yes you@server.one
    $ scp -o "ForwardAgent yes" user@host1:/path/to/file user@host2:/path/to/directory

and for large data files, use tar-over-ssh.

##

pssh
pdsh
clusterssh
clsterit
mussh
parallel

##

fabric

    $ sudo pip install fabric
    $ cat > fabfile.py
```
from fabric.api import local

def prepare_deploy():
    local("./manage.py test my_app")
    local("git add -p && git commit")
    local("git push")
```


