# avs-context-prompt
(EigenLayer AVS context window prompts)

“How can we modify our new developer tooling to support llm generation of AVS code as a first class citizen?”   

.. and thankfully [The Andrej has spoken](https://x.com/karpathy/status/1899876370492383450)
<img width="652" alt="image" src="https://github.com/user-attachments/assets/afa768ad-67bb-4279-96fe-c5771b996e8f" />



## Prompt to build the prompt


Share

You said:
write a simple context window prompt markdown file for building an AVS on EigenLayer

the context window prompt should help the user perform the following steps:

A) design their AVS
1) design the operator work (binary) compute
2) design the validation of that work in a decentralized way
3) define the successful behaviors for rewards distributions
4) define malicious behaviors for rewards withholding, operator ejection and slashing.

b) implement the AVS. The implementation should
1) mimic:  https://github.com/Layr-Labs/hello-world-avs
2) implement any custom logic needed for the service manager under contracts/src folder
3) implement any operator code or binaries in the /operator folder
4) implement code under test folder that initiates the AVS flow
5) provide a README file with instructions on how to run the operator binary
