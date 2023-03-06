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

A database is made up of many tables.
A table is made up of many records.
A record is made up of many fields.

# Normalisation

A process used to come up with the best possible design for a database. Tables should be organised
so that data is not supplicated in the same table or different tables. The structure should allows
complex queries to be made. There are 3 main stages of normalisation: first normal form (1NF),
second NF (2NF), and third NF (3NF).

1NF contains no repeating attributes or groups of attributes. All attributes must be atomic
(separate first and last names etc.).

2NF requires 1NF and contains no partial dependencies. This can only occur is the primary key is a
composite key. Identify a table's purpose; for each column, it must describe what the primary key
identifies. If it doesn't, then it should belong in a different table. For example, in a
`tblEmployee`, all columns should describe an attribute of the employee identified by the primary
key.

If a table has a composite primary key, then it is only in 2NF if each column directly relates to
*both* parts of the primary key. The table must refer entirely to a singular entity.

3NF requires 2NF and contains no non-key dependencies. All attributes are dependent entirely on the
primary key and nothing else.

A normalised database is much easier to maintain and change; there is no unnecessary duplication of
data; integrity is maintained and updates are small; having smaller tables with fewer fields makes
searching faster and saves storage.
