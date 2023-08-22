This file contains all the steps I have done in part 3.

node 1 and node 2 keys

#command for creating below key
----------------------------------------------- NODE 1 ---------------------------------------------------------------------------------------------------
./target/release/node-template key generate --scheme Sr25519 --password-interactive

password is qwe

phrase : item ozone return nest then sting hour team radar enrich winter couch
aura key : 5Fhi7XW3AUUmxje2LpjvnJK8j2uAkrJ5u8x2HCpTjWg5yVJK



node - 1 grandpa key generation
./target/release/node-template key inspect --password-interactive --scheme Ed25519 "item ozone return nest then sting hour team radar enrich winter couch"


password is qwe

phrase : item ozone return nest then sting hour team radar enrich winter couch
grandpa key : 5DuLGmrpn43RJyw2JpCEk2oSkiCEtpgAiGwfrZBsTJJh81kj



----------------------------------------------- NODE 2 ---------------------------------------------------------------------------------------------------

./target/release/node-template key generate --scheme Sr25519 --password-interactive

password is qwe

phrase : south black soft doll flee snow lawn holiday museum steak act use
aura key : 5DCZ6D45XCTyCGV3vWL7FcDVp6gHAMAeiUD1G3VdUDwu5HER



node - 1 grandpa key generation
./target/release/node-template key inspect --password-interactive --scheme Ed25519 "south black soft doll flee snow lawn holiday museum steak act use"


password is qwe

phrase : south black soft doll flee snow lawn holiday museum steak act use
grandpa key : 5E5Tsk64hQM9355d74DdM1QCE8m3HV2Hf1dHm9dAZc85BeaK

------------------------------------------------- CREATE CUSTOM CHAIN SPECIFICTION --------------------------------------------------------------------

./target/release/node-template build-spec --disable-default-bootnode --chain local > customSpec.json

------------------------------------------------- CONVERT CHAIN SPECIFICTION TO RAW FORMAT ------------------------------------------------------------
./target/release/node-template build-spec --chain=customSpec.json --raw --disable-default-bootnode > customSpecRaw.json



-------------------------------------------------------- PURGE CHAINS --------------------------------------------------------------------------------
#in case we want to purge the chains.

./target/release/node-template purge-chain --base-path "/tmp/node01" --chain local
./target/release/node-template purge-chain --base-path "/tmp/node02" --chain local


-------------------------------------------------------- ADD KEYS TO KEYSTORE --------------------------------------------------------------------------------

#NODE 1
#aura

./target/release/node-template key insert --base-path /tmp/node01\
    --chain customSpecRaw.json\
    --scheme Sr25519\
    --suri "item ozone return nest then sting hour team radar enrich winter couch"\
    --password-interactive\
    --key-type aura\
#grandpa

./target/release/node-template key insert \
    --base-path /tmp/node01 \
    --chain customSpecRaw.json \
    --scheme Ed25519 \
    --suri "item ozone return nest then sting hour team radar enrich winter couch" \
    --password-interactive \
    --key-type gran \


#NODE 2
#aura
./target/release/node-template key insert --base-path /tmp/node02 \
    --chain customSpecRaw.json \
    --scheme Sr25519 \
    --suri "south black soft doll flee snow lawn holiday museum steak act use" \
    --password-interactive \
    --key-type aura \
#grandpa
./target/release/node-template key insert \
    --base-path /tmp/node02 \
    --chain customSpecRaw.json \
    --scheme Ed25519 \
    --suri "south black soft doll flee snow lawn holiday museum steak act use" \
    --password-interactive \
    --key-type gran \

---- show inserted keys ------

ls /tmp/node01/chains/local_testnet/keystore
ls /tmp/node02/chains/local_testnet/keystore


-------------------------------------------------------- START BLOCKCHAIN -------------------------------------------------------------------------

./target/release/node-template \
    --base-path /tmp/node01 \
    --chain ./customSpecRaw.json \
    --port 30333 \
    --rpc-port 9933 \
    --telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
    --validator \
    --rpc-methods Unsafe\
    --name MyNode01\
    --password-interactive\








---------- STARTING NODES ---------------

#NODE1
sudo
    ./target/release/node-template \
    --base-path /tmp/node01 \
    --chain ./customSpecRaw.json \
    --port 30333 \
    --rpc-port 9933 \
    --telemetry-url "wss://telemetry.polkadot.io/submit/ 0"\
    --validator\
    --rpc-methods Unsafe \
    --name MyNode01 \
    --password-interactive \

#NODE2
sudo
    ./target/release/node-template\
    --base-path /tmp/node02\
    --chain ./customSpecRaw.json\
    --port 30334 \
    --rpc-port 9934 \
    --telemetry-url "wss://telemetry.polkadot.io/submit/ 0"\
    --validator\
    --rpc-methods Unsafe\
    --name MyNode02\
    --bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWLmrYDLoNTyTYtRdDyZLWDe1paxzxTw5RgjmHLfzW96SX\
    --password-interactive\


-----------------------------------------------------------------------------------------------



