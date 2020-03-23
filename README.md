## Introduction
This specific branch is for mutation testing.

## Setup Requirements (AWS instructions)
- Python 3.7
    - `sudo apt-get install libssl-dev libffi-dev zlib1g-dev`
    - `wget https://www.python.org/ftp/python/3.7.4/Python-3.7.4.tgz`
    - `tar xzf Python-3.7.4.tgz`
    - `cd Python-3.7.4`
    - `./configure --enable-optimizations`
    - `make altinstall`
    - `rm /usr/src/Python-3.7.4.tgz`
    - Set default Python version to be 3.7.4 via `update-alternatives`
      - `sudo update-alternatives --install /usr/bin/python python /home/desmond/Python-3.7.4/python 1`
      - `sudo update-alternatives --config python`
    - `sudo apt install python3-pip`


## Instructions
1. Install eth_vertigo: `pip3 install eth_vertigo` or `python -m pip install eth_vertigo`
2. Install ganache and ganache-cli (if not installed already): `npm i -g ganache` & `npm i ganache-cli`
3. Clone this repo
4. `cd ./PermissionGroups`
5. `npm ci`
6. `npx truffle compile`
7. Spawn 5 ganache-cli instances in 10 separate terminals / tabs: 
    ```
    ganache-cli -l 8000000 -e 1000000 -p 8545
    ganache-cli -l 8000000 -e 1000000 -p 8546
    ganache-cli -l 8000000 -e 1000000 -p 8547
    ganache-cli -l 8000000 -e 1000000 -p 8548
    ganache-cli -l 8000000 -e 1000000 -p 8549
    ganache-cli -l 8000000 -e 1000000 -p 8550
    ganache-cli -l 8000000 -e 1000000 -p 8551
    ganache-cli -l 8000000 -e 1000000 -p 8552
    ganache-cli -l 8000000 -e 1000000 -p 8553
    ganache-cli -l 8000000 -e 1000000 -p 8554
    ```
8. Run 
    ```
    vertigo run 
    --network mutNet1 --network mutNet2 --network mutNet3 --network mutNet4 --network mutNet5 
    --network mutNet6 --network mutNet7 --network mutNet8 --network mutNet9 --network mutNet10
    --output mutOutput.txt
    ```

## Notes
- Later versions of Truffle (>= 4.1.15) break the `beforeAll` hook. That's why specific truffle version must be used.
- If any port number needs to be changed, edit the port number in `truffle-config.js` as well.