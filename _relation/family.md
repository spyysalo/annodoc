---
layout: entry
title: "FAMILY"
shortdef: "familial relationship between humans"
---

The `FAMILY` relation is annotated between two `PERSON` entities that
are stated to stand in any familial relationship.

<!-- details -->

Example:

~~~ ann
Michelle Obama is the wife of Barack Obama.
T1 PERSON 0 14 Michelle Obama
T2 PERSON 30 42 Barack Obama
R1 FAMILY Arg1:T1 Arg2:T2
~~~

------------------------------------------------------------------------------

(This is an example entry in the `relation` collection. You can find
the source of this document in the `_relation/` directory, file
`family.md`. To add new entries like this, simply add new `.md` files
into the `_family/` directory.)
