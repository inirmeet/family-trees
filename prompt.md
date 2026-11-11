Build a web app for storing and displaying family trees.

## Pages

1. Family List (public, no login)
   - Lists all families whose trees are stored.
   - Search by family name or by member name.
   - Clicking a family opens its Family View.

2. Family View (public, no login)
   - Shows the family as a tree, one node per member.
   - Each node shows the member's photo and name (use a placeholder
     avatar when there is no photo).
   - Clicking a node opens a detail panel with: date of birth, date of
     death (if applicable), place of residence, and a free-text bio.
   - The tree supports pan and zoom, and stays usable for large families.
   - SEO friendly, so the page can be indexed and listed by search
     engines:
     - Readable URL built from the family name, e.g.
       /family/sanghani-family (unique slug, no numeric IDs or query
       strings).
     - Server-side rendered, so the family name and member names are in
       the HTML that crawlers receive.
     - Unique title and meta description per family, a canonical URL,
       and Open Graph tags for link previews.
     - Included in an auto-generated sitemap.xml, with a robots.txt
       that allows crawling.

3. Create & Edit Tree (login required)
   - A logged-in user can create a tree; each tree represents one family.
   - A tree can have multiple owners. Any owner can add, edit and remove
     members, and can add other registered users as owners.
   - Only owners can edit a tree; everyone else has read-only access.
   - Member form: name, photo upload, date of birth, date of death,
     place of residence, bio, and relationships (parents and spouse).

## Accounts
- Register and log in with email and password.
- Passwords are hashed; sessions use secure cookies.

## Data model
- User, Family (with a unique slug), FamilyOwner (user–family link),
  Member, and relationships between members (parent–child and spouse).
- A member can have two parents and more than one spouse over time.

## Tech stack
- JavaScript on both sides: Nuxt 3 (Vue 3) for the front end and the
  server API, with server-side rendering for the public pages.
- SQLite database, with migrations and a seed script that creates one
  sample family.
- Responsive layout that works on phone, tablet and desktop.

## Code style
- Keep the code simple and easy to read: short lines, small functions,
  no deeply nested calls.
- Validate all input on the server.

## Deliverables
- Working app with a README covering setup, run and seed commands.
- Tests for the API: auth, ownership rules and search.

Before writing code, show me the proposed data schema and page routes,
and ask about anything that is unclear.
