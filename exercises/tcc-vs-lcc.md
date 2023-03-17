# TCC *vs* LCC

Explain under which circumstances *Tight Class Cohesion* (TCC) and *Loose Class Cohesion* (LCC) metrics produce the same value for a given Java class. Build an example of such as class and include the code below or find one example in an open-source project from Github and include the link to the class below. Could LCC be lower than TCC for any given class? Explain.

## Answer


TCC = LCC only if only indirect link of a graph has also a direct link. Ex :

Let the nodes A, B, C, D, and E
There is link between [A, B], [A, C], [B, C]


No LCC is equal or superior to TCC