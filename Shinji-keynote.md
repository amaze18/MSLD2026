# Prof. Shinji's Keynote Session Notes
## MSLD 2026: Open Science, Reproducibility, and Scaling in Speech Recognition

**Speaker:** Prof. Shinji  
**Conference:** MSLD 2026  https://nlp.cs.illinois.edu/msld.html
**Key Topics:** Open Science, Model Reproducibility, Computational Scaling, Data Collection, Unification in Science

---

## 1. OPEN SCIENCE AND THE REPRODUCIBILITY PROBLEM

### What is the Problem?
In 2023, when OpenAI released Whisper, the speech recognition community was excited. This model could transcribe speech in 99 languages with impressive accuracy. However, excitement turned to concern when researchers realized they couldn't reproduce it.

**Why was reproducibility impossible?**
- The training data wasn't publicly available
- No one knew exactly how to train it
- The model details were proprietary

This creates several dangers:
- Risk of misuse (could be used to create deepfakes or other harmful applications)
- Fairness issues (model biases aren't transparent)
- No way to fix bugs or improve the model
- Science becomes locked behind closed doors

### The Case for Open Science
Prof. Shinji's position is clear: science works best when it's open. This doesn't mean companies are bad or shouldn't exist. Rather, there needs to be healthy collaboration:

**Academic researchers** work to push open science forward while **industrial researchers** develop practical products. These roles complement each other.

Think of it like this: Researchers want to be the best in their field. Even big companies have healthy competition. The key is creating a collaborative ecosystem where transparency and reproducibility coexist with innovation.

**Research Sources:** Recent papers on open science in AI (2025-2026), debates around proprietary vs. open models in speech recognition

---

## 2. THE WHISPER REPRODUCTION PROJECT

### What They Did
Prof. Shinji and colleagues worked to reproduce OpenAI's Whisper model using only public information and open-source approaches. This project took about two years (2024-2025).

### The Scale Problem
To appreciate how hard this was, understand the data scale:
- Whisper was trained on **680,000 hours of speech data**
- This is an enormous amount

**For context:**
- In 2022, researchers could publish papers with just 1,000 hours of speech data
- With some improvement, 10,000 hours was significant
- Some companies use 5 million hours
- Another reference: **680,000 hours = one person speaking continuously for over 77 years**

### Computational Resources
Training Whisper from scratch required 120,000 GPU-hours of computing power.

But Prof. Shinji didn't have 120,000 hours of continuous GPU access. Here's what they did instead:

**Clever resource gathering:**
- Applied for grants from the NSF (National Science Foundation)
- Used university computing centers (PSC and NCSA)
- Leveraged departmental computing clusters
- Applied for cloud computing credits

**Total effort:** Spent time writing detailed 16-page grant proposals instead of spending money directly. This shows that large projects don't require unlimited budgets—they require smart planning and effort.

**Key message:** If you want to do similar large-scale research, you can too. Prof. Shinji is willing to help others learn how to write proposals and secure computing time.

**Research Sources:** Papers on efficient GPU utilization, guides on computing cluster access and allocation

---

## 3. DATA COLLECTION AND PREPARATION

### The Critical Challenge
If training efficiency and computing resources are hard, data is even harder.

**The data problem:**
- Previous large speech datasets (like those used for Whisper) required enormous human effort
- Some training data is "synthetic" (created, not recorded from real people)
- Some data comes from difficult real-world scenarios (noisy environments, non-native speakers, long recordings)
- Using all data isn't always possible due to licensing concerns

### How They Collected Data
For the open reproduction project:
- Started with publicly available speech data
- Very careful about licensing
- Used carefully curated collections from the research community
- Aggregated data from multiple sources

**Result: 680,000 hours of open-source training data**

This includes:
- Public datasets donated by researchers
- Careful curation from sources like Common Voice and other open databases
- Community contribution

### Data Quality Improvements
They didn't just use raw data. They applied several filtering and cleaning techniques:
- Segmentation (breaking long recordings into manageable pieces)
- Language identification (checking the language is correct)
- Hallucination filtering (removing transcriptions with common errors)
- Punctuation and capitalization restoration

**Important insight:** Good data selection and cleaning can almost double the effective size of your dataset without collecting more raw data.

**Research Sources:** arXiv papers on data curation pipelines, Granary dataset paper (2505.13404), papers on data filtering for speech models

---

## 4. SCALING AND COMPUTATIONAL EFFICIENCY

### Training Timeline and Improvements
**2023 (Initial attempt):** Took a long time and required enormous compute

**2025 (After two years of optimization):**
- Training time reduced by **10 times**
- From needing 30,000 GPU-hours down to 3,000 GPU-hours

**Projection:** If this trend continues for 10 years, training would become exponentially faster. This shows that raw scaling (throwing more GPUs at the problem) isn't the only path to improvement.

### What Changed?
Several factors contributed to these speedups:

**Hardware improvements:**
- Newer GPUs became available
- Better GPU-to-GPU communication (faster networks)

**Software improvements:**
- Better deep learning frameworks
- Optimized implementations for specific operations
- Compiler improvements

**Architectural improvements:**
- Changes to the Transformer architecture for faster processing
- Reduced activation memory requirements

### The Scaling Law Principle
There's an important principle in machine learning called **scaling laws**. These describe how performance improves as you add more compute, data, or model parameters.

**The relationship is predictable:** Double the training data doesn't double training time. The relationship follows a power law (roughly: performance improves by a constant amount for each doubling of compute).

**Practical implications:**
- You can estimate in advance how long training will take
- You can make smart trade-offs (e.g., slightly smaller model for much faster training)
- These laws help plan resource allocation

**Research Sources:** Scaling laws papers from NVIDIA, arXiv papers on efficient training (scaling-book, NVIDIA blog on scaling laws)

---

## 5. OPEN VS. CLOSED: WHAT DOES "OPEN SOURCE" REALLY MEAN?

### The Definition Problem
Prof. Shinji makes an important distinction: just because code is available doesn't mean it's truly open.

**True open source requires:**
- Code is available
- Training data is available (or at least documented)
- Training procedures are reproducible
- Anyone can verify the claims

**What's not enough:**
- Just releasing a model without explaining how it was trained
- Releasing code but not the data
- Not documenting the process

### The OWSM Project
Prof. Shinji refers to their work as OWSM (Open Whisper Speech Model), not just "an open version of Whisper."

The name matters because:
- It's inspired by Whisper's approach, but different
- It emphasizes that this is a complete, reproducible system
- Everything needed to understand and verify the work is available

---

## 6. SCALING IMPROVEMENTS IN PRACTICE

### Case Study: Two Years of Progress
The team tracked their progress from 2023 to 2025:

**2023 Results:**
- Model performance was decent but not exceptional
- Encouraging enough to inspire further work
- Showed that reproduction was possible

**2024-2025 Results:**
- Significant improvements in accuracy
- Comparable to commercial models in many languages
- Better than Whisper in some specific cases

**Key improvements came from:**
- Using newer model architectures (Transformers with modifications)
- Normal Bayesian language models for better speech understanding
- Systematic algorithmic improvements

### Performance Measurement
Different metrics measure different things:
- **WER (Word Error Rate):** How many words are transcribed incorrectly. Lower is better.
- **Accuracy across speakers:** How well it works for different voice types
- **Language coverage:** How many languages it supports

### Test Contamination Issue
An important caveat: Many systems today are tested on datasets that were used in commercial models' training.

**This is like studying for a test, then taking that exact test.** You look much smarter than you actually are.

Prof. Shinji's team was careful to avoid this:
- Check if test data might overlap with training data
- Use separate, clean test sets
- Report both "clean" and "realistic" performance

This transparency is part of what makes open science valuable.

**Research Sources:** Papers on test contamination in ASR, ICLR 2025 paper on speech recognition robustness

---

## 7. TRANSFORMERS AND NEURAL ARCHITECTURES

### What Are Transformers?
A Transformer is the core architecture used in most modern speech and language models. It's based on attention mechanisms—a way for the model to focus on important parts of the input.

**In speech recognition:**
- Audio goes in (sound waves)
- Transformer processes it
- Text comes out (transcription)

### Speed Improvements Over Time
They explored several improvements:
- **Attention optimization:** Making the core computation faster
- **Model compression:** Using smaller models without losing accuracy
- **Quantization:** Using lower-precision numbers (like 8-bit instead of 32-bit)

These techniques can significantly reduce training and inference time.

### Architectural Choices Matter
Some design decisions have huge impacts:
- Reducing decoder layers (from 32 to 4) can make it 6 times faster
- Memory-efficient attention mechanisms reduce peak memory usage
- Different model sizes for different use cases

**Research Sources:** Papers on efficient Transformers, NVIDIA and JAX scaling documentation

---

## 8. COLLABORATION AND COMMUNITY

### Why Collaboration Matters
Prof. Shinji emphasizes that this project wasn't a solo effort:
- Colleagues from multiple institutions
- Community members donating data
- Open-source software contributors
- Researchers across the world

### The Importance of Community Data
Much of the 680,000 hours of training data came from community contributions:
- Researchers sharing datasets they created
- Public databases like Common Voice
- Crowdsourced speech collections

This is a powerful model: individual researchers and groups contribute data, and the entire community benefits.

### Supporting Others
Prof. Shinji's position: if you want to do large-scale open research, ask for help.
- Mentorship is available for writing proposals
- The path to securing computing resources is learnable
- Communities can pool resources

This democratizes large-scale AI research beyond just big companies.

---

## 9. UNIFICATION IN SCIENCE: DEEPER PRINCIPLES

### Why Unification Matters
In the second part of the talk, Prof. Shinji shifts to a broader scientific question: What do different fields have in common?

### Examples of Unification
**Physics:** The most famous example is Maxwell's equations, which unified electricity and magnetism.

**Before unification:** Scientists saw them as two separate phenomena.

**After unification:** They realized they're the same thing viewed from different angles. You can switch one for the other mathematically and get equivalent equations. This is beautiful and suggests deeper truth.

**Goal:** Achieve similar unification in speech processing.

### Symmetry and Beauty
The insight is that beautiful theories often have deep symmetries. When two seemingly different things turn out to be related, that's often a sign you're on to something fundamental.

**Application to speech:**
- Speech recognition (speech to text)
- Speech generation (text to speech)

These seem opposite, but they might be united by deeper principles.

### Natural Basis for Unification
There's a scientific basis for thinking these are related:
- Neuroscience shows the human brain uses similar pathways for understanding and producing speech
- Both involve encoding/decoding information
- Both require understanding acoustic and linguistic structure

### Joint Modeling Approach
Instead of building completely separate systems:
- Build a unified model that handles both understanding and generation
- This is not just a convenience—it's scientifically motivated
- Theories from linguistics and neuroscience support this approach

**Research Sources:** Neuroscience literature on speech production and comprehension, unified models in speech processing

---

## 10. PRACTICAL LESSONS AND RECOMMENDATIONS

### For Researchers Starting Large Projects

**Don't try to build the fanciest thing initially:**
- Start simple
- Prove the concept works
- Optimize later

**Writing proposals takes time but pays off:**
- 16 pages of careful proposal writing can unlock months of computing resources
- This is a learnable skill
- Help is available

**Focus on reproducibility early:**
- Document everything from day one
- Plan for others to understand your work
- Open science benefits everyone

### Key Takeaway About Resources
The project needed:
- Significant computational resources (120,000 GPU-hours)
- Large datasets (680,000 hours of speech)
- Talented people (researchers from multiple institutions)

But none of these individually are impossible. Smart combination and good planning make it achievable.

### Timeline Expectations
The project took **two years** to go from initial idea to comparable performance. This is important for setting realistic expectations.

This isn't fast, but it's faster than training Whisper originally (which took OpenAI much longer with more resources).

---

## 11. UNIFICATION PRINCIPLES IN RESEARCH DESIGN

### Symmetry and Bidirectional Processing
Prof. Shinji emphasizes looking for symmetries in your field:
- Where are two problems actually the same problem viewed differently?
- Can you build one system that solves both?
- Does this reveal deeper truth about the problem?

### Three Key Approaches for Unification
1. **Mathematical approach:** Show that two systems can be transformed into each other
2. **Neuroscience approach:** Show that the brain uses similar structures for both tasks
3. **Behavioral approach:** Show that learning one helps with the other

### Connection Between Specifics and Universality
While the talk focuses on speech, the principles apply broadly:
- Look for unification opportunities in your field
- Deep principles often underlie surface diversity
- Unified theories tend to be more elegant and more predictive

---

## 12. BIGGER PICTURE: SCIENCE AND SOCIETY

### Open Science as a Value
Beyond just technical achievement, Prof. Shinji advocates for open science as a principle:
- Transparency enables verification
- Reproducibility enables progress
- Openness enables fairness
- Community-driven development distributes benefits

### Responsibility of Researchers
If you develop new techniques or models:
- Consider how to make them reproducible
- Think about who might be harmed by opacity
- Plan for community contribution

### The Middle Path
The position isn't "commercial research is bad." Rather:
- Both have roles
- They should complement each other
- Healthy competition is fine, but transparency is essential

---

## SUMMARY: KEY TAKEAWAYS

1. **Reproducibility Matters:** The inability to reproduce Whisper revealed risks of closed science. Open alternatives are essential.

2. **Scale Is Achievable:** 680,000 hours of data and 120,000 GPU-hours sounds impossible, but smart planning makes it accessible.

3. **Efficiency Improves Over Time:** Two years of optimization reduced training time by 10x. This shows raw scaling (more GPUs) isn't the only path.

4. **Data Curation Matters More Than Raw Data:** Careful filtering and cleaning can be as valuable as collecting more data.

5. **Community Collaboration Works:** Large projects can succeed through distributed effort and shared resources.

6. **Beauty in Science Indicates Truth:** Looking for unification principles (like Maxwell's equations did for electromagnetism) can reveal deeper insights.

7. **Bidirectional Processing:** Speech recognition and generation might be unified through one system, following principles from neuroscience.

8. **Practicalities Matter:** Successful research requires attention to:
   - Grant writing and resource acquisition
   - Project timeline planning
   - Team collaboration
   - Documentation for reproducibility

---

## RELEVANT RESEARCH REFERENCES

### Open Science and Reproducibility
- Recent papers on open-source speech models (OLMoASR, FireRedASR, Meta's Omnilingual ASR)
- Discussions of test contamination in benchmarks (ICLR 2025)
- Papers on data filtering pipelines for speech

### Computational Efficiency
- JAX Scaling Book (jax-ml.github.io/scaling-book/)
- NVIDIA Blog on Scaling Laws (2025)
- Papers on efficient GPU training strategies
- MegaScale paper on training at 10,000+ GPUs
- Slamming paper on speech language model training in 48 hours

### Data Collection
- Granary dataset paper (arXiv 2505.13404): 25 European languages
- Papers on multilingual speech dataset curation
- Common Voice and VoxPopuli dataset papers
- FLEURS dataset for 102 low-resource languages

### Scaling Laws
- Original Chinchilla scaling laws papers
- Recent work on scaling vs. inference efficiency trade-offs
- Papers on compute-optimal training

### Speech Models
- Whisper model from OpenAI
- Recent improvements in multilingual ASR (2025-2026)
- Papers on attention mechanisms and Transformers
- Research on joint speech generation and understanding

### Unification in Science
- Historical examples (Maxwell on electromagnetism)
- Neuroscience papers on shared mechanisms in speech comprehension and production
- Papers on unified modeling approaches

---

**Note:** This keynote emphasizes both technical achievement (reproducible open-source speech models) and philosophical commitment 
(to open science, community collaboration, and looking for deep principles in research).

The practical lesson is that large-scale AI research, while challenging, is increasingly accessible to academic researchers through careful planning, community collaboration, and smart use of available resources.
