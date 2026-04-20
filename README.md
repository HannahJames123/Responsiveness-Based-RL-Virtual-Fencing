# Reinforcement Learning for Acoustic Cattle Guidance

This repository contains code for modeling and optimizing cattle behavioral responses to acoustic cues using reinforcement learning (RL), behavioral simulation, and personality-aware response analysis.

The project combines:

- a **behavioral response model** for cattle turning probability
- **personality classification** based on response latency and cue sensitivity
- **reinforcement learning** to optimize acoustic cue selection
- **publication-style plotting scripts** for analyzing results

## Overview

The main goal of this project is to simulate how cattle respond to different sound-based cues and to learn which cue combinations are most effective for guiding movement under different behavioral conditions.

The code explores:

- how **frequency**, **amplitude**, and **social context** influence response
- how **training history** changes turning probability over time
- how cattle can be grouped into **reactive**, **moderate**, and **low-reactive** personality types
- how an RL agent can learn better cue strategies across repeated training episodes

## Features

- Behavioral response model with:
  - frequency sensitivity
  - amplitude response
  - learning curve
  - habituation effects
  - solo vs. group response parameterization

- Personality detection using:
  - response rate
  - latency
  - latency variability
  - amplitude sensitivity

- RL training pipeline with:
  - discrete acoustic action space
  - multiple training runs
  - reward optimization
  - saved results for downstream analysis

- Plot generation for:
  - validation figures
  - publication-ready results
  - black-and-white compatible versions
  - summary metric visualizations

## Repository Structure

```bash
.
├── Rl_paper_final_code.ipynb      # Main notebook containing all modeling, validation, RL, and plotting code
├── 1_RL_TRAINING.py               # RL training script (exported from notebook)
├── 2_CREATE_PLOTS.py              # Plot generation script
├── best_result.pkl                # Best-performing RL run
├── all_runs_results.pkl           # All RL run outputs
├── all_runs_summary.json          # Summary of all runs
├── all_runs_summary.csv           # Tabular summary of all runs
└── README.md
