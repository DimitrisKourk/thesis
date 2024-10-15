# Employing AI Tools in Game Development & Unreal Engine as a Deep Reinforcement Learning Simulation Environment

LaTeX source of my **BSc thesis** for the Department of Informatics and Telecommunications, **University of Thessaly** (Lamia, 2024).
Advisor: Panagiotis Oikonomou, Adjunct Lecturer.

## Abstract

As AI technology advances, more and more industries integrate it into their workflow. This thesis focuses on the **game development industry**. It analyzes every part of developing a modern video game and how cutting-edge AI can optimize each part of the workflow, from creating behavior to generating digital content.

It reviews the current literature, features a range of widely available AI tools in detail, and then **develops a demo game** with those tools and **Unreal Engine**. The game world is then used as a simulation environment to **design, implement and train a Deep Reinforcement Learning agent** inside it. The thesis ends with how such an environment could be adapted to simulate real-world scenarios, and the benefits of deploying agents trained in simulation.

## Contents

| Chapter | Topic |
|---|---|
| 1 | Introduction: origins of gaming, AI, motivation and objectives |
| 2 | Literature review: **behavioral AI** (finite state machines, behavior trees, neural networks and deep reinforcement learning) and **generative AI** (VAEs, GANs, latent diffusion models, and their use for images, audio and more) |
| 3 | Modern video game development and the components of a video game |
| 4 | Challenges of game development by scale, and the benefits of AI |
| 5 | Game development software and the AI tools that can replace or augment parts of it |
| 6 | **Deep Reinforcement Learning inside Unreal Engine** (see below) |
| 7 | Conclusions |

### Chapter 6: training an RL agent in Unreal Engine

Unreal Engine has no built-in deep RL, so the agent is trained with a **middleman approach**. The **MindMaker** plugin extracts observations from the game world, sends them to an external Python process running **Proximal Policy Optimization (PPO)** (OpenAI Gym-style interface, `MlpPolicy`), and feeds the chosen actions back to the agent in the engine.

Four experiments, all with the same PPO hyperparameters:

1. **Movement and camera control:** navigating the level while controlling the camera
2. **Improved movement and camera control:** adds the agent's position and camera rotation to the observations, after diagnosing why the first agent couldn't tell similar states apart
3. **Stationary aiming:** turning to aim at targets
4. **Stationary aiming and shooting:** aiming and firing at targets

Training is analyzed with the **TensorBoard** scalar curves (approximate KL, clip fraction, entropy loss, explained variance, policy-gradient loss, value loss, action std). The chapter closes with how to adapt the environment to simulate real-world applications.

## Building the PDF

Requirements: a TeX Live distribution, **biber**, and **Python with Pygments** (used by `minted` for code listings).

```bash
latexmk -pdf -shell-escape main.tex
```

`-shell-escape` is required by `minted`. latexmk runs pdfLaTeX and biber as many times as needed.

| File | Description |
|---|---|
| `main.tex` | The full thesis |
| `myref.bib` | Bibliography (biblatex / biber) |
| `mieUTHtitle-en.sty` | University of Thessaly title pages (Greek and English) |
| `MyThesisImages/media/` | Figures, including the training-curve plots from the experiments |

The thesis is written in English, with a Greek abstract and the university's mandatory declaration in Greek.
