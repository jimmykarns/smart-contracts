## Introduction
This specific branch is for mutation testing.

## Instructions
1. Install eth_vertigo: `pip3 install eth_vertigo`
2. Install ganache-cli (if not installed already): `npm i ganache-cli`
3. Clone this repo
4. `cd ./PermissionGroups`
5. `npm ci`
6. Spawn 5 ganache-cli instances in 5 separate terminals / tabs: 
    ```
    ganache-cli -l 8000000 -e 1000 -p 8545
    ganache-cli -l 8000000 -e 1000 -p 8546
    ganache-cli -l 8000000 -e 1000 -p 8547
    ganache-cli -l 8000000 -e 1000 -p 8548
    ganache-cli -l 8000000 -e 1000 -p 8549
    ```
7. Run `vertigo run --network mutNet1 --network mutNet2 --network mutNet3 --network mutNet4 --network mutNet5 --output mutOutput.txt`

## Notes
- Later versions of Truffle (>= 4.1.15) break the `beforeAll` hook. That's why specific truffle version must be used.
- If any port number needs to be changed, edit the port number in `truffle-config.js` as well.