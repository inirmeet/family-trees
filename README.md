# Family Tree

A web app for storing and displaying family trees. Anyone can browse and
search families; owners log in to build and maintain their family's tree.

> **Status:** planning. The app is not built yet, so this README describes
> the intended design. Setup commands will be confirmed once the code lands.

## Features

### Family List (public)
- Lists every family whose tree is stored.
- Search by family name or by member name.

### Family View (public)
- Shows a family as a tree, one node per member.
- Each node shows the member's photo and name.
- Clicking a node shows date of birth, date of death (if applicable),
  place of residence and a short bio.
- Pan and zoom for large families.
- SEO friendly, so each family page can be found through web search:
  - Readable URLs such as `/family/sanghani-family`
  - Server-side rendered HTML
  - Per-family title, meta description, canonical URL and Open Graph tags
  - Auto-generated `sitemap.xml` and a `robots.txt` that allows crawling

### Create & Edit Tree (login required)
- A logged-in user can create a tree; each tree represents one family.
- A tree can have several owners. Any owner can add, edit and remove
  members, and add other registered users as owners.
- Everyone else has read-only access.

## Tech stack

| Layer      | Choice                                             |
| ---------- | -------------------------------------------------- |
| Front end  | Nuxt 3 (Vue 3), server-side rendered public pages  |
| Back end   | Nuxt server API (Node.js)                          |
| Database   | SQLite                                             |
| Layout     | Responsive: phone, tablet and desktop              |

## Data model

- **User**: account that can own trees.
- **Family**: one tree, with a unique URL slug.
- **FamilyOwner**: links users to the families they can edit.
- **Member**: a person in a family (name, photo, dates, residence, bio).
- **Relationship**: parent–child and spouse links between members.

## Getting started

Requires Node.js 20 or later.

```bash
git clone git@github.com:inirmeet/family-trees.git
cd familyTree
npm install
npm run db:migrate   # create the SQLite database
npm run db:seed      # load one sample family
npm run dev          # http://localhost:3000
```

## Routes

| Route                  | Access | Purpose                         |
| ---------------------- | ------ | ------------------------------- |
| `/`                    | Public | Family list and search          |
| `/family/:slug`        | Public | Family tree view                |
| `/login`, `/register`  | Public | Account access                  |
| `/family/new`          | Owner  | Create a tree                   |
| `/family/:slug/edit`   | Owner  | Edit members and owners         |
| `/sitemap.xml`         | Public | Sitemap of all family pages     |

## Testing

```bash
npm test
```

Tests cover authentication, ownership rules and search.

## Code style

Simple and easy to read: short lines, small functions, no deeply nested
calls. All input is validated on the server.

## Licence

Not yet chosen.
