# EigenLayer AVS Context Window Prompts


“How can we modify our new developer tooling to support llm generation of AVS code as a first class citizen?”   

.. and thankfully [The Andrej has spoken](https://x.com/karpathy/status/1899876370492383450)  

<img width="400" alt="image" src="https://github.com/user-attachments/assets/afa768ad-67bb-4279-96fe-c5771b996e8f" />

[Vibecoding stack](https://x.com/DennisonBertram/status/1899641887922725223) is the preferred mode for modern developers. Likely this flow will become more relevant as [agents become more involved](https://x.com/weswfloyd/status/1899814487038853453) in development cycles.


## End to End Flow

Step 1:  User defines their AVS goals or design at a high level (minimal prompt). eg "I want to build an AVS where an Operator generates cat images via LLM inference and their work is validated using a separate set of LLMs to measure their accuracy".

Step 2: User sends their prompt and the standard avs-coding-context-window-prompt.md to the LLM. This results in a detailed "EigenLayer AVS development plan" customized for their AVS.

Step 3: User feeds their avs-custom-development-plan.md file to Claude Code or Cursor along with the standard avs-coding-context-window-prompt.md for implementation to a codebase including deployment code.

Step 4: Testing? [todo determine how to best approach this]

Result: User gets a functional, working AVS prototype they can deploy to devnet or testnet.

Todos:
Build avs-design-context-window-prompt.md
Use it to generate example: "EigenLayer AVS development plan"s

Rebuild avs-coding-context-window-prompt.md





## Prompt to build the prompt that vibecodes the solution

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
