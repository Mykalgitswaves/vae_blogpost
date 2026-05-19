**Background:**
This is a random explanation of how vae's work - what i think is an interesting use case for them in the perfume domain and visualizations of perfume embeddings in 3d.

A while back i tested a bunch of different approaches to mapping scent sentences into 3d using umap. I looked into VAE's to see which ones could help me detangle sentence transformer embeddings that represented short descriptions of perfumes. The goal was to map a perfume's scent into a navigatable 3d space.

**My hypothesis** 
Do Vae's provide some kind of added value on top of raw embeddings for better understanding perfume scent descriptions:

1) Establish a baseline for how well sentence transformer embedding's + cosine similarity can find similar perfumes.
  
2) Use this baseline to rank with ndcg@10 as a metric.

**The constants for this experiement are**:

• The sentence transformer model we use for this: 768 dims.

• Cosine similarity as a baseline measurement for finding similar perfumes from embeddings.

• We will do PCA on raw embeddings as well to understand baseline.

**Developing our test set for ranking scores**:

Fragrantica similarity is what we will use as the defacto source of truth for figuring out whether our perfumes that are in the same neighborhood actually smell similar. We will make a test set of perfumes from that for generating our ndcg@10 metric.

**The questions we will hopefully answer are:**

4) Does lossy reconstruction with a regular VAE improve ndcg@10 scores.

5) Does lossy reconstruction + disentanglement of latent features with a TC-VAE improve ndcg@10 scores.

6) Does latent disentaglement correspond with more distinguished / interpetable scent neighborhoods. 

**Some blatant holes in this project**:

Semantic similarity is not a 1 - 1 translation to olifactory perception. Meaning, words can be similar but scents can be really different when combined. 
If the goal is to find things that smell the same semantic similarity is likely not the silver bullet we are looking for.

UMAP is not a reproducable metric for determining neighborhoods - because it differs on every run. We should find a better way to evaluate the neighborhoods of our embeddings using unsupervised learning - maybe spectral clustering or graphs?

---

#### other things i found while looking online:

Theres a whole dataset of molecules and their scent behavior here: https://github.com/pyrfume/pyrfume-data
Maybe there is a way to use these to double check scent embeddings, the problem is that our data's not weighted. but maybe these could help us make the correct weights for each of our words. I.e. Basenotes of bergamont get a .25 penalty when combined with top notes of lilac (floral) because they behave a certain way.
