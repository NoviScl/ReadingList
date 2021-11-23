1. **On Calibration of Modern Neural Networks**. ICML 2017. [[pdf](https://arxiv.org/pdf/1706.04599.pdf)]

Gave a clear definition of calibration, showed the reliability diagrams (divide into interval bins, compare expected accuracy and confidence within each bin). 
Evaluation metric: Expected Calibration Error (ECE): expected difference between confidence and accuracy (weighted average over all bins, where weights are relative size of each bin). 
Proposed an effective method: Temperature Scaling: divide logits by a temperature factor before doing softmax. The temperature is optimized wrt NLL on the dev set. TS doesn't affect model accuracy since the argmax is unchanged.


2. **Posterior calibration and exploratory analysis for natural language
processing models**. EMNLP 2015. [[pdf](https://arxiv.org/pdf/1508.05154.pdf)]

