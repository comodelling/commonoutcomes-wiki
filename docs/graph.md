# Graph of change

Here, we define the graph model underlying CommonOutcomes.

## Causal relations

Change cannot happen in isolation, it presupposes causes and/or effects.[^1]
Therefore, our model needs not only to represent units of change, but also their causal interconnections.

This leads us to consider, in its simplest form, a directed graph where nodes are the units of change, and edges represent relations of causality. Parents of a given node can be seen as conditions or causes, and child nodes as implications, effects, consequences, or follow-ups... Causality does not need to be strict: a condition—or set of conditions—may be neither sufficient nor necessary. The only assumption is that some form of causality exists between a parent node—or set of parent nodes—and its children.[^2]

!!! example "Example"
    ```mermaid
    graph LR
      ConditionA --> Change --> Consequence1
      Condition2 --> Change --> Consequence2
    ```

## Properties

We use a property graph as underlying data model to attach various properties to our nodes and edges: currently an *id*, a [*scope*](semantics.md#scope), a [*status*](evolutivity.md#status), a *description*, *references* and *tags*.


## Schema

Though graph databases, contrary to relational databases, do not require a fixed schema, we propose here to enforce a graph schema.
Each node is identified uniquely by an *id*, and must have a *title*, a *type*, and a *scope* properties. Furthermore, node *types* can only take certain values according to our agreed [semantics](semantics.md), forcing an important discussion about terms.
Each edge is identified by a pair of *ids*, one of the parent and one for the child, and a single type *imply* (or *implication*), representing the relation of soft causality discussed above.

Given the [participatory](collaboration.md) and [evolutive](evolutivity.md) nature of the project, we do not assume that the absence of an edge means that no such relation exists in the real world. This is called the Open World Assumption (OWA).


[^1]: Of course, sometimes there are no identifiable causes, and effects may be unclear. If no potential cause or effect can be identified, we will refer to it as "isolated" change, and will consider it irrelevant for the current project.

[^2]: If we associate a random variable to each node, a conditional probability to each edge, and assume no loop in the graph, this model fits what is called a graphical causal model, causal graph or causal bayesian network.
