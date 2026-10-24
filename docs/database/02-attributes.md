# Attributes

These are the facts each entity stores. Data types and sizes come later, in the physical model.
The **key** attribute (underlined in the Chen diagram) is marked with `(key)`.

## Entities

| Entity | Attributes |
|---|---|
| Customer | customer id (key), full name, email, phone, date joined |
| Skin profile | customer id (key), skin type, budget, vegan only |
| Address | address id (key), line 1, line 2, city, postcode, country, is default |
| Brand | brand id (key), name, country of origin, description |
| Category | category id (key), name |
| Product | product id (key), name, short description, description, how to use, size, price, stock, vegan status, cruelty-free |
| Ingredient | ingredient id (key), INCI name, common name, description, animal-derived |
| Order | order id (key), order date, status, total |

## Attributes that belong to a relationship

A many-to-many relationship can carry its own facts. In the Chen diagram, these hang off the diamond.

| Relationship | Attributes |
|---|---|
| Product to Ingredient | position in the ingredient list |
| Order to Product | quantity, price at the time of purchase |

## Notes

- Skin profile uses the customer id as its key, because each customer has at most one profile.
- Order total can be worked out from its products. It is a derived attribute, and we decide later whether to store it.
- Each order links to one saved Address (one-to-many from Address to Order). A used address should not be deleted while orders still point to it, so the database will block that.
