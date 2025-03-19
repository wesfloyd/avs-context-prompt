# EigenLayer AVS Idea to Prototype Pipeline
*via "EigenLayer AVS Context Window Prompts for LLMs"*




## Goals

1) Modify our new developer tooling to support llm generation of AVS code as a first class citizen   
2) Build our tooling so that a non-technical person can launch a working AVS **prototype**"
3) Enable the user to learn AVS Design while they are generating design and code assets alongside the LLM.

*The outputs from this pipeline do not need to generate Mainnet ready code. They simply need to provide enough value to prove the AVS idea quickly.*

## Background
  
[The Andrej has spoken](https://x.com/karpathy/status/1899876370492383450)  "In 2025 the docs should be a single your_project.md text file that is intended to go into the context window of an LLM."

The [Vibecoding stack](https://x.com/DennisonBertram/status/1899641887922725223) is the preferred mode for modern developers.
  
This flow will become more relevant as [agents become more involved](https://x.com/weswfloyd/status/1899814487038853453) in future development tasks.  



## End to End Flow

**Step 1)** AVS Idea Refinement:
User interacts with LLM to determine whether their 

**Step 2)** AVS Idea to Design: 
User defines their AVS goals or design at a high level in a minimal custom prompt for the llm ([example here](examples/avs-design-prompt-figs.md)).

User sends their custom prompt to the LLM along with:
- The standard [avs-design-context-window-prompt.md](design/avs-design-context-window-prompt.md)
- [Repomix](https://repomix.com/) compressed copies of EigenLayer docs and contracts. _in the near future, MCP server endpoints_ will replace these.   

This results in a detailed `avs-design-output-formyidea.md` customized for their AVS.


**Step 3)** AVS Design to Prototype:
User feeds their `avs-design-output-formyidea.md` file to a coding-centric llm (Claude Code or Cursor) along with an interchangeable set of standard context window files (_or in the near future, MCP server endpoints_) such as:
- [avs-**default**-coding-context-window-prompt.md](prototyping/avs-coding-context-window-prompt.md) for standard hello world AVS implementation to a codebase including deployment code.
- `avs-othentic-coding-context-window-prompt.md` to generate code that could be ran on [Othentic](https://docs.othentic.xyz/main).
- `avs-wavs-coding-context-window-prompt.md` to generate code that could be ran on [WAVS](https://www.wavs.xyz/)

**Result:** User gets a functional, working AVS prototype they can deploy to devnet or testnet.

**Step 4)** Deployment:
[todo determine how to leverage llms to simplify the contract deployment script generation w/forge]

**Step 5)** Testing:
[todo determine how to leverage an llm for this]


## Future Enhancements:
- Add architecture diagram generation to design stage.
- Design stage can be modified to product a "level of effort" to be used for high level planning of developer cost and timelines to implement their AVS idea.
- Refine Ideation step to prompt the user with suggestion and feedback loops.
- Moving from Context Window files to MCP server endpoints for enhanced LLM outputs.

