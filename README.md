# EigenLayer AVS Context Window Prompts


“How can we modify our new developer tooling to support llm generation of AVS code as a first class citizen?”   

.. and thankfully [The Andrej has spoken](https://x.com/karpathy/status/1899876370492383450)  

   
<img width="400" alt="image" src="https://github.com/user-attachments/assets/afa768ad-67bb-4279-96fe-c5771b996e8f" />



## Prompt to build the prompt

```
write a simple context window prompt markdown file for building an AVS on EigenLayer

the context window prompt should help the user perform the following steps:

part 1) design their AVS
design the operator work (binary) compute
design the validation of that work in a decentralized way
define the successful behaviors for rewards distributions
define malicious behaviors for rewards withholding, operator ejection and slashing.

b) implement the AVS. The implementation should
mimic: https://github.com/Layr-Labs/hello-world-avs
implement any custom logic needed for the service manager under contracts/src folder
implement any operator code or binaries in the /operator folder
implement code under test folder that initiates the AVS flow
provide a README file with instructions on how to run the operator binary
```
