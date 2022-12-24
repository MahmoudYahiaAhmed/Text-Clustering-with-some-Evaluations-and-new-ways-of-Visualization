# Text-Clustering-with-some-Evaluations-and-new-ways-of-Visualization
![ClassicBooks](https://user-images.githubusercontent.com/109751694/209452042-00959eed-f89d-42ea-b480-8ca39057c711.jpg)
*All those books are fiction books, so they have the different genres*

### Books and Preprocessing to get 200 partition of each book.
![image](https://user-images.githubusercontent.com/109751694/209452109-efd58df4-d1cf-41f3-a430-4bb488831464.png)
![image](https://user-images.githubusercontent.com/109751694/209452117-002e5826-28e6-46f8-902d-5ef5a1b89823.png)
### words per partitions
![image](https://user-images.githubusercontent.com/109751694/209452136-6578b22a-da91-4cb3-84cc-7b290c167a01.png)

### Stop words and stemming 
![image](https://user-images.githubusercontent.com/109751694/209452150-e4699f7a-4e67-4f2d-a1c2-e5833f64c213.png)

### Most common words for each book
![image](https://user-images.githubusercontent.com/109751694/209452160-4833ff15-2c7f-4109-9375-a438b5ec0e34.png)

### Transformation and Embeding
### Dimensionality reduction Algorithems that will be check "LDA" & "PCA" & "T-SNE" & "UMAP"
#### BOW
![image](https://user-images.githubusercontent.com/109751694/209452171-810725fe-d404-4be8-9bc5-4b33e6b29f2f.png)
#### TF-IDF
![image](https://user-images.githubusercontent.com/109751694/209452180-3fbee1d7-1ec7-4d0d-bc14-38cbfa471d4a.png)
#### BOW-n-gram
![image](https://user-images.githubusercontent.com/109751694/209452184-bc7674d7-b743-479c-9cec-a9c5cfa97dd9.png)
#### TFIDF-n-gram
![image](https://user-images.githubusercontent.com/109751694/209452197-31cde3a2-7c6f-4842-9ccf-4f4b577f7432.png)
#### Glove
![image](https://user-images.githubusercontent.com/109751694/209452204-51162a0d-fc2c-4013-80b1-8a522b80c86f.png)
#### Word2Vec
![image](https://user-images.githubusercontent.com/109751694/209452217-b9f2024f-b165-4a67-8881-84fa665c1203.png)
#### FastTxt
![image](https://user-images.githubusercontent.com/109751694/209452243-9afc8698-8045-44a6-b061-36122a9e83e6.png)

### we have checked the Clustering Separability visually between each Embedding technique and 4 dimensionality reduction algorithms, and our conclusion is that U-MAP is the best in separating the clusters with the occurrence of embedding techniques, but LDA is the best for contextual embedding teqniques, but because we need to deal with the absent y_true case (unknown), so we will apply UMAP for all of them, also to fit the memory.
### U-MAP will be used with { BOW, TF-IDF, BOW-n-gram, Tf-IDF-n-gram, Glove, Word2vec, FastTxt}
![image](https://user-images.githubusercontent.com/109751694/209452247-78c917aa-f0b0-4667-b5ad-720e87b27832.png)
## Apply Clustering
#### K-means
![image](https://user-images.githubusercontent.com/109751694/209452289-3d4c500c-edc5-4699-86ae-07491904deca.png)
![image](https://user-images.githubusercontent.com/109751694/209452293-5874c571-5b4f-4080-afe4-b6693e50b099.png)
![image](https://user-images.githubusercontent.com/109751694/209452298-365b1345-e1bc-4814-b417-ecc0b8e56752.png)
### K-means with FastText Embedding with UMAP dimensionality reduction got the highest silhouette, calinski and lowest wsse, and the majority voting is K=3
![image](https://user-images.githubusercontent.com/109751694/209452317-86686099-b668-4bfb-bf5b-fb5e2837996b.png)
![image](https://user-images.githubusercontent.com/109751694/209452335-37e954f0-185e-4038-a641-8cc56120de43.png)

### FastText Embedding with UMAP dimensionality reduction got the highest silhouette, calinski and lowest BIC, and lowest AIC
![image](https://user-images.githubusercontent.com/109751694/209452348-380d857c-90b8-4c6b-8565-38dd7214aa49.png)
![image](https://user-images.githubusercontent.com/109751694/209452353-598fd6d4-87ec-4d8f-9521-697123945099.png)
### Hierarchical clustering
#### FastText Embedding with UMAP dimensionality reduction got the highest silhouette, calinski
![image](https://user-images.githubusercontent.com/109751694/209452408-be97d5fd-68f1-456d-95a7-bd0e2fc35a6f.png)
![image](https://user-images.githubusercontent.com/109751694/209452409-4ea3afad-f235-4559-a5e9-1d77d2bfb77a.png)
### Choose the winner model, that success to cluster the data with highest separability and will chosen based.
### *maximized the number of clusters (k=3)
### *maximized the silhouette_score & calinski_harabasz_scores
![image](https://user-images.githubusercontent.com/109751694/209452419-ca52394e-5869-43b7-95f1-7bedf1d19a97.png)
### According to the results, we will choose K-means as best model, because it has the same silhouette and highest calinski, and we will choose K=3 as the best, because the silhouette will not decrease too much.

### KAPPA
![image](https://user-images.githubusercontent.com/109751694/209452430-d0d971de-2fda-4548-8ead-afa42debc4aa.png)

### K-means with 3 achives 0.36 with Kappa measurement, but the highest Kappa achived by Hierarchical with k=5, but we still dealing with k-means K=3
![image](https://user-images.githubusercontent.com/109751694/209452433-eb2dd22a-a1ef-4a75-a1f5-28aaf4a89e51.png)
### From the confusion matrix above, there are some clusters that contain different books, which means those books were written in the same context because the FastText embedding was used and it's a contextual embedding, and the authors use the same lingo or same latent meaning to express their ideas.
### E.g clusters 1 and 2, but cluster 0, didn't overlap because it has a religious book.
### Another consideration, we already know that we have 5 books with different genres, and the number of clusters should be 5, and best k was just 3, according to model perspective, and we can't claim that this observation is wrong because here the cluster using the latent similarity which indistinct for humans, so that may be correct..
### Appling the LDA-topic modeling
### The best K-topics according to Coherence_score is 3
![image](https://user-images.githubusercontent.com/109751694/209452448-a6ab0b07-5919-4560-b619-f066f445582b.png)
### Apply Error Analysis, and get what confuse the models.
![image](https://user-images.githubusercontent.com/109751694/209452478-0a400442-029a-4045-89d7-70863938092e.png)
### Here are the most common words that caused the overlapping within cluster 3
![image](https://user-images.githubusercontent.com/109751694/209452490-794b9e21-7eca-4b02-81be-dabccc15c738.png)

## References
https://aclanthology.org/W15-0705.pdf
https://mirror-medium.com/?m=https%3A%2F%2Fmedium.com%2F%40haataa%2Fhow-to-measure-clustering-performances-when-there-are-no-ground-truth-db027e9a871c

