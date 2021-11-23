1. **"You are grounded!": Latent Name Artifacts in Pre-trained Language Models**. EMNLP 2020. [[pdf](https://arxiv.org/abs/2004.03012)]

The authors used a set of experiments to demonstrate the artifacts associated with names in pretrained language models: 1) Prompt the PLM with given names, the most likely next word predicted by the PLM is the last name of a prominent named entity (e.g., Donald -> Trump); 2) Simple classifiers can easily recover masked given names of frequently discussed people in the media, as compared to other people; 3) Sentiment classifiers given strong negative sentiments to many names of people discussed in the media. Furthermore, they found that name swapping significantly drops model performance on template-based synthetic QA test sets.

