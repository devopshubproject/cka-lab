```
To take the snapshot of the existing ETCD:
$ etcdctl --endpoints=http://127.0.0.1:2379 \
--ca-file=/opt/ca.crt \
--certfile=/opt/etcd-client.crt \
--key=/opt/etcd-client.key snapshot save /path/to/backup/etcdbkp.db

To check the status of the snapshot:
$ ETCDCTL_API=3 etcdctl --write-out=table snapshot status snapshotdb

To write the output to the etcd backup file
$ ETCDCTL_API=3 etcdctl --write-out=table snapshot status File name saved in the previous step > etcdbkp.txt
```