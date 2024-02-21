## Creating a Snapshot


**Steps:**

1. **Stop The Junction Node**
2. **Create the Snapshot:**

    ```bash
    tar -czvf backup.tar.gz ~/.junction/data
    ```

* Note: This Process will take approximately 45 minutes to complete.

3 **Restart the Junction Node :**

```bash 
$HOME/go/bin/junctiond start --api.enable   --api.address "tcp://0.0.0.0:1317" --rpc.laddr "tcp://0.0.0.0:26657" --p2p.laddr "tcp://0.0.0.0:26656"  --p2p.persistent_peers="009075e1d1b0989ab2d0563c9e7454eb6c320772@35.200.232.241:26656" --minimum-gas-prices ="0.0001dair"
```
