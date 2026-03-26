[Read this in Russian / Читать на русском](README_RU.md)
# 🦾 Local LLM & SD Deployment Guide: The Path to Uncensored AI

A survival guide for setting up neural networks on budget hardware (GTX 1650 4GB).

This project is a detailed report on deploying local AI for text and graphics when you have limited VRAM but a strong desire for full freedom from corporate restrictions and censorship.

## 💻 System Specs (The Rig)
* **GPU:** NVIDIA GTX 1650 (4 GB VRAM) — The main bottleneck.
* **CPU:** AMD Ryzen 5 4600H (3.00 GHz)
* **RAM:** 16 GB
* **OS:** Windows 10 Pro (Optimized/Stripped build)

## 🧠 Part 1: Text Models (LLM) — In Search of a Personality
**Goal:** Create an assistant with Johnny Silverhand's (Cyberpunk 2077) personality that understands Russian.

**Software:** LM Studio. Chosen for its user-friendly interface and easy model search via Hugging Face.

**Personal Experience & Pitfalls:**
1. **Size Matters:**
   - 14B+ models: Too heavy; generation turns into a slideshow.
   - 4B models: Too "dumb"; they lose the thread of conversation quickly.
   - 7B - 8B (Llama 3, Mistral): The sweet spot for 4-8 GB of VRAM.
2. **Language Barrier:**
   - Local GPT variants: Worst results (ignored Russian).
   - Mistral: Tried, but its Russian comprehension was weak.
   - Llama 3 8B: Best "out-of-the-box" result for a Russian-speaking user.

**The CUDA Moment of Madness:**
When standard optimization methods failed, ChatGPT (in an attempt to help) suggested I rewrite the CUDA source code. At that moment, I realized the line between reality and absurdity had blurred. If you're being advised to patch NVIDIA driver source code, just know you've hit your hardware's absolute limit.

**Result:** [Johnny_Silverhand.jsonl](./JSasist.jsonl)

**Training Challenges:**
Fine-tuning (LoRA) for a specific character requires at least 12 GB of VRAM. Attempts to find free compute power via Oracle Cloud or university labs failed (Oracle only provides CPU/RAM, which is useless for neural networks).

## 🎨 Part 2: Image Generation (Stable Diffusion)
**Goal:** Generating NSFW and thematic content.

**UI Choice:**
* **Automatic1111:** Rejected due to its "90s-style" interface. Overly cluttered and unfriendly for beginners.
* **ComfyUI:** Top choice. The node-based system allowed for flexible workflow optimization under memory constraints.

**Optimization & Models:**
* **SD 1.5:** Fast, but images often felt "wooden."
* **SD3 (Stable Diffusion 3):** High quality, but one image took ~40 minutes on a GTX 1650.
* **Prompts:** I used pre-made prompt databases from Civitai and cloud services because mainstream AIs (like ChatGPT) refused to write NSFW descriptions due to built-in filters.

**The Model Fail:** While trying to bypass censorship for prompt writing, I tested the BadMistral checkpoint. Result: the model lost its mind and started speaking exclusively in Chinese. Likely due to a bad weights merge or corrupted quantization. After testing a few variants, I concluded that truly uncensored models are either a myth or extremely hard to find.

## 🛠 Quick Deployment Tips
* **Where to find models:** Hugging Face (text), Civitai (graphics).
* **For weak cards:** Always look for **GGUF** models (for LM Studio) and use **Q4_K_M** or **Q5_K_M** quantization. Use launch arguments like `--lowvram` or `--medvram`.
* **Environment:** Set up your Python environment correctly and update CUDA drivers, or ComfyUI might not detect your GPU.

## ⚖️ Conclusion: Why It Matters
Local deployment is the only working way to get AI without censorship. I believe the internet was originally created as a territory of freedom and should remain so. Even if using "raw" models seems "silly" or unsafe to corporations, the ability to communicate with an AI without a babysitter or filters is worth every hour spent on configuration. Freedom of speech and creativity is more important than the convenience of cloud services.

## 🖼 Gallery
![My Art](img/название_картинки.jpg)
