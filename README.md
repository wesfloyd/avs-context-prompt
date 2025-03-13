# EigenLayer AVS Context Window Prompts

## Motivation

“How can we modify our new developer tooling to support llm generation of AVS code as a first class citizen?”   

.. and thankfully [The Andrej has spoken](https://x.com/karpathy/status/1899876370492383450)  

<img width="400" alt="image" src="https://github.com/user-attachments/assets/afa768ad-67bb-4279-96fe-c5771b996e8f" />
  

[Vibecoding stack](https://x.com/DennisonBertram/status/1899641887922725223) is the preferred mode for modern developers.
  
Likely this flow will become more relevant as [agents become more involved](https://x.com/weswfloyd/status/1899814487038853453) in development cycles.  



## End to End Flow

Step 1) Idea: User defines their AVS goals or design at a high level (minimal prompt). eg "I want to build an AVS where an Operator generates cat images via LLM inference and their work is validated using a separate set of LLMs to measure their accuracy".

Step 2) Design: User sends their prompt and the standard [avs-design-context-window-prompt.md](./avs-design-context-window-prompt.md) to the LLM. This results in a detailed avs-custom-development-plan.md customized for their AVS.

Step 3) Implementation: User feeds their avs-custom-development-plan.md file to Claude Code or Cursor along with the standard [avs-coding-context-window-prompt.md](./avs-coding-context-window-prompt.md) for implementation to a codebase including deployment code.

Step 4) Deployment [todo]

Step 5) Testing [todo determine how to best approach this]

Result: User gets a functional, working AVS prototype they can deploy to devnet or testnet.

Todos:
Build avs-design-context-window-prompt.md
Use it to generate example: "EigenLayer AVS development plan"s

Rebuild avs-coding-context-window-prompt.md




