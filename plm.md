1. **BERT Loses Patience: Fast and Robust Inference with Early Exit**. arXiv 2020. [[pdf](https://arxiv.org/abs/2006.04152)]

During inference, instead of setting a threshold for early exit, the models exits when the predictions of each layer's classifier remain the same for a certain number of layers. Apart from inference speedup, it also achieves better robustness with ensemble effects (as it uses multiple layers' classifiers).


2. **Poly-encoders: Transformer Architectures and Pre-training Strategies for Fast and Accurate Multi-sentence Scoring**. ICLR 2020. [[pdf](https://arxiv.org/abs/1905.01969)]

For retrieval tasks with many candidates, cross-encoder (concat query + candidate and feed to transformer for every pair) is slow, bi-encoder (encoder and cache query and each candidate separately, use dot product as score) performs worse. Poly-encoder first encodes query and candidate separately which allows for caching of candidates. Then, it adds additional multi-head attention over context representations as well as context-candidate attention to get the final context embedding. The final score for each candidate is simply the dot product of final context embedding and that candidate embedding (aggregated over raw candidate encodings). This method is much faster than cross-encoder and also performs better than simple bi-encoder.


3. **STRUCTBERT: INCORPORATING LANGUAGE STRUCTURES INTO PRE-TRAINING FOR DEEP LANGUAGE UNDERSTANDING**. ICLR 2020. [[pdf](https://openreview.net/pdf?id=BJgQ4lSFPH)]

It extends BERT with two additional training objectives: 1) Randomly shuffle trigrams of unmasked tokens, and train the model to restore the correct word order (i.e. predict the original unshuffled token). This is trained together with MLM objective. 2) Upgrade the NSP objective to a three-way classification task for the relationship of the sentence pairs: next sentence, previous sentence, or a random sentence from a different document (Each type sampled 1/3 training examples).  
Adding these two simple objectives significantly improves the performance on downstream tasks compared to corresponding baselines.


4. **Improving Transformer Models by Reordering their Sublayers**. ACL 2020. [[pdf](https://arxiv.org/pdf/1911.03864.pdf)]

In the vanilla Transformer, each layer consists of a self-attention sublayer followed by a feedforward sublayer. The authors analyse the effect of reordering the sublayers by generating random transformer models, varying the number of each type of sublayer, and their ordering, while keeping the number of parameters constant. They find that models with more self-attention toward the bottom and more feedforward sublayers toward the top tend to perform better in general (on LM). Based on this, they propose sandwich transformer: `k` self-attention layers at the bottom, `(n-k)` self-attention + feedforward pairs in the middle, followed by `k` feedforward layers at the top. This model achieves better performance on LM than vanilla transformer, but no significant gains on translation. 


5. **Revisiting Few-sample BERT Fine-tuning**. ICLR 2021. [[pdf](https://arxiv.org/abs/2006.05987)]

Three useful tricks to improve BERT finetuning performance: 1) Adding back the bias-correction steps in BERTAdam optimizer improves stability especially for small datsets (and reduces degenerate runs). 2) Re-initializing the top K (K to be tuned) layers (including pooler layers) speeds up training and improves performance. 3) Training for more iterations (> 3 epochs) improves performance :)


6. **ReZero is All You Need: Fast Convergence at Large Depth**. UAI 2021. [[pdf](https://arxiv.org/abs/2003.04887)]

ReZero is a new technique for training deep neural networks (Transformers, ResNet, etc.), where we add a residual connection for each layer: x<sub>i+1</sub> = x<sub>i</sub> + &alpha;F(x<sub>i</sub>). The trainable parameter &alpha; is initialized as 0 at the beginning so it's just performing the identity operation, but it will dynamically evolve to suitable values during initial stages of training. For the original Transformers, each sublayer is added via a residual connection and then normalized by LayerNorm. We can replace this with ReZero connection. This achieves significant speedup for convergence. 




