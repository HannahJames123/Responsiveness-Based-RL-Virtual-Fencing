# Responsiveness-Based Reinforcement Learning for Virtual Fencing Cue Selection

This repository contains the main notebook used for a simulation study of responsiveness-based virtual fencing in cattle. The project uses a biologically informed cattle response model and reinforcement learning to test whether an adaptive controller can learn different cueing strategies for simulated cattle agents with different response profiles.

The study is intended as a proof-of-concept simulation, not as a field-ready virtual fencing system or a recommendation of specific cue settings for real cattle.

## Overview

Virtual fencing systems use GNSS-enabled collars or wearable devices to define a virtual boundary. When an animal approaches the boundary, the system issues an audio warning. If the animal continues moving toward or into the exclusion zone, the system may escalate to a brief electrical stimulus.

In practical terms, this simulation represents a virtual herd repeatedly encountering a virtual fence boundary. At each encounter, a reinforcement-learning controller selects a cueing action defined by:

- frequency
- amplitude
- sound type
- temporal pattern
- whether electrical stimulation is enabled

Each simulated cattle agent has responsiveness-linked response characteristics. High-responsive, moderate-responsive, and low-responsive agents differ in cue sensitivity, learning dynamics, and response latency. The controller receives higher rewards when agents turn in response to acoustic cues and lower rewards when agents fail to respond or require electrical stimulation. Over repeated interactions, Q-learning updates responsiveness-specific decision tables so that the controller learns which cue combinations are most effective for each simulated response profile.

## Research Goal

The main goal of this project is to evaluate whether reinforcement learning can identify candidate virtual-fencing cueing policies that adapt to heterogeneous simulated cattle response profiles while minimizing reliance on electrical stimulation.

In simple terms, the study asks:

1. Can a reinforcement-learning controller learn different cueing actions for simulated cattle agents with different response profiles?
2. Can it do so while keeping simulated electrical-stimulation use low?
3. Can the resulting cueing patterns help identify candidate strategies for future controlled animal studies?

## Main Notebook

### `Rl_paper_final_code.ipynb`

This is the only code file included in the repository. It contains the complete workflow used in the simulation study, including model setup, reinforcement-learning training, evaluation, analysis, and figure generation.

The notebook includes code for:

1. Defining the biologically informed cattle response model.
2. Initializing simulated cattle agents with responsiveness-linked traits.
3. Assigning high-responsive, moderate-responsive, and low-responsive response profiles.
4. Modeling cattle-agent responses to acoustic virtual-fencing cues.
5. Defining the reinforcement-learning action space, including frequency, amplitude, sound type, temporal pattern, and electrical-stimulation status.
6. Training a Q-learning controller across repeated simulated boundary interactions.
7. Running multiple independent training runs with different random seeds.
8. Selecting the highest-scoring learned policy based on a composite evaluation score.
9. Evaluating learned cue-selection patterns across responsiveness classes.
10. Calculating welfare-relevant outcomes, including simulated shock delivery rate.
11. Generating publication-style figures and summary metrics.

All outputs, including intermediate results, summary metrics, and plots, are generated from within the notebook. No separate training scripts, plotting scripts, pickle files, CSV files, or JSON summary files are included in this repository.

## Model Components

The simulation includes a behavioral response model with:

- frequency sensitivity
- amplitude response
- associative learning
- habituation effects
- social facilitation
- response latency
- responsiveness-linked cue sensitivity

The reinforcement-learning framework includes:

- discrete acoustic cue action space
- responsiveness-specific Q-tables
- repeated training episodes
- reward optimization balancing containment, cue personalization, and shock minimization
- evaluation of learned cue-selection patterns
- welfare-relevant metrics such as shock delivery rate

## Important Interpretation Notes

The outputs should be interpreted as simulation results, not as direct evidence of cattle sound preferences or field-ready cue settings.

Some parts of the analysis evaluate whether the model behaved consistently with its assigned response structure. Other parts examine the cueing actions selected by the controller under that structure.

The model does not establish real-world effectiveness, transferability to live cattle, long-term welfare outcomes, or practical deployment feasibility. Controlled animal studies, grazing trials, reward-sensitivity analyses, and testing of the full warning-cue/electrical-stimulus sequence would be needed before practical recommendations could be made.

## Repository Structure

Only the main notebook and this README are included:

```text
.
├── Rl_paper_final_code.ipynb      # Main notebook containing simulation, RL training, evaluation, and plotting code
└── README.md                      # Repository documentation
```

## Requirements

The notebook uses standard Python scientific computing and plotting libraries, including:

- `numpy`
- `pandas`
- `matplotlib`
- `scipy`
- `pickle`
- `json`

Additional packages may be required depending on the local environment used to run the notebook.

## Running the Notebook

Open `Rl_paper_final_code.ipynb` in Jupyter, JupyterLab, Google Colab, or another compatible Python notebook environment.

Run the cells sequentially to reproduce the simulation workflow, training process, evaluation outputs, and figures.

Because reinforcement-learning results depend on random initialization and exploration, the notebook uses defined random seeds where possible to support reproducibility.

## Citation

If using or adapting this code, please cite the associated manuscript:

**A Simulation Study of Responsiveness-Based Virtual Fencing: A Reinforcement Learning Approach to Precision Livestock Management**

## Disclaimer

This repository provides code for a simulated proof-of-concept study. It does not provide a deployable animal-control system, animal-use protocol, or validated virtual-fencing cue recommendation. No live animals are used in the simulation.
