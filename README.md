freecash-rpc-client
==================

This is a lightweight java freecash JSON-RPC client binding. It does not require any external dependencies.

Maven
=====
The package is published in the wf.freecash group and you can add it to you pom.xml adding a section like this:

```
<dependency>
    <groupId>wf.freecash</groupId>
    <artifactId>freecash-rpc-client</artifactId>
    <version>1.1.0</version>
</dependency>
```


Configuration
=====
In order to know what RPC API to use, the library will look in the freecash configuration file (`<user home>/.freecash/freecash.conf`) and read the relevant configs:
- rpcconnect
- rpcport

Here is a sample freecash.conf that will setup freecash to run in regtest mode and in a way compatible with this library:

```
# Maintain full transaction index, used in lookups by the getrawtransaction call
txindex=1

# Run freecash in regtest mode
regtest=1

# Accept command line and JSON-RPC commands
server=1

# Tells freecash that the RPC API settings on the following lines apply to the regtest RPC API
[regtest]

# RPC API settings
rpcconnect=localhost
rpcport=9997
```

Note that the configuration does not contain any API credentials. The authentication is done via a temporary token stored in a cookie file by freecash (see [details](https://freecash.org/en/release/v0.12.0#rpc-random-cookie-rpc-authentication)). The approach of using rpcuser and rpcpassword is still supported, even though freecash considers it legacy.
