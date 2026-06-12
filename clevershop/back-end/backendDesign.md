---
title: CleverShop backend design
updated: 6/1/2026
tags:
- backend
- architecture
- microkernel
- clevershop
summary: Backend design for the CleverShop web application, centered on a microkernel core with optional feature services.
---

# CleverShop backend design

The main idea is simple: keep one core backend that handles the important shopping-list features, then add separate services later for the extra stuff.

## Design goals

The backend should support the requirements in this repository without making the code harder to maintain than it needs to be.

The required parts of the app, like accounts, login, grocery lists, and marking items as purchased, belong in the backend kernel. Optional features such as smart list filling, speech-to-text, list sharing, and scraping should stay separate so the base app still works if they are not present.

User and list data should stay on the server, and protected requests should only work after the session is checked.

## Architectural style

CleverShop uses a microkernel design in the backend.

## Design drawing

See the diagram in [backendDesign.svg](backendDesign.svg).

## Core data flow

1. The user submits login credentials.
2. The frontend sends the credentials to the kernel.
3. The kernel checks the stored account record and compares the password hash.
4. If the credentials are valid, the kernel creates a session identifier.
5. The kernel returns success and session information to the frontend.

1. The frontend sends a request with the session identifier in the authorization header.
2. The kernel validates the session.
3. The kernel queries the database for the user’s lists or items.
4. The kernel applies business rules and formats the response.
5. The frontend renders the returned data for the user.

1. The frontend requests a feature that depends on optional backend logic.
2. The kernel validates the session and gathers the required raw data.
3. The kernel sends that data to the relevant optional service.
4. The service returns structured results.
5. The kernel merges those results with the rest of the response and sends it to the frontend.

When a user creates an account, the frontend sends the details to the kernel, the kernel checks the input and stores the account if it is valid, and then it returns the result.
When a user logs in, the kernel checks the stored account record, compares the password hash, and creates a session ID if the login is valid.

When the frontend asks for list data, it sends the session ID in the authorization header, the kernel checks that session, fetches the user data from the database, applies the business rules, and returns the formatted result.

If a feature depends on an optional service, the kernel should validate the session, gather the needed raw data, send it to the service, and merge the returned result into the final response.

## Suggested module layout

The kernel should still be split into a few internal modules so the code stays readable.

- API layer for routing, request parsing, and response formatting
- Authentication layer for login, session creation, and session checks
- Account layer for account CRUD behavior
- Grocery list layer for list and item operations
- Purchase layer for purchased-item updates and related state
- Integration layer for communication with optional services
- Database access layer for queries, updates, and transaction boundaries

## Data entities

The backend should center its storage around a small set of core entities.

User represents a registered CleverShop account. Typical fields include user ID, email, username, password hash, created timestamp, and updated timestamp.

Session represents a logged-in user session. Typical fields include session ID, user ID, creation timestamp, expiration timestamp, and revocation state.

Grocery list represents one named shopping list owned by a user. Typical fields include list ID, user ID, list name, created timestamp, and updated timestamp.

List item represents one item in a grocery list. Typical fields include item ID, list ID, item label or selected item reference, quantity, purchased state, and purchased timestamp.

Optional metadata such as pricing, suggestions, or sharing tokens can be stored separately so the core records stay light.

## API design

The frontend should communicate with the backend through a JSON API over HTTPS.

The main endpoint groups are:

- account endpoints for create, update, delete, and fetching current account details
- authentication endpoints for login, logout, and session validation
- list endpoints for create, fetch, rename, and delete
- item endpoints for add, remove, mark purchased, and unmark purchased
- optional feature endpoints for smart suggestions, speech-to-text, sharing helpers, and data enrichment

## Security considerations

Security matters here because CleverShop stores user-specific shopping data on the backend.

- Passwords must never be stored in plain text.
- Session IDs must be verified on every protected request.
- Input should be validated before database writes.
- Authorization checks should make sure users only access their own data.
- Optional services should receive only the minimum necessary data.
- Sensitive information should stay server-side whenever practical.

## Reliability considerations

The kernel should fail in a predictable way and keep the core app usable whenever possible.

- If an optional service fails, the kernel should degrade gracefully instead of stopping the whole app.
- Database failures should return clear errors to the frontend.
- Requests that fail authentication should stop before database access.
- Multi-step write operations should use transactions when consistency matters.

## How this design fits the requirements

- User login is handled by the kernel through account and session management.
- Grocery list display is handled by the kernel through list retrieval and formatting.
- Grocery list item add and delete are handled by the kernel through item management.
- Multi-list support is handled by the kernel through the list entity model.
- List item selection can be supported by the kernel and expanded later by optional services.
- Purchase recording is handled by the kernel through item state updates.
- Deferred features map cleanly to optional services outside the kernel.

