# AVS Design: Feline Image Generation Service (FIGS)

## Part 1: AVS Design

### 1. AVS Purpose and Scope

The Feline Image Generation Service (FIGS) is designed to provide high-quality, on-demand cat images through a decentralized network of operators running LLM inference. This service addresses several key needs in the web3 ecosystem:

- **Decentralized AI Content Generation**: Rather than relying on centralized AI image generation services, FIGS distributes this capability across multiple independent operators.
- **Quality-Assured Content**: Through a validation mechanism that evaluates image quality and accuracy.
- **Permissionless Infrastructure**: Any qualified operator can join the network, stake tokens, and participate in the image generation ecosystem.

FIGS brings value in a trust-minimized, decentralized manner by:
- Reducing single points of failure in AI image generation
- Creating economic incentives for high-quality image generation
- Establishing a framework for quality validation that doesn't rely on a central authority
- Enabling dApps to access AI-generated content without depending on centralized providers

### 2. Designing the Operator "Work" (aka task)

#### Operator Task Definition

**Generator Operator Task**: 
The primary task involves running LLM inference to generate cat images based on specific prompts. Generator operators must:
- Receive image generation prompts from users or the protocol
- Process these prompts through their LLM infrastructure
- Generate high-quality cat images that match the specified requirements
- Return the generated images in a standardized format to the network

**Validator Operator Task**:
Validator operators are responsible for evaluating the quality and accuracy of generated images using their own LLM infrastructure. They must:
- Receive generated cat images along with the original prompts
- Analyze the images using their LLM to determine how well they match the prompt requirements
- Assign an accuracy rating between 0% and 100% based on predefined criteria
- Submit their validation results back to the network

#### Input and Output

**Generator Input**:
- Text prompts specifying the desired cat image characteristics (e.g., "a ginger cat sitting on a windowsill at sunset")
- Optional parameters such as image resolution, style preferences, etc.

**Generator Output**:
- The generated cat image in a standardized format (e.g., PNG, JPG)
- Metadata about the generation process, including processing time, model used, etc.

**Validator Input**:
- The original prompt
- The generated cat image
- Reference to the Generator Operator's identifier

**Validator Output**:
- Accuracy rating (0-100%)
- Validation metadata, including reasoning for the assigned rating
- Validator's cryptographic signature

### 3. Decentralized Validation

#### Validation Mechanism

The FIGS validation system relies on multiple validator operators independently assessing each generated image:

1. When a Generator Operator submits a cat image, the protocol randomly selects at least two Validator Operators from the available pool.
2. Each selected Validator uses their LLM to analyze how well the image matches the original prompt.
3. Validators evaluate multiple factors, including:
   - Subject accuracy (Is it actually a cat?)
   - Attribute accuracy (Does it match specified characteristics like color, position, or background?)
   - Image quality (Is the image clear, coherent, and visually appealing?)
   - Prompt adherence (Does the image follow all aspects of the prompt?)
4. Based on these factors, each Validator assigns a percentage score from 0% to 100%.

#### Consensus Rules

Consensus is reached through aggregation of validator scores:

1. The protocol collects all validator ratings for a given image.
2. An average accuracy score is calculated from all validator submissions.
3. This average score determines the outcome for the Generator Operator:
   - Scores ≥ 90%: Generator is considered excellent and receives full rewards
   - Scores between 20% and 90%: Generator is considered acceptable but receives proportional rewards
   - Scores < 20%: Generator is considered poor quality or malicious and faces penalties

In case of significant deviation between validator scores (e.g., difference > 30%), additional validators may be requested to provide ratings to ensure fairness.

### 4. Rewards Distribution for Successful Behaviors

#### Reward Conditions

**Generator Operators**:
- Receive rewards when their generated cat images earn an average validator accuracy rating of 90% or higher
- The reward amount is proportional to the complexity of the prompt and the computational resources required
- Consistent high-performance (maintaining >90% ratings over time) results in reputation bonuses and priority for future tasks

**Validator Operators**:
- Receive rewards for each validation they perform, regardless of the rating they assign
- Validator rewards are smaller than generator rewards but require less computational resources
- Validators whose ratings consistently align with the consensus receive reputation bonuses

#### Payment Mechanism

Rewards are distributed using the following mechanism:

1. For each successful cat image generation cycle (submission + validation), tokens are allocated from the protocol treasury or user payments.
2. Distribution occurs at the end of each epoch (defined as a set number of blocks, e.g., 7,200 blocks or approximately 1 day).
3. The smart contract automatically distributes rewards based on recorded performance metrics.
4. Tokens are sent directly to operator-controlled addresses without requiring manual claims.
5. A small percentage of each reward (e.g., 5%) is directed to a community development fund to ensure protocol sustainability.

### 5. Penalties for Malicious Behaviors

#### Malicious Activity Definition

The following behaviors are considered malicious or negligent within the FIGS network:

**For Generator Operators**:
- Submitting images that are not cats or do not reasonably match the prompt requirements
- Submitting low-quality, distorted, or incomplete images
- Copying or plagiarizing existing images instead of generating new ones
- Attempting to game the system by colluding with validators
- Consistently producing images that receive low accuracy ratings

**For Validator Operators**:
- Providing arbitrary ratings without proper evaluation
- Colluding with generator operators to provide artificially high ratings
- Consistently providing outlier ratings that deviate significantly from consensus
- Failing to complete assigned validations within the specified timeframe

#### Punitive Actions

**Reward Withholding**:
- Generator Operators with average accuracy ratings below 90% receive reduced or no rewards for the affected tasks
- Validator Operators who provide ratings that consistently deviate significantly from consensus may have rewards reduced

**Operator Ejection**:
- Generator Operators whose images consistently receive ratings below 40% over an extended period (e.g., 10 consecutive tasks or a 7-day period) may be temporarily suspended
- Operators found to be deliberately gaming the system through collusion are permanently ejected from the network

**Slashing**:
- Generator Operators whose images receive an average accuracy rating below 20% have a portion of their staked tokens slashed
- The slashing amount is proportional to the severity and frequency of low-quality submissions
- First offense: 1% of stake
- Second offense: 5% of stake
- Third and subsequent offenses: 10% of stake
- Validators proven to be colluding with generators may also face slashing penalties

## Technical Implementation Considerations

### Smart Contract Architecture

The FIGS protocol will require several key smart contracts:

1. **Registry Contract**: Manages operator registration, stake deposits, and network participation
2. **Task Distribution Contract**: Handles prompt distribution and assignment to generator operators
3. **Validation Assignment Contract**: Randomly selects validators for each generated image
4. **Reward & Slashing Contract**: Manages economic incentives and penalties based on performance
5. **Governance Contract**: Enables parameter adjustments and protocol upgrades through community voting

### Operator Infrastructure Requirements

**Generator Operators** must maintain:
- High-performance computing resources capable of running LLM inference
- Reliable network connectivity
- Sufficient storage for model weights and generated images
- Proprietary or third-party LLM access with image generation capabilities

**Validator Operators** must maintain:
- LLM infrastructure capable of image analysis and rating
- Reliable network connectivity
- Lower computational requirements than generators, but still substantial

### Data Flow and Storage

1. Prompts and generated images will be stored on a combination of:
   - IPFS for decentralized storage
   - Arweave for permanent storage when needed
   - Operator-managed databases for quick retrieval

2. Validation results and performance metrics will be:
   - Recorded on-chain in a compressed format
   - Stored in full detail off-chain with verifiable references on-chain

## Roadmap and Future Enhancements

### Phase 1: Core Functionality
- Basic cat image generation and validation
- Simple reward and slashing mechanisms
- Limited prompt complexity

### Phase 2: Enhanced Features
- Support for more complex and specific prompts
- Integration with popular dApps and platforms
- Reputation system for operators

### Phase 3: Expansion
- Support for additional animal types and image categories
- Advanced styling options and image manipulation
- Integration with other AVS services in the EigenLayer ecosystem

### Phase 4: Full Decentralization
- Community governance of all protocol parameters
- Open-source operator software
- Cross-chain functionality

## Conclusion

The Feline Image Generation Service (FIGS) represents an innovative application of EigenLayer's restaking capabilities, bringing AI-powered content generation into the decentralized world. By combining strong economic incentives, robust validation mechanisms, and fair penalties for malicious behavior, FIGS creates a sustainable ecosystem for high-quality cat image generation that can serve as a model for other decentralized AI services.
