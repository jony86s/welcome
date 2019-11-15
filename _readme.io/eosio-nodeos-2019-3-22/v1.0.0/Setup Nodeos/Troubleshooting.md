---
title: "Troubleshooting"
excerpt: ""
---
1. **You get an error such as `St9exception: content of memory does not match data expected by executable` when trying to start `nodeos`, try restarting `nodeos` with one of the following options (you can use `nodeos --help` to get a full listing of these).**

```
Command Line Options for eosio::chain_plugin:
    --fix-reversible-blocks               recovers reversible block database if 
                                          that database is in a bad state
    --force-all-checks                    do not skip any checks that can be 
                                          skipped while replaying irreversible 
                                          blocks
    --replay-blockchain                   clear chain state database and replay 
                                          all blocks
    --hard-replay-blockchain              clear chain state database, recover as 
                                          many blocks as possible from the block 
                                          log, and then replay those blocks
    --delete-all-blocks                   clear chain state database and block 
                                          log
```

2. **You get an error such as `could not grow database file to requested size.`**

Start `nodeos` with `--shared-memory-size-mb 1024`. A 1 GB shared memory file allows approximately half a million transactions.

3. **How do I find which version of `nodeos` I'm running or connecting to?**

If defaults can be used, then `cleos get info` will output a block that contains a field called `server_version`.  If your `nodeos` is not using the defaults, then you need to know the URL of the `nodeos`. In that case, use the following with your `nodeos` URL:
```
cleos --url http://localhost:8888 get info
```

To focus only on the version line within the block:
```
cleos --url http://localhost:8888 get info | grep server_version
```