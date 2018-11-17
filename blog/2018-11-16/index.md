---
date: '2018-11-16'
title: 'Developer Journal: Week 2'
category: 'Journal'
---

## Individual Accomplishments

[@VeraSimon](https://github.com/VeraSimon)

![Contribution Graph](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-16/contribution_graph.png 'Github Repository Contribution Graph')

<!-- Provide a paragraph (5-8 sentences) summarizing the work you did this week, the challenges you faced, the tools you used, and your accomplishments. -->

This week saw the team trying to tie up integrating the frontend, backend, and APIs to get a base to go forward with. In particular, I made sure to get the continuous deployment for the backend up and running successfully, and also worked with Eva on getting Stripe integration going in the frontend and backend. We were successful in getting the frontend working, but are currently troubleshooting an issue regarding the backend replying to the frontend with the charge status related to CORS/CORB.

## Tasks Pulled

### Front End

- Stripe frontend integration
  - https://trello.com/c/zseKxoGT/90-stipe-frontend
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/54

### Back End

- Bug: urls.py config typos
  - https://trello.com/c/RiyoyRZL/64-blocking-url-parameter-in-urlspy-is-preventing-dev-server-from-launching
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/35
- Universal database configuration for backend
  - https://trello.com/c/0rOFzsry/59-wire-up-django-to-work-with-both-local-and-prod-databases
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/38
- Setting up continuous deployment for backend
  - https://trello.com/c/gda7yGAW/60-continuous-deployment
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/issues/24
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/52
- Set up static files for Django
  - https://trello.com/c/9lk4uJfZ/94-django-static-files
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/52

### Miscellaneous

- Updated frontend and backend URLs to be more recognizable
  - https://trello.com/c/edHFhqcp/62-update-fsw-frontend-and-backend-urls-to-be-recognizable
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/33
- Completely rewrote 'Environment Setup: Django & Python' wiki article
  - https://trello.com/c/GezWRy5n/91-update-environment-setup-django-python-wiki-article-to-flesh-out-pipenv-use-and-other-missing-bits
- Passing wrong params to git push during backend deploy
  - https://trello.com/c/uRP6WaDU/81-heroku-throwing-error-during-manual-deploy

## Detailed Analysis

<!-- Pick one of your tickets and provide a detailed analysis of the work you did. This should be approximately 1/4 page of text, and at least three screenshots. -->

Setting up continuous deployment for the Django backend on Heroku posed many challenges specifically related to the platform itself. To start, Heroku does not officially support deploying from a subfolder in a git repository, so I needed to surmount that hurdle before any progress forward could be made. Taking a note from a suggestion of a fellow member of the cohort, I ended up using the 'subdir-heroku-buildpack' third-party buildpack, which, when a git push is triggered to Heroku, copies the specified subdirectory to a temp directory, deletes everything else from the root of the pushed git branch, then copies the specified directory back to the project root before passing things back off to the official 'Heroku/Python' buildpack for further deployment processing. After a bit of stumbling with the subdir buildpack not recognizing I had set the needed environment variable for the subfolder to process, things went off pretty smoothly for it.

The next issue I ran into though was a misunderstanding on my part on how to call git push when specifying a specific remote and branch. I mistakenly thought that the branch name was for the remote branch I was trying to push to, but it turns out that it was the local branch that it was expecting, causing me no end of headaches when one of the Heroku pre-commit hooks kept throwing an error related to the Django static files configuration. Eventually, one of my fellow group members saw what I was doing wrong, and informed me of my mistake.

With a little egg on face, I continued forward with the deploy to discover that the Django/Whitenoise static file configurations I had set worked as expected from the get-go. From here, I was able to confirm that a manual push of the code worked successfully, and was able to subsequently turn on continuous deployment for the repo and did the initial push through the Heroku web interface to confirm that it could successfully pull and deploy in an automated manner!

![Successfully deployed!](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-16/dep_success.png 'Deploy success!')

---

![The continuous deployment configuration](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-16/dep_config.png 'Deploy configuration')

---

![Deployed site](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-16/dep_site.png 'Deployed site')

## Integration

<!-- As a part of your journal entry, write 1/4 to 1/2 a page reflecting on your experiences working with a team to integrate several servers, pages, APIs, and services into one project. Describe how your pieces of the project interfaced with and integrated with your teammates. -->

This week has been a rough one on a couple of fronts. To start, due to Veterans Day (observed), we were short a day for the week, but still had a full-week MVP course load. In addition to that, working in a remote team of developers is particularly difficult while trying to get everything integrated due to the fact that everyone is trying to get their particular splinter of the project done, but seeing as we're all junior developers at this point, gauging how big of a bite to take out of the project at a time can be difficult, though I think the entire team understands that it's a practiced skill that we'll get better at as time and effort is expended.

As far as the specific integration bits, I spent a decent portion of the week helping one of my team members with the integration of the stripe API into our project, each alternating on working with the frontend and backend portions of it to get things working. The backend portion of strip has proved particularly challenging, especially in regard to things relating to CORS and CORB, as we were both still getting used to working with the 'django-cors-headers' Python library. As it stands, we have a toy frontend and backend that work seemlessly with stripe, and our integration of the frontend changes into the codebase appear to work as expected, but the integration of code into the backend is hitting some CORS/CORB issues that we've yet to iron out. Otherwise the payment chain works successfully all the way until the backend tries to send the success/failure message back to the frontend.

## Whiteboarding session

<!-- Add a link to the weeks whiteboarding session -->

- [Rock, Paper, Scissors](https://www.youtube.com/watch?v=QOb4PD3loHw)

## Weekly Milestones

<!-- As a group, provide links to evidence that:
Front and back end servers are connected
Users can create accounts and log in through the front end via OAuth
All APIs and services are connected and can be interacted with through the front end. A test message is acceptable to meet this requirement
 -->

### Users can create accounts and log in through the front end via OAuth

![Facebook auth](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-16/facebook-pop-up.jpg 'Facebook auth')

---

![Facebook auth](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-16/facebook-console-log.jpg 'Facebook auth')

---

![Google auth](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-16/google-auth.png 'Google auth')

---

![Google auth code](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-16/google-auth-code.png 'Google auth code')

### All APIs and services are connected and can be interacted with through the front end

![Stripe frontend shenanigans](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-16/frontend-stripe-cors-corb.png 'Stripe frontend shenanigans')

---

![Stripe backend doing its thing](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-16/backend-stripe-response.png 'Stripe backend doing its thing')
