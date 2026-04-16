# Panel Discussion Session Notes
## AI Research: Multimodal Learning, Grounding, and Future Directions

**Panel Members:** Dan Roth, Ruhi Sarikaya, Karen Livescu, Heng Ji, Manling Li, Kevin Small  
**Chair:** Hao Peng  
**Topic:** The role of multimodality in achieving true AI intelligence

---

## 1. THE SYMBOL GROUNDING PROBLEM

### What Is It?
Language models learn from text alone. But words are just symbols—they're representations of things in the real world. The question is: can AI truly understand meaning by reading words, or does it need to experience the physical world like humans do?

In 2020, researchers Emily Bender and Alexander Koller published an influential paper arguing that text-only models **cannot** truly understand language meaning. Their reasoning: meaning requires a connection between words and real-world experiences. If you only read about "fire" but never feel heat, do you really understand fire?

### The Core Issue
- Language models work with patterns in text, not actual understanding of what those words represent
- Humans learn meaning through bodies, senses, and physical interaction with the world
- Models trained only on text lack this grounding in reality
- This is called the "symbol grounding problem"

**Real-world impact:** A model might produce grammatically perfect sentences about a concept it doesn't truly understand. It's like a parrot repeating words without knowing what they mean.

### Why It Matters Now
The panel discussed whether recent multimodal models—those trained on images, video, and text together—can solve this problem. The evidence is mixed. Some findings show these models do capture some real-world concepts better than text-only models. But they still lack true embodied experience (movement, touch, consequences of actions).

**Sources:** Bender & Koller (2020) "Climbing Towards NLU"; research from MIT and Royal Society on multimodal grounding

---

## 2. MULTIMODAL LEARNING: MORE THAN JUST TEXT

### What Is Multimodal?
Instead of learning from only text, multimodal models learn from:
- Text (words and sentences)
- Images (visual information)
- Video (motion and temporal sequences)
- Audio (sounds and spoken language)
- Sensor data (from robots: touch, temperature, position)

These different information types together provide richer understanding.

### Why Multimodal Helps
**Example from the panel:** Understanding how a crow uses a tool requires seeing space, timing, and physical cause-and-effect. Text alone makes this extremely difficult. The model needs to see the action.

- Robots performing tasks: A robot picking up an object needs visual feedback AND language instruction AND knowledge of forces/weight
- Reasoning about the physical world: "If I move this forward 10 steps, what happens?" requires spatial understanding that language struggles to capture
- Scientific discovery: Understanding chemical reactions or biological processes works better with visual and experimental data

### Current Multimodal Models
**Vision-Language Models (VLMs):** These understand both images and text. Example: You show them a picture and ask a question—they answer based on both seeing and language understanding.

**Vision-Language-Action Models (VLAs):** These go further. They understand vision, language, AND how to control actions (crucial for robots). Examples include Google's RT-2 and other recent robotics-focused systems.

**Key insight from research:** Even with multimodal training, models still struggle with tasks that require understanding physical forces, cause-and-effect in the real world, and long-term planning. They're better than text-only, but still far from human-like understanding.

**Sources:** arXiv survey "A Survey on Vision-Language-Action Models for Embodied AI"; MIT, Stanford robotics labs

---

## 3. EMBODIED AI: ROBOTS AND PHYSICAL INTELLIGENCE

### The Big Picture
Embodied AI means AI systems that exist in the physical world and interact with it. Instead of just processing text in a computer, the system has sensors (cameras, touch sensors) and actuators (motors, grippers) to actually do things.

### Why Embodied AI Matters
The panel emphasized that **intelligence requires interaction with the physical world.**

One fascinating point: A sea squirt is a creature with a nervous system and brain. But once it becomes an adult and stops moving, it eats its own brain because it doesn't need it anymore. The lesson? Intelligence arises from the need to move and interact. Without physical interaction, a brain isn't necessary.

For AI, this suggests: true intelligence might require embodied experience, not just processing information.

### Current Applications
- Robots in warehouses picking and placing items
- Autonomous vehicles navigating complex environments
- Humanoid robots performing dexterous tasks (assembly, dangerous work)
- Robotic arms learning manipulation through demonstration

### The Data Problem
Here's a major challenge: We have millions of text examples online, but we have far fewer examples of robots doing tasks. This makes it harder to train embodied AI systems to the level we've trained language models.

Recent projects address this by:
- Training in simulation (virtual worlds) then transferring to real robots
- Combining internet video (humans doing tasks) with robot-specific data
- Using smaller amounts of carefully curated robot data with very large foundation models

**Research example:** RT-2 (Google DeepMind) and systems like ELLMER show robots can follow natural language instructions to complete complex tasks like making coffee or decorating plates.

**Sources:** Nature Machine Intelligence articles on embodied AI; survey papers from UC Berkeley, Stanford on robotics and vision-language-action models

---

## 4. WHAT DO TEXT-ONLY MODELS DO WELL?

### The Panel's Consensus
Language models have surprising strengths that shouldn't be dismissed:

**Math and abstract reasoning:** Frontier models recently solved previously unsolved math problems. They found novel techniques unknown even to mathematicians. This is remarkable and doesn't require seeing the physical world.

**Code generation:** Writing software and understanding algorithms works well in language. The problems are self-contained in text.

**Knowledge synthesis:** These models know vast amounts about many topics. They can combine knowledge in creative ways.

**Writing and communication:** Email drafting, technical writing, summarization—humans confirm these models often do better than people can.

### The Key Limitation
The panel noted an important distinction: These models **memorize and synthesize existing knowledge** very effectively. They don't necessarily create fundamentally new insights through their own exploration.

**Important caveat:** This is still useful and valuable. Many real-world problems don't require creating new knowledge—they require applying and combining existing knowledge intelligently.

---

## 5. MISSING PIECES: WHERE TEXT-ONLY FALLS SHORT

### Physical Reasoning
Models struggle with tasks requiring understanding of:
- How objects fall, balance, or move
- What happens when you apply force
- Spatial relationships and navigation
- Consequences of physical actions in the real world

**Example from panel:** Models take much longer than humans to solve escape-room style puzzles because they don't understand spatial affordances (how objects can be used, what surfaces support weight, etc.).

### Causality and Temporal Reasoning
Understanding cause-and-effect in real situations is harder for these models. They recognize patterns but struggle to understand "because."

### Hallucination Problem
Models sometimes produce confident-sounding but false information. This happens particularly with physical descriptions and facts they haven't seen enough examples of.

### Robustness
A 6-year-old child might struggle to count large numbers, but that doesn't mean humans are stupid. Similarly, models being weak at some tasks doesn't mean they're not intelligent—it just shows intelligence is uneven and specialized.

**Key insight:** Intelligence is "jagged"—systems excel in some areas and struggle in others. This is true for both humans and AI.

---

## 6. THE MULTIMODAL FUTURE: WHAT'S NEEDED

### Current Gaps
The panel identified several architectural and design changes needed:

1. **Better integration of modalities:** Currently, models often treat text, vision, and action somewhat separately. They should be more deeply integrated from the start.

2. **Temporal understanding:** Real-world tasks unfold over time. Models need better ways to understand sequences and how one action leads to another.

3. **Physical priors:** The models need to incorporate the constraints and rules of the physical world (objects don't pass through each other, gravity works downward, etc.).

4. **Interactive learning:** Rather than just learning from static data, systems should learn through trial and error with the environment.

### Inductive Biases
This is a technical concept that matters: Models should be designed with built-in assumptions that make physical and spatial reasoning easier. Humans have these (spatial orientation, understanding symmetry, etc.). AI systems need analogous design choices.

**Example:** Vision models have built-in spatial structure—pixels near each other matter more. This is an inductive bias that helps. Physical reasoning needs similar assistance.

---

## 7. RESEARCH PRIORITIES: WHERE TO INVEST

### Problems That SHOULD Get Less Focus
**Reinforcement Learning (as currently pursued):** The panel noted that much published work claims to use reinforcement learning but actually uses human demonstrations instead. Real reinforcement learning (learning through trial and error) is harder but might be oversold right now.

### Problems That NEED MORE Investment

#### 1. Misinformation and Disinformation
This is massive and underfunded. As AI becomes more capable:
- How do we defend against AI-generated misinformation?
- How do we detect false content?
- This requires both offensive (understanding attacks) and defensive understanding

#### 2. Alignment and Safety
Making sure AI systems do what we want them to do, and don't do things we don't want.

#### 3. Low-Resource Domains
Languages and problems where we don't have massive datasets:
- Languages with few speakers
- Specialized domains (rare diseases in medicine, uncommon industries)
- This matters because the world is diverse—solutions shouldn't only work where data is abundant

#### 4. Scientific Discovery
Current focus is on problems where solutions exist in training data. But science requires discovering new knowledge. This is harder and takes longer but is crucial for real progress.

#### 5. Robustness and Consistency
Making models more reliable, especially in critical domains like healthcare and autonomous vehicles.

### What Industry Is Better At
- **Scale:** Building massive systems that work at scale
- **Optimization:** Practical improvements in speed, efficiency, cost
- **Products:** Turning research into things people use

### What Academia Should Focus On
- **Efficiency:** Can we achieve similar results with less compute and data?
- **Generalization:** How do we make systems that work across many different domains and tasks?
- **Low-resource problems:** Domains where you don't have infinite data
- **Interdisciplinary application:** Applying AI to fields that need domain expertise (biology, physics, chemistry, etc.)
- **Theoretical understanding:** Why do these systems work? What are the fundamental principles?

---

## 8. THE INFERENCE AND EVALUATION PROBLEM

### The Gap Between Industry Success and Real Understanding
The panel raised an important issue: Companies claim remarkable results, but there's often a gap between what models can do and what problems they actually solve.

**Example:** A model might look impressive on a benchmark but fail at the practical problem. Or it might succeed because humans are coaching it step-by-step (like in the recent math problem example).

### The Evaluation Challenge
We need better ways to measure whether systems truly understand things or just pattern-match. This is hard because:
- Traditional metrics don't capture real-world usefulness
- It's easy to overfit to benchmarks
- Real-world problems are messier than test sets

### What Business Needs
Companies care about: Can this make my processes better? But often they're evaluating models incorrectly or the models succeed in limited ways.

---

## 9. ARCHITECTURE DESIGN: FROM TOKENS TO UNDERSTANDING

### The Current Approach
Language models work by predicting the next word (token) based on previous words. They're like very sophisticated autocomplete.

**New architectural thinking needed:** Models should incorporate:
- Causal reasoning (understanding because, not just correlation)
- Physical constraints naturally
- Temporal structure for sequential reasoning
- Feedback loops from the environment

### Simulation Environments
The panel discussed building simulated worlds where AI can learn:
- **Problem:** Simulations often don't match reality closely (sim-to-real transfer is hard)
- **Solution:** Rather than perfect physics simulations, focus on simulations that teach the right concepts and let models learn through interaction

**Important note:** Even simple simulations with meaningful feedback can teach useful concepts.

---

## 10. ADVICE FOR STUDENTS AND JUNIOR RESEARCHERS

### Don't Just Follow the Crowd
The research community can feel crowded. Trendy topics get attention. But there are many important problems that are underfunded and where a student's work could have real impact.

**Ideas for good research directions:**
1. **Low-resource languages and domains:** Major languages are covered. Many of the world's languages have almost no AI resources. This is important and less crowded.

2. **Efficient models:** Everyone wants bigger models. But making smaller, more efficient models that work with less data is valuable and needed.

3. **Applications to important domains:** Medicine, climate, biology, physics—these fields need AI expertise combined with domain knowledge. Not many people work here.

4. **Robustness and reliability:** Unglamorous but critical. How do we make AI systems we can trust?

### Think Bigger Than AI Papers
- Consider starting a company if you see a problem that needs solving
- Many industry problems are inefficient and AI could help
- The job market is changing—AI is automating some tasks but creating opportunities in others

### Pick Problems Wisely
Good research picks problems that are:
- Important (would genuinely help people or advance understanding)
- Under-explored (not crowded)
- Tractable (you can actually make progress)
- Aligned with your interests (you'll spend years on it)

---

## 11. THE BITTER LESSON AND FUTURE TRENDS

### The Bitter Lesson
In the 1970s, researchers tried to hand-code knowledge about chess or language. It didn't work. What worked was: scale up computation and data.

**The question now:** Will this hold forever? Will scaling continue to work, or do we need new approaches?

### Practical Reality
- We haven't hit fundamental walls in text-based learning yet
- But we're reaching limits in specific domains (like image generation at extreme detail)
- For embodied AI, we need new approaches—pure scaling won't be enough

### The Horizon
The panel sees progress coming from:
- Better multimodal integration
- Embodied learning (robots learning through interaction)
- Combining learning with physical constraints
- More efficient training

---

## 12. COLLABORATION BETWEEN INDUSTRY AND ACADEMIA

### Current State
Industry and academia are increasingly interdependent. Large companies fund academic research. Academics have better incentive structures for long-term thinking.

### What's Needed
- More industry investment in basic research in academia
- Academia bringing fundamental thinking to industry problems
- Sharing of simulation environments and datasets
- Joint work on underfunded problems (misinformation, robustness, alignment)

### The Risk
If academia becomes too focused on short-term problems that industry finds useful, we lose the exploratory, long-term thinking that generates fundamentally new ideas.

---

## SUMMARY: KEY TAKEAWAYS

1. **Multimodality matters:** Text alone is insufficient for full intelligence. Vision, action, and sensory data all contribute.

2. **Grounding is real but solvable:** The symbol grounding problem is not a showstopper. Embodied systems and multimodal training can partially solve it.

3. **Current systems are uneven:** Models are superhuman in some areas (math, code) and subhuman in others (physical reasoning, true understanding). This is normal.

4. **Architecture matters:** We need better-designed systems that incorporate physical constraints and temporal reasoning from the start.

5. **Data is not everything:** Efficiency and clever design can reduce our dependence on massive datasets.

6. **Embodied AI is the frontier:** Physical robots and systems that interact with the world are where intelligence will be tested and developed next.

7. **Important problems need funding:** Misinformation, robustness, alignment, and domain-specific applications are under-resourced and important.

8. **Students should think independently:** There are more important problems than trending topics. Follow your judgment.

---

## KEY RESEARCH REFERENCES

### Symbol Grounding
- Bender, E. M., & Koller, A. (2020). "Climbing towards NLU: On meaning, form, and understanding in the age of data." ACL 2020.
- Harnad, S. (1990). "The symbol grounding problem." Physica D, 42(3-4), 335-346.
- Research on whether multimodal models truly ground language: MIT, Royal Society publications, 2023-2024.

### Embodied AI and Robotics
- Survey: "A Survey on Vision-Language-Action Models for Embodied AI" (arXiv 2405.14093)
- Mon-Williams et al. (2025). "Embodied large language models enable robots to complete complex tasks." Nature Machine Intelligence.
- Mower et al. (2026). "A robot operating system framework for using large language models in embodied AI." Nature Machine Intelligence.

### Multimodal Learning
- Research on Vision-Language Models: Stanford, UC Berkeley, Google DeepMind, Meta
- Robotic learning from diverse data sources: Physical Intelligence, Stanford Robotics
- Simulation for robotics training: NVIDIA Isaac Sim, research from multiple labs

### General AI Progress
- Papers on Large Language Models and their capabilities: OpenAI, Google, Anthropic, Meta
- Research on AI alignment and safety: Anthropic, MIT, UC Berkeley
- Studies on AI robustness: Various academic labs
