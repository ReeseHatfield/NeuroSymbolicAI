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

    - lookup table somwhere for h,t -> r ?
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