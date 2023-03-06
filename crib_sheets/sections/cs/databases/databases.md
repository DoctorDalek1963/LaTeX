A simple (flat file) database is a single file containing information on a single entity.

An *entity* is a category of object, person, event, or thing about which data needs to be recorded.

An entity maps to a table. A table contains many records, each holding information about a
particular instance of an entity. For example, a `customer` table will contain many records, each
representing a single customer.

Each record of an entity table needs an identifier to uniquely identify it. The identifier is known
as the *primary key*.

A composite primary key is a combination of keys in a record, where the *combination* uniquely
identifies the record rather than having a separate ID key.

Most databases automatically index the primary key field so that any particular record can be found
quickly.

If another key field also needs to be searched for, then it can be called a *secondary key*, and
this field will be indexed.

Entities can be linked by one-to-one, one-to-many, or many-to-many relationships.

TIKZ: boxes contain entities, relationship lines have a single line conn to box for one, and a
crow's foot conn for many

To create a relationship between entities, the "many" side must have a *foreign key*, which matches
the primary key in another table.

TIKZ: Draw database diagram from notebook

*Referential integrity* means that no foreign key can reference a non-existent record in a related
table.

As a canonical example, a customer can have many orders; an order can have many orderLines (an
order is like a shopping cart, and an orderLine is like a single order with product, quantity,
price); a product can appear in many orderLines.

Many-to-many rels cause problems with unknowable column numbers. This can be fixed with a *linking
table*. Suppose a fitness center - members can take many classes, and classes can have many members.
Instead, have an enrolment table in the middle. A member can have many enrolments, and a class can
be part of many enrolments. Each enrolment record is a single link between a member and a class.
