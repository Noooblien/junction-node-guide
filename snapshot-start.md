## Starting the Chain via Snapshot

**Prerequisites:**

* Sufficient disk space (approximately 27 GB + space for chain data growth)
* Minimum Recommended 200 GB of Storage

**Steps:**

1. **Download the snapshot:**

   ```bash
   curl -o backup.tar.gz http://34.131.6.75/backup.tar.gz 
    ```

* The snapshot is approximately 27 GB in size. It will Require about 30 minutes to download.

2. **Extract the snapshot:**

   ```bash
   tar -xvzf backup.tar.gz -C ~/.junction/ 
   ```

3. **Remove or Backup the old data directory of Junction:**

* Without Backup :

   ```bash
    rm -rf ~/.junction/data 
    ```

* With Backup :

   ```bash
   cp ~/.junction/data ~/.junction/data_old
   rm -rf ~/.junction/data
   ```

4. **Rename the extracted folder:**

   ```bash
   mv ~/.junction/backup ~/.junction/data
   ```

5. **Start the Junction Node:**

   ```bash
    $HOME/go/bin/junctiond start --api.enable   --api.address "tcp://0.0.0.0:1317" --rpc.laddr "tcp://0.0.0.0:26657" --p2p.laddr "tcp://0.0.0.0:26656"  --p2p.persistent_peers="009075e1d1b0989ab2d0563c9e7454eb6c320772@35.200.232.241:26656" --minimum-gas-prices ="0.0001dair"
    ```
