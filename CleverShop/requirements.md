---
title: CleverShop functional, non-functional, and deferred requirements
updated: 5/24/2026
tags:
- functional
- non-functional
- deferred
- requirements
- CleverShop
- design
summary: Assortment of functional, non-functional, and deferred requirements for the CleverShop web application.
---

# CleverShop requirements

This document details functional, non-functional, and deferred requirements for the CleverShop web application.

## Functional requirements

Listed below are functional requirements expected for initial release.

- User login system
    * User can create, access, modify, and delete their account
- Grocery list display
    * User can view grocery list
- Grocery list item add/delete
    * User can add and delete items to their grocery lists
- Multi-list system
    * User can maintain multiple grocery lists
- List item selection
    * User selects items to add, as opposed to typing them out
- Purchase record
    * User can mark list items as purchased
- Database hoster
    * Service to host program database
- Container hoster
    * Service to host program containers
- Domain
    * Suitable domain for program frontend

## Non-functional requirements

Listed below are non-functional requirements expected for intial release.

- User data in the backend
    * User data is saved in a remote server as much as safety allows
- Mandatory login
    * Web application cannot be used without an account. User must be logged in

## Deferred requirements

Listed below are deferred functional requirements to be implemented after initial release.

- Smart list fill
    * User data is used to partially or fully fill grocery lists
- Agentic assistant
    * A large-language model assists the user with grocery item choices
- Speech to text list fill
    * Grocery lists can be filled out using speech to text
- List sharing
    * User can share their grocery list within the app or online
- Custom list items
    * User can type out their own items if the existing selection is insufficient
- List pricing
    * Grocery list prices can be recorded for analytics
- Item pricing 
    * Item prices can be recorded for analytics
- Web scraping
    * Program can scrape grocery store websites to extract relevant information
- Item location display
    * User can see the in-store location of their items (e.g. aisle number)