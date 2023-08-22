cargo contract instantiate --constructor new --args "false" --suri //Alice --salt $(date +%s) -x



//instantiate response
 Event Balances ➜ Withdraw
         who: 5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY
         amount: 3.533174218mUNIT
       Event Balances ➜ Reserved
         who: 5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY
         amount: 259.63mUNIT
       Event Contracts ➜ CodeStored
         code_hash: 0x36b8bc3ca9c34d45d4ed150517586e6f74dd5ac33acee79789c212504fbf8c35
       Event System ➜ NewAccount
         account: 5FHnWHFnUQcEdQYakWBmcGtue5WfuTVUVJWLUY12DN2z1JtP
       Event Balances ➜ Endowed
         account: 5FHnWHFnUQcEdQYakWBmcGtue5WfuTVUVJWLUY12DN2z1JtP
         free_balance: 100.765mUNIT
       Event Balances ➜ Transfer
         from: 5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY
         to: 5FHnWHFnUQcEdQYakWBmcGtue5WfuTVUVJWLUY12DN2z1JtP
         amount: 100.765mUNIT
       Event System ➜ NewAccount
         account: 5HXJiwDZTVYtK1JCm41FVcjas7pMsNexTvMmpvkYoCBZqjDL
       Event Balances ➜ Endowed
         account: 5HXJiwDZTVYtK1JCm41FVcjas7pMsNexTvMmpvkYoCBZqjDL
         free_balance: 1mUNIT
       Event Balances ➜ Transfer
         from: 5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY
         to: 5HXJiwDZTVYtK1JCm41FVcjas7pMsNexTvMmpvkYoCBZqjDL
         amount: 1mUNIT
       Event Contracts ➜ Instantiated
         deployer: 5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY
         contract: 5HXJiwDZTVYtK1JCm41FVcjas7pMsNexTvMmpvkYoCBZqjDL
       Event Balances ➜ Transfer
         from: 5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY
         to: 5FHnWHFnUQcEdQYakWBmcGtue5WfuTVUVJWLUY12DN2z1JtP
         amount: 100.005mUNIT
       Event TransactionPayment ➜ TransactionFeePaid
         who: 5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY
         actual_fee: 3.533174218mUNIT
         tip: 0UNIT
       Event System ➜ ExtrinsicSuccess
         dispatch_info: DispatchInfo { weight: Weight { ref_time: 3533162223, proof_size: 9095 }, class: Normal, pays_fee: Yes }


//contract calls

         cargo contract call --contract 5HXJiwDZTVYtK1JCm41FVcjas7pMsNexTvMmpvkYoCBZqjDL --message get --suri //Alice -x
         cargo contract call --contract 5HXJiwDZTVYtK1JCm41FVcjas7pMsNexTvMmpvkYoCBZqjDL --message flip --suri //Alice -x
