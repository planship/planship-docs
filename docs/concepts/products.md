## Products

In Planship, a product is a container that defines pricing [plans](/concepts/plans) along with [feature](/concepts/feature-levers) and [metered](/concepts/metered-levers) levers, and it typically represents a single product offering for your customers. However, a Planship product can also represent a part of a larger product, a group of products, or whatever makes sense for your business.

!!! Example
    Imagine a large product that is marketed as a single solution and is built on a single tech stack, but in reality consists of several distinct offerings that are priced independently of one another.

### Name and slug

Every product has a unique _name_, which is used to automatically generate a _slug_. The product slug is unique within the organization, and is used to identify the product in all Planship API operations.

## Organizations

An organization is a top level container for your Planship products and [customers](/concepts/customers), and it typically represents your business or a part of it (E.g. a division of a larger company).

## Users

Organizations and all related resources (E.g. products, plans, etc.) are managed by Planship users, with access based on the following roles:

- **Admin** - can perform all operations including organization deletion (along with all of its data)
- **Collaborator** - can perform all operations with the exception of organization deletion
- **Read-only** - read only access to all data

Every organization has at least one user attached to it, and a user can belong to any number of organizations.
