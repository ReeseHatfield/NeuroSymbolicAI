# NeuroSymbolic AI (actual course name, jfc)
Neural Systems + Symbolic Systems

TODO -> Watch ML videos
## Neural SYstem 
- Transformers
- ANNS + deriatives
- GNN
- 


## Symbolic Systems
- Knowledge Graphs
- "Knowledge" -> Logic based Systesm -> Ontology
    - "Logic" -> First order logic, PDDL, Discourse Representation, Description Logic
- Expert Systems -> Diagnosticians -> Decision Trees
    - Model any decision tree with a neural networks and vice vcersa
    - Diagnosticians -> Chatbot based systems

-----------------------------------------------

## Ontology 
- Philospohy -> Old as hell
- Study of classifciatino as conceptualizations
- How to put reality into nice boxes
- In comp sci, term orginates in like late 70s ish
- Formally investigated in mid 90s, by some guy bnamed Gruber (93)
- Ontology now defined as "Explicit conceptualization "
    - take concepts of the world and encode in such a way that you can share with another person AND  computer
- Define with human sysmbols, then replace with computer sysmbols
    - then contrain how they interact with one another

## Defintions

An Ontology O, is a tuple defined as 

- O = < Tbox, Abox, Rbox >
- TBox = = set of terminological axioms
- Abox = set of assertional axioms
- RBox = set of rule axioms


### axioms

terminological axioms
- C, D := T, (inverse T)

ER.C
C|-|
This is a grammar, google it


see atomic and complex 

- Any ontology is a set of those grammar statements

#### Assertional axioms
Description: that some entity is an instance of another class
OR
Telling you how they are related to another entity
syntax: 

R(a,b) -> those are related
A(a) -> a is an instance of A

can chain together

R(a,b) AND A(a) 
Can be expressed in graph form 

Arrows -> R (for relation)
or 
(Type)

- Rbox is the set of relations in that format

Can have relational higharchy

Sibling >= Brother
Brother <= Sibgling

### Encoding somethign human understandable

Father === Parent (intersect) Male
Son === Child (intersect) Male

Cogan (son of)-> Bill

This is tricky beacuse a son cannot NOT be a Child
But a father cannot NOT be a a male, but can not be a parent
Overall, a son must be a child, but a father may not always be a son,

Cogan (performs)-> Son Relation <-(provides) Bill


inverse(R) === R^-
R === R^- (role is reflexive)
symmetric(R)
transitive(R)

R <= R * R  (role chaining)

Son <= performsSonRole * providesSonRole^- (- for going backwards in the chain)

sonOf(Cogan, Bill)

Bill -> must be a parent
Cogan -> must be a male
in order for sonOf(Cogan, Bill) to be true

A sonOF . Male <= T (domain???)

T <= A sonOf. Parent (range???)

Cogan slot = R^- filler (head)
Bill slot = R Filler (tail)


T <=sonOf. Parent 

graph = set of assertions that form a graph
Cogan (sonOf) -> Bill

can infer that Bill -> Parent


Ax T(x) -> [Ay sonOf(x,y) -> Parent(y)]


sonOf(Cogan, Bill)
----------------------
Parent(Bill)

can save space in the triple stores


Go fucking research this shit cause god damn


### Motivations

- Logic based systems -> deductions
- Axiom of explosion
    - One bad fact in Knowledge base -> can derive all false facts
    - Poisons the Graphs
Devin (sonOf)-> Bill

We can infer that Siblig(Cogan, Devin)
But what is cogan is not the son of Bill, but we already inferred that
they are siblings

- We are not "Brittle"

- Need to check EVERYTHING to find faulty reasoning
- Tablua Algos, are double exponetions 2^2^N
- at least in the worst case

How do we use ML to do some of these tasks?
- If we have noisey data, can we still get inferences out of it?
- Open question of if this shit is even possible
- What are the effective mchansims of providing a nueral system to get a useful knowledge graph

- ChatGPT -> turn this note sinto knowledge graphs (homework)
- Seriously need to research how the fuck knowledge graphs work


## Use knowedge graphs with neural systems
- Word embeddings, but with knowledge graphs
- Translational embeddings
- Foundation way of creating an embedding via graph

(E, R)

MinErr(t =~ h + t)



## By thursday
- Get the paper
- Read the paper
- Do not expect to understand it, but read it at least (for me lmao)
- Take down a list of questions about it
- Will discuss thursday
    - What we didn't get
- Will discuss next week
    - the science behind it
    - think about projects

## How to read that fucking paper    
- Read it once
- basic underlining of shit I dont get
- Sleep on it
- Read it again, take notes
- 