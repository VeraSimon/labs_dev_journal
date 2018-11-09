---
date: '2018-11-09'
title: 'Developer Journal: Week 1'
category: 'Journal'
---

## Individual Accomplishments

[@VeraSimon](https://github.com/VeraSimon)

![alt text](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-09/contribution_graph.png 'Github Repo Contribution Graph')

My week was full of a lot of initial initialization and engineering tasks, though I didn't get to code as much as I might have liked. Still, the tasks I accomplished, such as standardizing the dev environment database with a PostgreSQL Docker container, and getting a bunch of the finer details on the git repo taken care of, such as global and codebase specific .gitignore's and a pull template to streamline the pull process for the developers, make all the difference between a team that flounders and a team that's set up to accomplish a task. I was also able to get the frontend deployed to Netlify, along with continuous deployment set up and running successfully. In addition, I was able to accomplish a manual deploy of the Django backend and connect it up to PostgreSQL, ensuring we had a good starting point. Setting up continuous deployment for the backend is ongoing.

## Tasks Pulled

### Monday 11/5:

- Initializing the Github repository
  - https://trello.com/c/hwEgp1JS/7-initialize-your-project
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/2

### Tuesday 11/6:

- Getting a standardized PostgreSQL install set up for all the FSW developers
  - https://trello.com/c/D47AjeHV/19-initialize-postgres-database
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/8
- Set up specific .gitignore files for each of the three code bases
  - https://trello.com/c/TqM006gG/34-global-gitignore-for-tool-settings
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/10

### Wednesday 11/7:

- Wiki documentation stubs to get development environments set up for each of the three code bases
  - https://trello.com/c/OeSKz0iY/38-create-documentation-stubs-for-each-of-the-three-code-bases-for-environment-setup
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/13
- Github pull request template
  - https://trello.com/c/pvM0DeiB/41-github-pull-request-template
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/15
- Set up a Base .gitignore file to ignore tool-specific configuration data put into the working directory
  - https://trello.com/c/WgYhQG79/48-add-os-specific-content-to-base-gitignore
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/21

### Thursday 11/8:

- Deploy the React frontend to Netlify
  - https://trello.com/c/t3OWPK6O/50-deploy-frontend-to-netlify
  - https://trello.com/c/oW9FtsXC/12-deployed-to-the-web
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/25
- Deploy the Django backend to Heroku
  - https://trello.com/c/u35yvOlR/51-deploy-backend-to-heroku
  - https://trello.com/c/oW9FtsXC/12-deployed-to-the-web
- README.md update to reflect current wiki content
  - https://trello.com/c/5XJ0wlYK/13-readme
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/27

## Front End

- Getting a standardized PostgreSQL install set up for all the FSW developers
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/8
  - https://trello.com/c/D47AjeHV/19-initialize-postgres-database
- Deploy the React frontend to Netlify
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/25
  - https://trello.com/c/t3OWPK6O/50-deploy-frontend-to-netlify
  - https://trello.com/c/oW9FtsXC/12-deployed-to-the-web

## Back End

- Getting a standardized PostgreSQL install set up for all the FSW developers
  - https://trello.com/c/D47AjeHV/19-initialize-postgres-database
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/8
- Deploy the Django backend to Heroku
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/issues/24
  - https://trello.com/c/u35yvOlR/51-deploy-backend-to-heroku
  - https://trello.com/c/oW9FtsXC/12-deployed-to-the-web

## Detailed Analysis

The front and back end deployments were an interesting experience. The frontend specifically did not prove much of a challenge via Netlify, as I had previous experience using it with a repo that had the project in a subdirectory, but the backend deployment proved to be vexing. This is the FSW teams first foray into using Django at all, so there were a lot of initial growing pains in that arena especially, but then subsequently getting the app deployed from a subdirectory and connected to the postgres database was difficult. After a long FSW Zoom session, we _were_ able to eventually get it deployed and connected though, with much celebration throughout.

![alt text](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-09/django_admin.png 'Django Admin Panel')

## Experience forming a team

As a part of your journal entry, write ¼ to ½ a page reflecting on your experiences forming a team. What did you do to help the team solidify as a group? What did you do that you now realize caused friction in this process?

I've actually built and supervised teams in previous positions, so I was able to help avoid a lot of the initial growing pains as our group formed and started to get rolling. I made sure throughout the week that the small touches on the code base were in place, such as proper .gitignore files and a pull template, and also went out of my way to get some standardized tooling in place on the developer side of the house, specifically including a standardized PostgreSQL Docker container using the same version that Heroku uses in production. This made ramping up the backend side of the code base a lot smoother than it could have been, with a bunch of developers using different infrastructure with major and minor changes that could make or break a code base. As far as growing pains are concerned, getting all of the developers to use a specific branching strategy without being able to explicitly enforce it via Github is proving difficult, and our coding style standards are still a bit looser than I would like. Overall though, I believe we're all off to a pretty solid start, and I hope the experience of working with this group continues to be as pleasant as week one.

## Weekly Milestones

- [Frontend](https://anywhere-reader-test.netlify.com/)
- [Backend](https://anywhere-reader-test.herokuapp.com)

![alt text](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-09/django_admin.png 'Django Admin Panel')
