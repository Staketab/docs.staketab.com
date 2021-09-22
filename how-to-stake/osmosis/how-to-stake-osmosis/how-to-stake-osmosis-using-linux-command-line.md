# How to stake Osmosis using Linux command line

1. Make an update of your operation system:

```text
sudo apt update
```

```text
sudo apt install curl wget git make unzip jq screen -y
```

2. Download the [Go language repository](https://golang.org/dl/go1.17.1.linux-amd64.tar.gz).

3. Extract the archive:

```text
sudo tar -xvf go1.16.4.linux-amd64.tar.gz
```

4. Install Go language to the directory you choose:

```text
sudo mv go /usr/local
```

5. Setup Go language environment variables \(GOROOT, GOPATH and PATH\):

```text
export GOROOT=/usr/local/go export GOPATH=/root export PATH=$GOPATH/bin:$GOROOT/bin:$PATH
```

This environmaent is active just for your current session. For perpetual use, add the commands above to the `~/.profile` file.

6. Clone current Osmosis Git repository:

```text
clone git 
https://github.com/osmosis-labs/osmosis
```

7. Build Osmosis CLI:

```text
cd osmosis make build
```

8. Copy the file to `/usr/local/bin` to become available as a global application:

```text
cd osmosis/build/ cp osmosisd /usr/local/bin
```

9. Create new OSMO address or export an exising one.

9.1. Create new OSMO address:

```text
osmosisd keys add "$KEY_NAME" --keyring-backend "$KEYRING_BACKEND"
```

`"$KEY_NAME"` is a custom key name youu choose.

`"$KEYRING_BACKEND"` is selected from `os` or `file` or `test` value \(default is `os`\).

Then setup a password to confirm your transactions.

9.2 Export existing OSMO address:

```text
$ osmosisd keys add "$KEY_NAME" --keyring-backend "$KEYRING_BACKEND" --recover
```

Enter your mnemonic phrase to get access to your existing OSMO address. 

10. To make the reward come once a day, set up a cronjob:

```text
crontab -e
```

11. Create a bash script file for stake, e. g. `osmosis_stake.sh`.

12. Paste the following script to the file:

```text
#!/bin/bash
GREEN='\033[0;32m'
RED='\033[0;31m'
NC='\033[0m' # No Color
DELEGATOR='Delegator_address' # your address created or imported
VALIDATOR='Validator_address' # can get from Keplr app or Mintscan block explorer
PASWD='Your_pass_from_keyring'
ACC_NAME='Your_account_name'
NODE='htps://???' # Don't change that endpoint
KEYRING='file' # (if you selected "os" or "test", paste it instead)
CHAIN_ID='osmosis-1' # Don't change this parameter 
for ((; ;));
 do
        BAL=$(osmosisd query bank balances ${DELEGATOR} --node ${NODE}  -o json --output=json --denom=uosmo | jq -r '.amount'); #current balance
        echo ${BAL}
        echo -e "BALANCE: ${GREEN}${BAL}${NC} uosmo\n"
        echo -e "Claim rewards\n"
        echo -e "${PASWD}\n" | osmosisd tx distribution withdraw-rewards ${VALIDATOR} --from ${ACC_NAME} --node ${NODE} --keyring-backend ${KEYRING} --chain-id ${CHAIN_ID} -y #claim rewards
        for (( timer=10; timer>0; timer-- ))
        do
                printf "* sleep for ${RED}%02d${NC} sec\r" $timer
                sleep 1
        done
        BAL=$(osmosisd query bank balances ${DELEGATOR} --node ${NODE} -o json --output=json --denom=uosmo | jq -r '.amount'); # balance after claim
        echo -e "BALANCE: ${GREEN}${BAL}${NC}uosmo\n"
        echo -e "Stake ALL\n"
        echo -e "${PASWD}\n" | osmosisd tx staking delegate ${VALIDATOR} ${BAL}uosmo --from ${ACC_NAME} --node ${NODE} --keyring-backend ${KEYRING} --chain-id ${CHAIN_ID} -y #delegate claim rewards
done
```

Filled bash file for staking to [Staketab](https://staketab.com/) is the following \(just paste your Osmosis address to the `DELEGATOR` field, password to the `PASWD` field and Account name to the `ACC_NAME` field\):

```text
#!/bin/bash
GREEN='\033[0;32m'
RED='\033[0;31m'
NC='\033[0m' # No Color
DELEGATOR='osmoXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX' # your address created or imported
VALIDATOR='osmovaloper1t29pjdugzyetxaehf62a8x7hhq4u0v4un9mxg5' 
PASWD='Your_pass_from_keyring' 
ACC_NAME='Your_account_name'
NODE='https://???' # Don't change that endpoint
KEYRING='file' # (if you selected "os" or "test", paste it instead)
CHAIN_ID='osmosis-1' # Don't change this parameter 
for ((; ;));
 do
        BAL=$(osmosisd query bank balances ${DELEGATOR} --node ${NODE}  -o json --output=json --denom=uosmo | jq -r '.amount'); #current balance
        echo ${BAL}
        echo -e "BALANCE: ${GREEN}${BAL}${NC} uosmo\n"
        echo -e "Claim rewards\n"
        echo -e "${PASWD}\n" | osmosisd tx distribution withdraw-rewards ${VALIDATOR} --from ${ACC_NAME} --node ${NODE} --keyring-backend ${KEYRING} --chain-id ${CHAIN_ID} -y #claim rewards
        for (( timer=10; timer>0; timer-- ))
        do
                printf "* sleep for ${RED}%02d${NC} sec\r" $timer
                sleep 1
        done
        BAL=$(osmosisd query bank balances ${DELEGATOR} --node ${NODE} -o json --output=json --denom=uosmo | jq -r '.amount'); # balance after claim
        echo -e "BALANCE: ${GREEN}${BAL}${NC}uosmo\n"
        echo -e "Stake ALL\n"
        echo -e "${PASWD}\n" | osmosisd tx staking delegate ${VALIDATOR} ${BAL}uosmo --from ${ACC_NAME} --node ${NODE} --keyring-backend ${KEYRING} --chain-id ${CHAIN_ID} -y #delegate claim rewards
done
```

13. Setup a time and path to your script:

```text
08 15   * bash /path/to/your/script/osmosis_stake.sh
```

14. Make your script executable:

```text
chmod +x osmosis_stake.sh
```

15. Run your script:

```text
./osmosis_stake.sh
```

Tokens are on the journey to stake and will be used by the staking provider soon. Just wait for your rewards from now.

## Sources

1. [CyberObiOne readme](https://github.com/CyberObiOne/crypto/tree/main/osmosis).

2. [CyberObiOne script](https://github.com/CyberObiOne/crypto/blob/main/osmosis/osmosis_comission.sh).

