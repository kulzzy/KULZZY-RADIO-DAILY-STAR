KULZZY RADIO DAILY STAR — PLAIN WEBSITE + ADMIN

FILES
- index.html: plain public page, displays only published competitions.
- admin.html: admin creator/editor for competition details and feature switches.
- config.js: shared API base URL and competitions endpoint.

IMPORTANT BACKEND REQUIREMENT
The front-end calls these REST API routes:
GET    /api/competitions                  list competitions
POST   /api/competitions                  create competition
GET    /api/competitions/:id              (optional, not currently required by UI)
PUT    /api/competitions/:id              update a competition
PATCH  /api/competitions/:id              publish/unpublish status
DELETE /api/competitions/:id              delete a competition

Admin requests use:
Authorization: Bearer <admin API token>

GET should return either a JSON array or an object containing "competitions", "items", or "data".
Each record should include id (or _id), name, status or published, and optional fields:
type, description, coverImage, startDate, endDate, resultDate, rules, prizes,
entryFee, votePrice, maxEntries, winnerCount, features, notes.

A record is public when status="published" or published=true.
CORS must allow the GitHub Pages domain and GET/POST/PUT/PATCH/DELETE plus Authorization and Content-Type headers.

HONEST LIMITATION
These files connect to the expected REST API contract, but the existing Kulzzy Backend Core's actual routes, auth method, and database schema have not been confirmed from available information. If those routes do not exist, the site will show an API error until the backend is configured to support this contract or config.js/admin request code is adapted to its actual API. The site cannot create backend endpoints by itself.
For real contest registrations, contestant photo/song/video uploads, voting, and verified payments, backend storage/routes and payment-provider verification must also be implemented. The feature switches here store the competition's configuration; they do not magically create those separate workflows.

DEPLOY
Upload all three files into the root of the KULZZY-RADIO-DAILY-STAR GitHub repository, commit changes, then enable GitHub Pages from the main branch/root.
Open index.html for the public page. Open admin.html for the admin panel.
