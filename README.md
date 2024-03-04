# Technical test

## Introduction

Fabien just came back from a meeting with an incubator and told them we have a platform “up and running” to monitor people's activities and control the budget for their startups !

All others developers are busy and we need you to deliver the app for tomorrow.
Some bugs are left and we need you to fix those. Don't spend to much time on it.

We need you to follow these steps to understand the app and to fix the bug :
- Sign up to the app
- Create at least 2 others users on people page ( not with signup )
- Edit these profiles and add aditional information
- Create a project
- Input some information about the project
- Input some activities to track your work in the good project

Then, see what happens in the app and fix the bug you found doing that.

## Then
Time to be creative, and efficient. Do what you think would be the best for your product under a short period.

### The goal is to fix at least 3 bugs and implement 1 quick win feature than could help us sell the platform

## Setup api

- cd api
- Run `npm i`
- Run `npm run dev`

## Setup app

- cd app
- Run `npm i`
- Run `npm run dev`

## Finally

Send us the project and answer to those simple questions : 
- What bugs did you find ? How did you solve these and why ? 
- Which feature did you develop and why ? 
- Do you have any feedback about the code / architecture of the project and what was the difficulty you encountered while doing it ? 

## Changelog

People update
- Name not showing in profile update page => user name attr mapping was not set properly on user creation (username instead of user)
- Input binding issue
- Update button not working => changed onChange to onClick on update button

People creation
- Email validation missing => requires a validation/field sanitizer
- User name bound to username instead of name

Activities
- null value prop on select => init field with empty string and use empty string as default option

Project page
- project.name = undefined => this bug was fixed by updating the api endpoint project/:id to throw 1 project instead of an array

API
- GET : project/id endpoint throwing array instead of 1 project
- Add user delete endpoint to delete a list of users

Miscellaneous
- Better highlight of nav menu elements - highlight sub pages (project and project/123 should highlight nav menu project)
- Disable user deletion for self - for security
- Add eslint command - code quality

Quick win
- Implement drawer toggler - because its onclick trigger was broken
- Restore user name update - enable user name field in user update page, to fix the previously broken mapping username => user
- People batch deletion - add bulk action to users list page (deletion) to simplify redundant actions


Code/Architecture feedback
- Api should have a better error handling mechanic, 5xx errors to be avoided
- Sanitize raw user input before nosql commands to prevent injections
- Avoid using async/await pattern where not necessary in order not to block the execution of other instructions
- Use eslint to avoid code smell (dead code, code duplication etc)
- Use a proper oauth2 with shorter refreshable access tokens 
