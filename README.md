# Representation of a Real-World Problem as a Markov Decision Process

## Aim

To represent a real-world sequential decision-making problem as a Markov Decision Process (MDP) by defining its states, actions, transition probabilities, rewards, and Python representation.

## Problem Statement

### Problem Description

**Application: Traffic Signal Control**

A traffic signal controls vehicles at a road junction. The signal changes between red and green based on traffic conditions. The objective is to reduce traffic congestion and ensure smooth traffic flow.

The traffic signal acts as an agent, the road junction is the environment, and the traffic conditions determine the states. The agent selects actions and receives rewards based on traffic flow.

## MDP Components

A Markov Decision Process is represented as:

\[
MDP=(S,A,P,R,\gamma)
\]

Where:

| Symbol | Meaning |
|---|---|
| S | Set of states |
| A | Set of actions |
| P | Transition probability function |
| R | Reward function |
| γ | Discount factor |

## State Space

The state space represents the traffic conditions at the junction.

```text
S = {
    Low Traffic,
    Medium Traffic,
    High Traffic
}
```

## Sample State

**High Traffic:** A large number of vehicles are waiting at the junction, causing congestion.

## Action Space

The action space represents the possible actions taken by the traffic signal.

```text
A = {
    Red Signal,
    Green Signal
}
```

## Sample Action

**Green Signal:** The signal allows vehicles to move through the junction, helping to reduce congestion.

## Transition Probability

Transition probability represents the probability of moving from one traffic state to another after an action is taken.

General form:

\[
P(s'|s,a)
\]

Example:

If the current state is High Traffic and the action is Green Signal, the probability of moving to Medium Traffic may be 0.7.

\[
P(\text{Medium Traffic}|\text{High Traffic},\text{Green})=0.7
\]

This means there is a 70% probability that traffic changes from high to medium after the green signal. This is an illustrative probability.

## Reward Function

The reward function provides feedback based on traffic conditions.

\[
R(s,a,s')
\]

Example:

- +10 for reducing traffic congestion.
- +5 for maintaining smooth traffic flow.
- -10 for increased traffic congestion.

The objective is to maximize the total reward and reduce traffic congestion.

## Graphical Representation

```text
       Green Signal
  ┌────────────────────┐
  │                    ▼
Low Traffic ──────► Medium Traffic
     ▲                    │
     │                    │ Green Signal
     │                    ▼
     └──────────── High Traffic
                (Congestion)
```

The states represent traffic conditions, and the arrows represent possible transitions after actions. Rewards are assigned according to changes in traffic conditions.

## Python Representation

```python
# MDP Representation using Python

print("Name: __________________")
print("Register Number: __________________")

states = {
    0: "Low Traffic",
    1: "Medium Traffic",
    2: "High Traffic"
}

actions = {
    0: "Red Signal",
    1: "Green Signal"
}

# Illustrative transition probabilities
transitions = {
    ("High Traffic", "Green Signal"): {
        "Medium Traffic": 0.7,
        "High Traffic": 0.3
    },
    ("Medium Traffic", "Green Signal"): {
        "Low Traffic": 0.6,
        "Medium Traffic": 0.4
    },
    ("Low Traffic", "Red Signal"): {
        "Medium Traffic": 0.4,
        "Low Traffic": 0.6
    }
}

# Reward function
rewards = {
    "Low Traffic": 10,
    "Medium Traffic": 5,
    "High Traffic": -10
}

gamma = 0.9

print("\nStates:", states)
print("Actions:", actions)
print("Transition Probabilities:", transitions)
print("Rewards:", rewards)
print("Discount Factor:", gamma)
```

## Output

```text
Name: __________________
Register Number: __________________

States: {0: 'Low Traffic', 1: 'Medium Traffic', 2: 'High Traffic'}

Actions: {0: 'Red Signal', 1: 'Green Signal'}

Transition Probabilities:
{('High Traffic', 'Green Signal'):
 {'Medium Traffic': 0.7, 'High Traffic': 0.3},
 ('Medium Traffic', 'Green Signal'):
 {'Low Traffic': 0.6, 'Medium Traffic': 0.4},
 ('Low Traffic', 'Red Signal'):
 {'Medium Traffic': 0.4, 'Low Traffic': 0.6}}

Rewards: {'Low Traffic': 10, 'Medium Traffic': 5, 'High Traffic': -10}

Discount Factor: 0.9
```

## Result

The real-world problem of traffic signal control was successfully represented as a Markov Decision Process by defining the state space, action space, transition probabilities, reward function, and Python representation.
