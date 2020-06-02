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
4. `npm ci`
5. `npx truffle compile`
6. Spawn buidler node in a separate terminal: 
    ```
    npx buidler node
    ```
7. Run 
    ```
    vertigo run --network mutNet1 --exclude ./contracts/Dao --exclude ./contracts/mock --exclude ./contracts/utils/zeppelin --exclude ./contracts/wrappers --exclude ./contracts/Migrations.sol --output mutOutput.txt
    ```

## Notes
- Later versions of Truffle (>= 4.1.15) break the `beforeAll` hook. That's why specific truffle version must be used.
- ~~If any port number needs to be changed, edit the port number in `truffle-config.js` as well.~~