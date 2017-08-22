# Project: Neural Network Superviser
## Experiments
### 1) Batch ordering with respect to instance error
- Run 1 or 2 passes through the data and compute the error per instance
- Rank instances by error. Higher error produces higher rank
- Retrain network only on higher rank samples only. Check performance on test data
- Retrain with all data and check overall performance on test data
- Loop until beats some baseline

### 2) Batch ordering with respect to instance error and representation characteristics
- As before compute error per instance, but this time also compute metric in representation space (obtain from a layer in the neural network), per instance
 - e.g. This could be the difference from the mean separation from other instances
- Rank data by both error and ambiguity in representation space
- Continue on as in experiment 1

**Things to assess:**
- Which layer offers best representation?
- If the representation layer is the final fully connected layer, in the representation space metric ranked data pass, does freezing the forward weights produce better results?
 - "Diminish the output error based on the representation of the data"
 - Intuition here is that the network should refine the representation space that it uses, but can still use the representation space -> output mapping that will have worked for well represented data

### 3) Add more complexity to the Neural Network as necessary
If experiment 2 cannot obtain a better representation space for certain data, without always negatively affecting other data, then this might indicate that the neural network needs more degrees of freedom (more units)
- Add more units if experiment 2 does not produce better performance during each pass
- Repeat experiment 2 with new neural network structure

**Things to assess**
- Is it possible to add units but leverage the progress made from previous experiments?
 - e.g. "Catastrophic forgetting" experiment by DeepMind produced penalty on established performing weights, such that the more they were changed in subsequent experiments, the more they would resist. This effectively but a max change limit on the weights that were deemed useful.



