# Frontend Assignment

 Getting Started

After cloning the project, run the following commands:

```bash
npm install
npm run dev
```

Then open your browser at:
```bash
http://localhost:3000
```
------------------------------------

## PART A: Code Reading & Debugging
1. Code Reading

Question A : What will be logged to the console, and why?

Answer: Will logged -> 1 0.

Question B : When will double be re-computed?

Answer: When calling `double`.

------------------------------------

2. Debugging

Question A : Does this code contain a bug?

Answer: Yes, it does.

Question A : If there is any bug, how would you fix it to make it safe?

Answer: Change props title like this
```
title: {
      type: String,
      required: true
    }
```
because from code example, title have probably to be undefiend.

-------------------------------------

## PART A: Coding & Algorithms

### Question 1

Path: `/part-b/a`

- Implement a groupBy function for used with `Items`

-------------------------------------

### Question 2

Path: `/part-b/b`

- Remove duplicate users
- Duplicate conditions:
  - Same email (case-insensitive)
  - Same full name and normalized phone number
- Implemented without using `Set`

-------------------------------------

### Question 3

Path: `/users`

- Use the Options API
- Declare mockData in `/users/index.vue`, then pass the data to `userList` component
- In the component, accepts users via props, displaying them as a Data Table. In the table, sort data ascending via age value.  Then create a toggle button above the table, whenever the user triggers it, sort data descending.

-------------------------------------

## PART C: SCSS & Styling

Path: `/`

- Single SCSS file
- No external CSS libraries
- Uses SCSS variables and mixins
- Includes:
  - Image carousel
  - Thumbnail navigation with prev / next buttons
  - Active and hover effects