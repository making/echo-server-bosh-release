# BOSH Release for echo-server

## Usage

To use this bosh release, first upload it to your bosh:

([bosh-lite](https://github.com/cloudfoundry/bosh-lite))

```
bosh upload release https://github.com/making/echo-server-boshrelease/releases/download/v1/echo-server-1.tgz
bosh cloud-config upadte cloud-config-warden.yml
bosh -n deploy
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
