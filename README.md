# Optimizer Comparison on Fashion-MNIST (AutoEncoder)

This project compares different optimization strategies for training a compact AutoEncoder on the Fashion-MNIST dataset.

## Objective
- Train an AutoEncoder to reconstruct input images
- Implement and compare optimizers and learning rate schedules
- Evaluate performance based on reconstruction loss, training time, and convergence behavior

## Model
- Dataset: Fashion-MNIST
- Model: Fully-connected AutoEncoder
- Task: Image reconstruction

## Methods
### Adam (baseline)
- Implemented from scratch (EMA + bias correction)
- Tuned learning rate (best: 0.0045)

### Adam with scheduling
- Linear warmup + cosine decay
- Trapezoidal schedule (warmup → constant → cosine decay)

### Shampoo-Lite
- Structured second-order optimizer
- Preconditioning using per-dimension statistics

## Results
| Method                      | Final Loss | Training Time |
|----------------------------|-----------|--------------|
| Adam                       | 0.0110    | 227s         |
| Adam + Cosine Schedule     | 0.0090    | 219s         |
| Adam + Trapezoidal Schedule| 0.0087    | 217s         |
| Shampoo-Lite               | 0.0107    | 730s         |

## Key Findings
- Learning rate scheduling significantly improves Adam performance
- The trapezoidal schedule achieved the best loss and fastest convergence
- Shampoo-Lite is computationally expensive and did not outperform Adam in this setup

## Insights
- Warmup stabilizes early training
- A constant learning rate phase improves exploration
- Cosine decay improves stability near convergence
- More complex optimizers are not always beneficial for smaller models

## How to Run
Open the notebook and run all cells.
