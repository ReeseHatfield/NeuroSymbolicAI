# TransE Paper notes

## Introduction

- Multi-Relational Data = Directed Graph
    - Node = entity
    - Edge = (head, label, tail)

- Use patterns in this mutli-relational to generalize to other uses
    - Between one entity-to-ALL of the others
- Can model more complex relations between data, that is not simple one-to-one
- "Following the success of user/item clustering or matrix factorization techniques in collaborative
filtering to represent non-trivial similarities between the connectivity patterns of entities in single-
relational data," -> What the hell

- Last paragraph kinda lost me

## Relationships as translations in the embedding space

- energy-based model ?
- TransE -> learning low dimensional vector space
- In TransE 
    - relationships = translations in the embedding space
    - if (h,l,t) holds true:
        - (t should be close to h) + some vector depending on l
    - In TransE, we learn only one low, dimensional vector for each eneity and each relationship
- Chose parameter budget based on based on (number of?) relationships
    - Number of KEY-RELATIONSHIPS in the knowedge base

- Despite being mostly designed for heirarchical data, TransE works well for most kinds of relations

## Training algorithm
- Basically completely lost on this ngl
- Revisit this


## Transation Based Models

- We want that h + l =~ t (or at least be the neartest neighbor of t)
- Energy(h,l,t) = d(h+l, t), where d(v1,v2) is a dissimilarity metric (L1 or L2 norm)
- Corrupted Triplets for training = training triplets with either the head of the tail replaced
- the loss function favors lower values of energy
- Run stochastic gradient descent with that loss function over all possible h,l,t


## Related work
- Structued Embedding embeds entities into R^k, and relationships into two matrices
    - L1 = R^(k x k)
    - L2 = R^(k x k)
- such that d(L1 * h, L2 * t) is large for corrupted tuples
    - and small otherwise
- when two entities belong to the same triplet, their embeddings should be close to one another
- TransE performs better than a normal SE because TransE is a more direct way of representing the relationship
    - (1) our model is a more direct way to represent the true properties of the relationship
    - (2) optimization is difficult in embedding Models


### Neural Tensor Models
- another approach is a neural tensor model
- learning score s(h,l,t) = h^T * Lt + l1^T * h + l^T * t
- 

## Experiments:
- TransE evaluted on data from FreeBase and WordNet
    - Wordnet: Designed to product dictionary and thesaurus, as well as auto text analysis
        - ex triplet: ( score NN 2, has part, musical notation NN 1)
    - FreeBase: KB of general facts,
        - KB has 1.2 Billion triplets
        - KB has 80 Million entities

- Unclear is all relationship types can be modeled effectively:
    - 1-1, 1-Many, etc, (#head-to-#tail)

- Overall, you are predicting the tail of a relation
- Should figure out how this is different from Structured Embedding
