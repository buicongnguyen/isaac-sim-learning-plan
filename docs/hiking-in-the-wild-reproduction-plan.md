# Hiking in the Wild Reproduction Plan

Goal: learn Isaac Sim and Isaac Lab deeply by reproducing the core ideas from **Hiking in the Wild: A Scalable Perceptive Parkour Framework for Humanoids**, first in simulation and only later thinking about real-robot deployment.

Paper: https://arxiv.org/abs/2601.07718  
Project page: https://project-instinct.github.io/hiking-in-the-wild/  
Code: https://github.com/project-instinct/InstinctLab  
Related framework: https://github.com/project-instinct/instinct_rl  
Isaac Lab docs: https://isaac-sim.github.io/IsaacLab/

## 0. Problem Direction

This paper sits in the research direction of **perceptive humanoid locomotion over unstructured terrain**.

The central problem is:

> How can a humanoid robot move quickly and safely across unknown rough terrain using onboard perception, without relying on fragile mapping, localization, or hand-designed foothold planning?

The paper focuses on:

- humanoid locomotion and hiking
- onboard depth perception
- rough terrain, stairs, platforms, ramps, gaps, and grass-like surfaces
- end-to-end reinforcement learning
- Isaac Sim and Isaac Lab training
- zero-shot sim-to-real deployment
- safe foothold placement near terrain edges
- reward hacking prevention through feasible target sampling

For my learning, the important senior-level question is:

> Can I reproduce the paper's key mechanisms in Isaac Lab, understand why each part matters, and show ablations that prove the mechanisms are useful?

## 1. What Makes The Paper Special

The paper is publishable because it does not only show a strong demo. It identifies two concrete failure modes in perceptive humanoid RL and gives scalable solutions.

### 1.1 Failure Mode: Unsafe Footholds

Humanoids are sensitive to partial foot contact. A foot landing partly on a stair edge, gap edge, or platform lip can slip and create a catastrophic fall.

The paper's mechanism:

- detect sharp terrain edges from arbitrary meshes
- attach volume points to the robot feet
- penalize foot volume points that penetrate edge regions
- make the policy learn safer, more centered footholds without explicit foothold planning

Learning target:

- implement a simplified terrain edge detector
- visualize detected edges
- implement an edge-contact penalty
- compare policies with and without this penalty

### 1.2 Failure Mode: Reward Hacking

Random velocity commands can make the robot learn bad shortcuts, such as turning in place or avoiding hard terrain instead of actually crossing it.

The paper's mechanism:

- sample reachable flat patches on the terrain
- convert target patch position into velocity and heading commands
- train the robot on physically meaningful navigation targets

Learning target:

- implement flat patch sampling on generated terrain
- convert target position into velocity commands
- compare uniform random velocity commands against flat-patch position-based commands

### 1.3 System Direction

The paper trains one policy that maps:

```text
depth history + proprioception + command -> joint targets
```

The policy avoids explicit mapping and localization. That makes the research direction attractive because it reduces modular pipeline brittleness, but it also puts more burden on simulation quality, observation design, reward design, and domain randomization.

## 2. Reproduction Scope

I should not try to reproduce the full real-robot system first. The correct scope is staged.

### Level 1: Reading Reproduction

Deliverable:

- a 2-3 page technical summary in my own words
- diagram of the system pipeline
- list of all observations, actions, rewards, terminations, and training tricks

Done when:

- I can explain why depth, edge penalty, flat patch sampling, MoE, AMP, and depth history each exist
- I can explain the ablation table without reading the paper

### Level 2: Codebase Reproduction

Deliverable:

- clone and run the released Project Instinct / InstinctLab code
- document exact versions, install steps, and first successful command
- save one training or playback screenshot

Done when:

- I can run at least one provided Isaac Lab task
- I know where tasks, configs, terrains, rewards, observations, and policies live in the codebase

### Level 3: Minimal Isaac Lab Reproduction

Deliverable:

- my own small Isaac Lab task with a humanoid or simpler legged robot
- terrain with boxes, ramps, stairs, and gaps
- proprioceptive observations
- basic velocity command tracking

Done when:

- a baseline policy trains or at least runs through the environment loop
- I can log reward terms and reset reasons

### Level 4: Perceptive Reproduction

Deliverable:

- add depth observation or ray-cast style height/depth input
- add depth history
- add sensor noise or observation randomization

Done when:

- I can compare proprioception-only vs perception-conditioned training
- I can visualize the observation seen by the policy

### Level 5: Core Mechanism Reproduction

Deliverable:

- implement simplified terrain edge detection
- implement foot volume points or simplified foot contact safety points
- implement edge contact penalty
- implement flat patch sampling
- implement position-based command generation

Done when:

- I can run ablations:
  - baseline
  - no depth history
  - no edge penalty
  - no flat patch command
  - full simplified method

### Level 6: Paper-Style Report

Deliverable:

- short report with method, implementation, plots, screenshots, and videos
- success rate by terrain type
- mean reaching time or episode return
- failure case analysis
- comparison against ablations

Done when:

- the report reads like a mini paper
- the repo is reproducible from clean instructions

## 3. Learning Roadmap

## Phase A: Isaac Sim Foundations

Purpose: become comfortable with the simulator itself.

Tasks:

- [ ] Launch Isaac Sim 5.1.0 successfully.
- [ ] Open sample scenes.
- [ ] Create a simple USD stage.
- [ ] Add rigid objects and inspect physics properties.
- [ ] Add a robot articulation.
- [ ] Add camera and depth camera sensors.
- [ ] Run a simple scripted robot control example.
- [ ] Save screenshots and notes.

Skills to understand:

- USD stage and prim hierarchy
- articulations and joints
- PhysX simulation settings
- sensors and render products
- Python scripting inside Isaac Sim
- debugging simulation instability

## Phase B: Isaac Lab Foundations

Purpose: move from manual simulation to scalable robot learning environments.

Tasks:

- [ ] Install Isaac Lab compatible with Isaac Sim 5.1.0.
- [ ] Run a built-in Isaac Lab environment.
- [ ] Run training with a small number of environments.
- [ ] Run headless simulation.
- [ ] Understand manager-based environments.
- [ ] Understand direct workflow environments.
- [ ] Locate observations, actions, rewards, events, terminations, and curriculum configs.

Skills to understand:

- environment registration
- scene configuration
- observation manager
- reward manager
- termination manager
- command manager
- event/domain randomization manager
- vectorized simulation

## Phase C: Project Instinct Code Reading

Purpose: learn from the authors' implementation style.

Tasks:

- [ ] Clone InstinctLab.
- [ ] Clone instinct_rl.
- [ ] Read the root README files.
- [ ] Find the parkour task code.
- [ ] Find terrain generation code.
- [ ] Find reward definitions.
- [ ] Find observation definitions.
- [ ] Find policy/export/deployment flow.
- [ ] Make a code map in notes.

Questions to answer:

- Where is the task registered?
- What robot asset is used?
- How are terrains represented?
- How are commands generated?
- How are depth observations generated?
- Where are reward terms defined?
- How are policies exported?

## Phase D: Baseline Locomotion Task

Purpose: build my own controllable baseline before adding the paper's ideas.

Tasks:

- [ ] Create a new Isaac Lab project or extension.
- [ ] Register a minimal locomotion task.
- [ ] Use a simple terrain first.
- [ ] Add velocity command tracking.
- [ ] Add basic rewards:
  - velocity tracking
  - orientation stability
  - energy penalty
  - action smoothness
  - foot slip penalty if available
- [ ] Add basic terminations:
  - fall
  - low base height
  - illegal contact
  - out of bounds
- [ ] Train a baseline.

Deliverables:

- baseline training command
- baseline video
- baseline reward plot
- reset/failure statistics

## Phase E: Terrain Curriculum

Purpose: reproduce the terrain challenge space.

Tasks:

- [ ] Create stairs.
- [ ] Create platforms.
- [ ] Create ramps.
- [ ] Create gaps.
- [ ] Create rough terrain.
- [ ] Randomize terrain dimensions.
- [ ] Track success rate per terrain type.

Deliverables:

- terrain screenshot gallery
- terrain config table
- baseline performance by terrain

## Phase F: Depth Perception

Purpose: move from blind locomotion to perceptive locomotion.

Tasks:

- [ ] Add forward-facing depth observation.
- [ ] Confirm camera pose relative to robot head/body.
- [ ] Resize/crop/normalize depth input.
- [ ] Add depth history.
- [ ] Add artificial sensor delay.
- [ ] Add noise, blur, dropout, or missing depth regions.
- [ ] Visualize processed depth tensors.

Deliverables:

- depth observation visualization
- comparison between raw and processed depth
- proprioception-only vs depth-conditioned baseline

## Phase G: Flat Patch Sampling

Purpose: reproduce the paper's solution to reward hacking.

Tasks:

- [ ] Sample candidate 2D terrain positions.
- [ ] Ray-cast around each candidate.
- [ ] Reject patches with too much height variation.
- [ ] Store valid flat patch targets.
- [ ] Select a target periodically.
- [ ] Convert target in robot frame to forward velocity and yaw command.
- [ ] Add speed limits by terrain type.
- [ ] Keep some pure turning commands for in-place rotation skill.

Minimal algorithm:

```text
for each terrain:
  sample many candidate xy positions
  query heights around candidate radius
  if max_height - min_height < threshold:
    accept as flat patch

for each robot:
  choose target patch
  transform target to robot base frame
  command forward velocity proportional to target x
  command yaw rate proportional to target heading
```

Deliverables:

- visualization of accepted flat patches
- training run with uniform commands
- training run with flat-patch commands
- comparison of reward hacking/failure behavior

## Phase H: Terrain Edge Detection

Purpose: reproduce the paper's safety mechanism.

Tasks:

- [ ] Load terrain mesh or generated terrain geometry.
- [ ] Find adjacent mesh faces.
- [ ] Compute dihedral angle between adjacent faces.
- [ ] Mark sharp edges above threshold.
- [ ] Merge or simplify edge segments.
- [ ] Build an efficient query structure.
- [ ] Visualize detected edges.

Minimal version:

```text
for each adjacent face pair:
  compute normal_1 and normal_2
  angle = arccos(dot(normal_1, normal_2))
  if angle > threshold:
    mark shared edge as terrain edge
```

Deliverables:

- edge visualization for stairs, platforms, gaps, and rough terrain
- documented threshold choices
- failure cases where detection is noisy or incomplete

## Phase I: Foot Volume Point Penalty

Purpose: make the policy avoid risky partial foot contacts near edges.

Tasks:

- [ ] Define points inside each foot collision volume.
- [ ] Transform foot points into world frame every step.
- [ ] Query distance or penetration relative to terrain edge regions.
- [ ] Penalize contact near edges, especially high-velocity contact.
- [ ] Log the penalty separately.
- [ ] Visualize foot points during contact.

Simplified reward idea:

```text
edge_penalty = 0
for each foot_point:
  if foot is near contact and distance_to_edge < margin:
    edge_penalty += weight * (margin - distance_to_edge)
```

Deliverables:

- visualization of foot safety points
- edge penalty logs
- comparison of landing behavior with and without edge penalty

## Phase J: Ablation Study

Purpose: learn to think like a researcher, not only an implementer.

Run these experiments:

- [ ] Baseline blind locomotion.
- [ ] Depth input without edge penalty or flat patch sampling.
- [ ] Depth + flat patch sampling.
- [ ] Depth + edge penalty.
- [ ] Full simplified method.
- [ ] Full method without depth history.
- [ ] Full method without flat patch sampling.
- [ ] Full method without edge penalty.

Metrics:

- success rate by terrain type
- mean reaching time
- episode return
- fall rate
- unsafe edge-contact count
- foot landing area or distance-to-edge proxy
- command tracking error

Deliverables:

- one table like the paper's ablation table
- 3-5 videos of success and failure cases
- written interpretation of what each mechanism contributed

## Phase K: Report And Portfolio

Purpose: turn the learning into a senior-level artifact.

Final repo structure:

```text
paper-reproduction/
  README.md
  docs/
    paper-summary.md
    implementation-notes.md
    ablation-results.md
  scripts/
    train.py
    play.py
    export_policy.py
  source/
    tasks/
      hiking_repro/
  media/
    screenshots/
    videos/
```

Final report sections:

- Problem
- Related work
- What I reproduced
- What I simplified
- Isaac Sim / Isaac Lab environment design
- Observation design
- Terrain generation
- Flat patch sampling
- Edge detection
- Foot safety penalty
- Training setup
- Ablation results
- Failure cases
- Lessons learned
- Next steps

Portfolio claim I want to be able to make:

> I reproduced the core simulation mechanisms of a recent perceptive humanoid locomotion paper in Isaac Lab, implemented terrain-aware command generation and edge-aware foothold penalties, and evaluated them through ablations.

## 4. What Not To Do First

Avoid these traps:

- Do not start with full real-robot deployment.
- Do not try to train the exact final humanoid policy before understanding Isaac Lab.
- Do not copy the code blindly without mapping the architecture.
- Do not focus only on making a nice video.
- Do not skip ablations.
- Do not ignore failure cases.

The senior-level skill is not only making the robot move. It is knowing why it moves, why it fails, and which mechanism fixes which failure.

## 5. Weekly Schedule

## Week 1: Paper And Tooling

- [ ] Read the paper once quickly.
- [ ] Read the paper again and annotate methods.
- [ ] Install or verify Isaac Sim.
- [ ] Install or verify Isaac Lab.
- [ ] Run one Isaac Lab example.
- [ ] Clone Project Instinct repositories.
- [ ] Write a codebase map.

Output:

- paper summary
- installation notes
- first successful run screenshot

## Week 2: Baseline Isaac Lab Task

- [ ] Create or modify a simple locomotion task.
- [ ] Add simple terrain.
- [ ] Train or run baseline policy.
- [ ] Log rewards and reset reasons.

Output:

- baseline video
- baseline notes

## Week 3: Terrain And Perception

- [ ] Add stairs, gaps, ramps, and platforms.
- [ ] Add depth observation.
- [ ] Add processed depth visualization.
- [ ] Compare blind vs depth-conditioned behavior.

Output:

- terrain gallery
- depth visualization
- initial comparison

## Week 4: Flat Patch Sampling

- [ ] Implement flat patch sampler.
- [ ] Visualize patch targets.
- [ ] Convert target patches into velocity commands.
- [ ] Compare against uniform velocity commands.

Output:

- flat patch visualization
- command-generation notes
- comparison videos

## Week 5: Edge Detection And Foot Safety

- [ ] Implement terrain edge detection.
- [ ] Visualize detected edges.
- [ ] Add foot safety points.
- [ ] Add simplified edge penalty.
- [ ] Compare with and without edge penalty.

Output:

- edge visualization
- edge penalty logs
- failure case comparison

## Week 6: Ablations And Report

- [ ] Run final ablation set.
- [ ] Create result table.
- [ ] Record success and failure videos.
- [ ] Write mini paper-style report.
- [ ] Publish repo and notes.

Output:

- ablation table
- final report
- portfolio README

## 6. Senior-Level Checklist

I can call this a strong reproduction when I can do the following:

- [ ] Explain the paper's problem in one minute.
- [ ] Explain why blind locomotion is insufficient.
- [ ] Explain why mapping/localization pipelines are fragile for this setting.
- [ ] Explain the role of depth history.
- [ ] Explain flat patch sampling and reward hacking.
- [ ] Explain terrain edge detection and foot volume points.
- [ ] Implement a custom Isaac Lab task.
- [ ] Add custom observations.
- [ ] Add custom commands.
- [ ] Add custom rewards.
- [ ] Add custom terminations.
- [ ] Add terrain generation.
- [ ] Run training headlessly.
- [ ] Debug unstable simulation.
- [ ] Produce ablation results.
- [ ] Write a technical report.

## 7. Open Questions To Investigate

- How close can I get using only a simplified legged robot before using Unitree G1?
- Is full depth image input necessary, or can ray-cast height/depth features reproduce the main insight?
- How expensive is training on my hardware?
- Which part is hardest: terrain generation, perception, edge penalty, or RL stability?
- How sensitive is edge detection to terrain mesh quality?
- Does flat patch sampling help even with simpler robots?
- Can the same edge safety idea help manipulation, stepping stones, or loco-manipulation tasks?

## 8. Final Learning Outcome

If I complete this plan, I should understand Isaac Sim at a senior research-engineering level:

- not just opening scenes
- not just running tutorials
- but building a robot learning environment, reproducing a paper idea, measuring it, and explaining the result

