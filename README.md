# BOSH Release for echo-server

## Usage

To use this bosh release, first upload it to your bosh:

([bosh-lite](https://github.com/cloudfoundry/bosh-lite))

```
bosh upload release https://github.com/making/echo-server-boshrelease/releases/download/v1/echo-server-1.tgz
bosh cloud-config upadte cloud-config-warden.yml
bosh -n deploy
```

You can see `echo-server` runs on `10.244.212.2`.

```
$ bosh vms
Acting as user 'admin' on 'Bosh Lite Director'
Deployment 'echo-server'

Director task 1156

Task 1156 done

+------------------------------------------------------+---------+----+---------+--------------+
| VM                                                   | State   | AZ | VM Type | IPs          |
+------------------------------------------------------+---------+----+---------+--------------+
| echo-server/0 (ad139b14-3870-49e9-9fcb-20f65d784103) | running | z1 | default | 10.244.212.2 |
+------------------------------------------------------+---------+----+---------+--------------+

VMs total: 1
```

You can check `echo-server` as follows:

```
$ echo 'Hello BOSH!' | nc 10.244.212.2 12012
Hello BOSH!
```

### Development

As a developer of this release, create new releases and upload them:

```
bosh create release --force && bosh -n upload release
```

### Final releases

To share final releases:

```
bosh create release --final
```

By default the version number will be bumped to the next major number. You can specify alternate versions:


```
bosh create release --final --version 2.1
```

After the first release you need to contact [Dmitriy Kalinin](mailto://dkalinin@pivotal.io) to request your project is added to https://bosh.io/releases (as mentioned in README above).
