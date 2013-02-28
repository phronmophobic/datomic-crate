# datomic-crate

A Clojure library designed to work with pallet 0.8.0 and create a datomic instance.  This instance has been tested on Ubuntu with the free version of datomic.  I don't believe there is anything preventing it from working with non-free versions but I don't have one so don't know the process.  This crate will 
* It is expected that you have java installed on the machine already.
* Download datomic based upon the type and version
* Unzip datomic into /opt/local/datomic/<version>
* Update a soft link /opt/local/datomic/current -> /opt/local/datomic/version
* Install the upstart service.  (It will NOT run the service)

## Continuous Integration Status
[![Build Status](https://travis-ci.org/rstradling/smf-crate.png)](https://travis-ci.org/rstradling/datomic-crate])

## Usage
Artifacts are released [released to Clojars](https://clojars.org/strad/datomic-crate).  If you are using Maven, add the following definition to your `pom.xml`:
```xml
<repository>
 <id>clojars.org</id>
 <url>http://clojars.org/repo</url>
</repository>
```

### The Most Recent Release
With Leiningen
```clojure
   [org.clojars.strad/smf-crate "0.1.0"]
```

With Maven
```xml
   <dependency>
      <groupId>org.clojars.strad</groupId>
      <artifactId>smf-crate</artifactId>
      <version>0.1.0</version>
   </dependency>
```

## Server Spec
The datomic crate defines the datomic function, that takes a settings map and returns a server-spec for installing datomic.  You can use this in a `group-spec` or `server-spec`.

```clj
(group-spec "my-node-with-datomic"
   :extends [(pallet.crate.datomic/datomic {})])

## Settings
The datomic crate uses the folowing settings...
`:version`
Version number of datomic to use 

`:type`
The version to use.  One of `#{"free"}`.  This is only used to figure out what version should be downloaded.

`:user`
The user to install the datomic service and code as.  Defaults to `"datomic"`.

`:group`
The group to install the datomic service and code as.  Defaults to `"datomic"`.

`:config-path`
The location of the config file.  Defaults to `"/etc/datomic"`. The file name would then be /etc/datomic/transactor.properties.

### Config
`:config`
The data to save to the config-file.

`:protocol`
The protocol to use.  Defaults to free

`:host`
The host to use.  Defaults to localhost

`:port`
The port to use.  Defaults to 4334

`:data-dir`
The data directory to save the dbs to.  Defaults to `"var/lib/datomic/data"`

`:log-dir`
The log directory to save the logs to.  Defaults to `"var/log/datomic"`

`:memory-index-max`
Optional.  Defaults to no key and no value. (i.e. nothing is written to the config file)







## License

Copyright © 2013 FIXME

Distributed under the Eclipse Public License, the same as Clojure.