# Compare and Contrast different KGEs

- Knowledge graph embedding is the task of completing the knowledge graphs by probabilistically inferring the missing arcs from the existing graph structure


## Scores
![scores](../img/kge_scores.png)
- One difference is the score function (see dissimilarity function I think?)
- TransE
    - emb("PersonA") = h
    - emb("PersonB) = t
    - hopefully, h + r ~= t
    - represented via those triples 
    - Their relationship, is just a translation vector
    - scoring function is negative distance between h+r and t, or f=−∥h+r−t∥ sub 1/2
    - TODO FIND OUT WHAT TYPES of relation this can stores
        - then what it does well/not so well

    - "where the tail entities (t 1 , t2 , ..., t m )
        are all pushed into a cramped range because mini-
        mizing loss function impels every training triplet to
        satisfy ||h + r  t|| = 0, leading to h 1 = h 2 =
        ... = h m in the worst case" - from TransM paper, but it makes sense why it's bad at handling "many" relations

- Would like to talk about Unstructed at some point

- TransM
    - Just an extension of TransE
    - Introduces a weight for each triple
    - adjust importance based on confidence/relevance
    - this makes it bad for noisey dataset
    - "pre-calculating the distinct weight for each training triplet"
    - authors keep dissing TransE authors for its inability to handle "many" relations
        - "In reality, however, there are roughly only 26.2% ONE-TO-ONE triplets that are suitable to be modeled by TransE."
    - comparable parameter complexity to TransE
    - weights are measured using (tails per head) and (heads per tail)
    - "many" relations will have a much higher number of tph and hpt
        - for instance, parentOf might have a low number of tails per head, and a high heads per tails
        - low parents, high children
    - normalized to a unit sphere around where the relation points to
- TransH
    - Hyperplane?
    - project h,r,t into a hyperplane specific to that relation.
    - since the hyperplan is relation specific, it can better capture information about that relation
    - Pairwise (h1, t2) vs (h2, t2 )closeness will be preserved in the hyperplane
    - You just learn for the best hyperplane, starting at random -> minimize loss  
    - useing a relation specific hyperplan allows for better encoding of semantics
        - which is why it is better than TransE at [-many] type realtionships
- TransR
    - Why stop at just a hyperplane lol?
    - introduce a specific relation space 
    - TransR learns a separate space for each relation
    - even more flexible than TransH (and TransE)
    - each relation r, gets it's own relation space
    - each relation gets its own matrix M_r. 
        - so h_r (head in the relation space) = M_r * h
        - same for the tail
    - can map symetric relations well
        - a matric M can easily map t and h to the same point in relation space
        - which means they can still be different in entity space :0

    - to solve that, it separates entity space, from relationship space
    - h, t are elements of R^k
    - r is an element of R^d
        - d =  num entities
        - k =  num relations
    - those semantic spaces no longer need to be of the same dimension
    - projection matrix for each relation??
    - can model 1 to many relations better
        - say h is related to both t1 and t2,
        - map h to h` in relation space
        - then map t1 and t2 to the same place in relation space
        - while all three remain separate entities in entity space