# Entities and relationships

## Entities

| Entity | Why it exists |
|---|---|
| Customer | A person with an account who browses the shop, saves their skin details and places orders. |
| Skin profile | Stores a customer's skin type, budget and whether they only want vegan products, so the shop can match products to them. |
| Address | A place a customer can have orders delivered to. A customer can save more than one. |
| Brand | The company that makes a product. Each brand comes from Korea, Japan or China, and shoppers often search by brand. |
| Category | The type of product, such as cleanser, serum or lip tint, so shoppers can browse by type. |
| Product | An item for sale, with its price, size, stock, vegan status and cruelty-free status. |
| Ingredient | One ingredient from a product's ingredient list, with whether it is animal-derived. The vegan status is based on this. |
| Order | One purchase by a customer, with its date, status and total. |

## Relationships

| Relationship | Cardinality | Ordinality (mandatory or optional) | Why |
|---|---|---|---|
| Customer to Skin profile | one-to-one | A skin profile must belong to one customer. A customer may not have a profile yet. | A customer has only one set of skin details, and they might skip filling it in. |
| Customer to Address | one-to-many | An address must belong to one customer. A customer can have zero or many addresses. | A new customer has no saved address yet, and someone might save a home and a work address. |
| Customer to Order | one-to-many | An order must belong to one customer. A customer can have zero or many orders. | A customer who has just signed up has not bought anything yet. |
| Brand to Product | one-to-many | A product must have exactly one brand. A brand can have zero or many products. | Each product is made by one brand, and a brand makes many products. |
| Category to Product | one-to-many | A product must have exactly one category. A category can have zero or many products. | Each product is one type of thing, and a category holds many products. |
| Product to Ingredient | many-to-many | A product must have at least one ingredient. An ingredient can be in zero or many products. | The same ingredient, such as glycerin, appears in many products, and each product has many ingredients. A junction table will also store the order of the list. |
| Order to Product | many-to-many | An order must contain at least one product. A product can be in zero or many orders. | An order can hold several products, and a popular product appears in many orders. A junction table will store the quantity and the price at the time of purchase. |

## Decisions

- Vegan status: each ingredient is marked animal-derived (yes, no or unknown). Each product then gets a status of vegan, contains animal-derived ingredients, or unverified when the source of an ingredient is unclear.
- Cruelty-free: stored separately on the product as yes or no, because vegan is about ingredients and cruelty-free is about animal testing.
- Passwords: not stored in the shop's own tables. Supabase handles logins, so the Customer table only holds profile details such as name and phone.
