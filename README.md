**Background:**
This is a random explanation of how vae's work - what i think is an interesting use case for them in the perfume domain and visualizations of perfume embeddings in 3d with umap.

A while back i tested a bunch of different approaches to mapping scent sentences into 3d using umap. I looked into VAE's to see which ones could help me detangle sentence transformer embeddings that represented short descriptions of perfumes. The goal was to map a perfume's scent into a navigatable 3d space.

**My hypothesis** 
Do Vae's provide some kind of added value on top of plain old scemantic similarity for better understanding perfume scent descriptions:

1) Establish a baseline for how well sentence transformer embedding's + cosine similarity can find similar perfumes.
  
2) Use this baseline to rank with ndcg@10 as a metric.

**The constants for this experiement are**:

• The sentence transformer model we use for this: 768 dims.

• Cosine similarity as a baseline measurement for finding similar perfumes from embeddings.

• We will do PCA on raw embeddings as well to understand baseline.

**The questions we will hopefully answer are:**

4) Does lossy reconstruction with a regular VAE improve ndcg@10 scores.

5) Does lossy reconstruction + disentanglement of latent features with a TC-VAE improve ndcg@10 scores.

6) Does latent disentaglement correspond with interpetable scent axis (x,y,z position) on umap. 
