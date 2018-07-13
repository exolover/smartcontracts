# EXO Token smart contract  
Status: Contract deployed  
https://etherscan.io/token/0xe58e751aba3b9406367b5f3cbc39c2fa9b519789#tokenInfo  

## Special contract method review  
### Token distribution from Cab
In addition to standard ERC20 methods, EXOToken  smart contract support `multiTransfer` method
for batch token distribution from CAB. This allows spend much less Gas and Time for this operation.  
Method recieve two arrays as params:  
- array of addresses;  
- array of amounts for each address;  
Under the terms of the campaign, this method available just for initial token keeper account.  
Method verify:  
- number of adress array elements >0 and <=255 (due to Gas Limit per block);  
- length of two arrays are equal;  
- each element in array of addresses is not zero address;  
- sum of all elements in  array of amounts not more then sender balance of tokens;  
**!!! Address validation must be provided by the caller!!!**  

Method emit events:  
`Transfer` - on each transfer in the batch;  
`BatchDistrib` - with count and sum all transfers in the batch.  
**!!! It's strongly recommended for smart contract operator to catch and analysis these events for prevent token distribution errors.**  

### Burn tokens
`burn` method is implemented in smart contract for **ProofOfConnect** functionality support.   



