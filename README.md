# PPAI---Full-Stack-Project
# PPAI Member Directory

A simple full-stack app where you can search and browse PPAI members. The backend is a Spring Boot API that holds member data in memory, and the frontend is an Angular app that talks to it.

## What you need installed

- Java 8 or higher (JDK, not just JRE)
- Maven 3.6+
- Node.js 14+
- npm
- Angular CLI 14 (install with `npm install -g @angular/cli@14`)

## How to run

You need two terminals, one for backend and one for frontend.

**Terminal 1 - start the backend:**

```
cd member-directory-api
mvn clean package
mvn spring-boot:run
```

This starts the API on http://localhost:8080. Wait until you see "Started MemberDirectoryApplication" in the console before moving on.

**Terminal 2 - start the frontend:**

```
cd member-directory-ui
npm install
ng serve
```

This starts the UI on http://localhost:4200. Open that in your browser.

The backend has to be running first otherwise the frontend will show an error when it tries to load members.

## How it works

The backend has 12 sample members hardcoded in memory. No database, nothing fancy. When you restart the server everything resets.

The frontend has two pages. The home page shows all members as cards and lets you search, filter by year, and sort by name/company/year. Click on any member card and it takes you to their detail page.

The search is case-insensitive and matches partial text against first name, last name, and company.

## API endpoints

- `GET /api/members` - returns all members
- `GET /api/members/search?query=alice` - search by name or company
- `GET /api/members/3` - get one member by id (returns 404 if not found)

## Tech used

Backend - Java 8, Spring Boot 2.7, Maven. Just the spring-boot-starter-web dependency, nothing else.

Frontend - Angular 14, plain JavaScript (no TypeScript types used). Font Awesome for icons and Google Fonts (Inter) for the font, both loaded from CDN. No Bootstrap or any other CSS framework, all the styling is handwritten.

## Assumptions I made

- No database needed, the data is just a hardcoded list in Java
- memberSince is stored as a plain year number (like 2015) not a full date
- Search only matches against name and company, not email
- CORS is enabled on the backend so the frontend can call it from a different port
- No login or authentication since it wasnt in the requirements
- The app is read-only, no creating or editing members

## What requirements are covered

**Part 1 - Backend**
- All three endpoints work (get all, search, get by id)
- Member has all the required fields (id, firstName, lastName, company, email, memberSince)
- Data is in-memory, no database
- 12 sample members included
- Search is case-insensitive and matches partial strings
- Returns JSON

**Part 2 - Frontend**
- Has a search box
- Results shown as clean cards
- Click a member to see full details
- Responsive, works on mobile and desktop
- Built with HTML, CSS, and JavaScript (Angular framework)
- Clean design with custom CSS

**Part 3 - Integration & Docs**
- Frontend connects to backend API
- This README covers how to run it, tech choices, assumptions, and libraries

**Bonus points covered**
- Loading state - spinner shows while data is loading
- Filtering - dropdown to filter by membership year
- Sorting - sort by name, company, or year, click again to reverse

