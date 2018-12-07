---
date: '2018-12-07'
title: 'Developer Journal: Week 4'
category: 'Journal'
---

## Individual Accomplishments

[@VeraSimon](https://github.com/VeraSimon)

![Contribution Graph](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/DATE_HERE/contribution_graph.png 'Github Repository Contribution Graph')

<!-- Provide a paragraph (5-8 sentences) summarizing the work you did this week, the challenges you faced, the tools you used, and your accomplishments. -->

This week was loaded with a lot of helping my other team members with various coding and troubleshooting. Monday saw me working collaboratively with Caleb to put the finishing touches on the OAuth2 flow between front end and backend, with me using react-facebook-sdk for React on the front end, and Caleb using django-rest-framework-social-oauth2 on the backend, opening up the possibility to use more OAuth2 providers in the future. Tuesday I was able to create and integrate an auth higher-order component into the frontend to utilize the OAuth2 flow to gate the apps main features behind a login prompt. This also saw me separating some styling out into separate components for use in various places, as I was in the specific code doing refactoring for the AuthHOC already. Wednesday and Thursday saw me primarily helping sort out issues with database schema design with Eva and Caleb, and getting some more styling on the Settings page done in between things. Thursday was spent almost entirely troubleshooting the code that resulted from the schema design from Wednesday. Out of this and some missed documentation, I did some quick digging Thursday afternoon and found that Django has a built-in module for auto-documentation, so I enabled that and submitted a pull request to master.

## Tasks Pulled

### Front End

- Article modal
  - https://trello.com/c/Bs0yYFDX/182-create-page-modal-to-show-contents-of-a-given-page-in-the-frontend
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/97
- Facebook OAuth2 integration
  - https://trello.com/c/4Bvy58XE/194-fb-oauth2-frontend-work
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/106
- Auth higher-order component
  - https://trello.com/c/VYim0FTl/197-hoc-component-to-gate-content-via-login
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/113
- Auth higher-order component integration
  - https://trello.com/c/zl7RBhs8/200-separate-the-landing-page-styling-out-into-its-own-styled-component-piece-for-use-on-the-landing-page-login-page-etc
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/115
- Article modal styling
  - https://trello.com/c/pXqzwR4c/207-style-article-modal
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/119

### Back End

- Django code self-documenting code
  - https://trello.com/c/6daHz70T/223-self-documenting-django
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/130

## Detailed Analysis

<!-- Pick one of your tickets and provide a detailed analysis of the work you did. This should be approximately 1/4 page of text, and at least three screenshots. -->

Integrating OAuth2 into our project has so far been the biggest hurdle amongst all of the features that we needed to implement into the project overall. On Monday, I worked with Caleb to ensure that we finished integrating an end-to-end workflow for Facebook OAuth2 authentication up and working. Up to that point, myself, Caleb, and Andrew had made around a dozen attempts to integrate an OAuth2 workflow from various providers to no success, stemming primarily from the fact that we're using different languages/frameworks for our web frontend and backend. This made finding examples especially difficult, as the extreme majority of them out there are based on a single language/framework stack, not taking into account multiple clients. With that, on Monday while I was trying to get yet another backend auth library to work with Google OAuth2, Caleb, in a separate branch, was able to get django-rest-framework-social-oauth2 at least partially working with the Facebook sub-module for it. Based on his backend work, I jumped in and started writing the front end code needed to interact with the new back end API endpoint, and got things successfully working over the course of a couple hours.

![Front end login prompt](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-12-07/login-prompt.png 'Login prompt')

![Front end login code](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-12-07/login-code-frontend.png 'Front end code')

![Back end login code](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-12-07/login-code-frontend.png 'Back end code')

## Polishing The Application For Prime-time

<!-- As a part of your journal entry, write ¼ to ½ a page reflecting on your experiences working with a team to make your product look and feel as good as it works under the hood. Describe how the duties of you and your team shifted tasks shifted towards the front end - and debugging the back end to improve UX. -->

My experiencing polishing up the web side of the application this week went pretty decently. I refactored some CSS bits that were causing inheritence issues, implemented some CSS global resets via styled components, styled out article modal, did some initial styling on the settings page, and tweaked some other styling throughout the front end web app to account for the features that are implemented at this time. As far as improving the polish on the backend, due to some recent restructuring of the API endpoints, documentation fell behind a bit, so I took the opportunity to enable the auto documentation generation in Django so that we would always have an up to date reference to check what's going on under the hood.

## Whiteboarding Session

- [Whiteboarding playlist](https://www.youtube.com/playlist?list=PLw5W0SfMYtxWUrDu0Y0jDRIiNv3et_TZz)

<!-- Add a link to the weeks whiteboarding session -->

- [Set Of Stacks](https://youtu.be/avTwnLWGaOU)

## Weekly Milestones

<!-- insert stuff here -->

- [Landing Page](https://anywhere-reader-test.netlify.com/)

  - Looks good overall. Could stand to use a vector-based background image which scales to the viewport, but otherwise functions as expected.

- [Log In Page](https://anywhere-reader-test.netlify.com/signin)

  - Work on styling pending upload after an auth bug is squashed. The login prompt is a bit minimal right now, but has pleasant graphics that mesh pretty well with the Landing/Login background.

- [Articles Form/List Page](https://anywhere-reader-test.netlify.com/articles)

  - Looks great, if currently a bit minimal! Could stand to fill in some of the white space maybe?

- [Subscription Page](https://anywhere-reader-test.netlify.com/payment)

  - Currently minimally styled. There's lots of white space here that needs to be used up.

- [Settings Page](https://anywhere-reader-test.netlify.com/settings)

  - Currently minimally styled. There's lots of white space here that needs to be used up. Some refactoring of the component to use values from Redux state is pending auth bugfix.
