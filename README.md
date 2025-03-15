# Idea to AVS Pipeline
via "EigenLayer AVS Context Window Prompts for LLMs"  


## Goals

1) “How can we modify our new developer tooling to support llm generation of AVS code as a first class citizen?”   
2) "How can we build our tooling so that a non-technical person can launch a working AVS **prototype**?"
3) Enable the user to learn AVS Design while they are generating design and code assets alongside the LLM.

The outputs from this pipeline do not need to generate Mainnet ready code. They simply need to provide enough value to prove the AVS idea quickly.

## Background
  
[The Andrej has spoken](https://x.com/karpathy/status/1899876370492383450)  

<img width="400" alt="image" src="https://github.com/user-attachments/assets/afa768ad-67bb-4279-96fe-c5771b996e8f" />
  

The [Vibecoding stack](https://x.com/DennisonBertram/status/1899641887922725223) is the preferred mode for modern developers.
  
This flow will become more relevant as [agents become more involved](https://x.com/weswfloyd/status/1899814487038853453) in future development tasks.  



## End to End Flow

**Step 1)** Idea to Design: 
User defines their AVS goals or design at a high level (minimal prompt). 
Example prompt:
```
Generate an EigenLayer AVS design file named avs-design-formyidea.md.
Use the attached avs-design-context-window-prompt.md for guidance.
Operator Work: Design an AVS where a single Operator **generates cat images** via LLM inference.
Validation: The work is validated using at least two other operators set of LLMs to measure their accuracy. The validating operators should assign a percentage "accuracy rating" between 0% and 100%. 
Rewards: validating operators get rewarded if they respond with any accuracy rating. Mark the Operator that generated the original image for a reward if the aversage validator accuracy was greater than 90%
Slashing: slash the generating Operator if their average validator accuracy was less than 20%
```

**Step 2)** Design to Development Plan: 
User sends their prompt and the standard [avs-design-context-window-prompt.md](./avs-design-context-window-prompt.md) to the LLM. This results in a detailed avs-custom-development-plan.md customized for their AVS.

**Step 3)** Implementation: 
User feeds their avs-design-formyidea.md file to a coding-centric llm (Claude Code or Cursor) along with an interchangeable set of standard context window files such as:
- [avs-**default**-coding-context-window-prompt.md](./avs-coding-context-window-prompt.md) for standard hello world AVS implementation to a codebase including deployment code.
- `avs-othentic-coding-context-window-prompt.md` to generate code that could be ran on [Othentic](https://docs.othentic.xyz/main).
- `avs-wavs-coding-context-window-prompt.md` to generate code that could be ran on [WAVS](https://www.wavs.xyz/)
  
**Step 4)** Deployment:
[todo determine how to leverage llms to simplify the contract deployment script generation w/forge]

**Step 5)** Testing:
[todo determine how to leverage an llm for this]

**Result:** User gets a functional, working AVS prototype they can deploy to devnet or testnet.

Todos:
- Refine Ideation step to prompt the user with suggestion and feedback loops.
- Split the Design asset into a high level design and lower level design. Add to lower level design the specific organization of tasks to Operators (single, multiple, round robin, w/ vs w/out aggregator). Add architecture diagram generation.
