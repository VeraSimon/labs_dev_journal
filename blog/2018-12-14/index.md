---
date: '2018-12-14'
title: 'Developer Journal: Week 5'
category: 'Journal'
---

## Individual Accomplishments

[@VeraSimon](https://github.com/VeraSimon)

![Contribution Graph](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-12-14/contribution_graph.png 'Github Repository Contribution Graph')

<!-- Provide a paragraph (5-8 sentences) summarizing the work you did this week, the challenges you faced, the tools you used, and your accomplishments. -->

This week I did some finishing touches to the authentication and authorization flow, wrote a lot of documentation, and spent a lot of time helping my group members troubleshoot issues they ran into. The major piece of the auth flow that I completed was the sign out functionality. An API endpoint existed for revoking an access token, but it required that secrets be passed to it, which we can't store on the client side. With that in mind, I wrote up a wrapper for the existing API endpoint. Next, I implemented a web client component that sent the user access token to be revoked, then cleaned up the Redux state when it was done. Next, I spent a day-ish playing catch up getting documentation written. I wrote documentation for web stack manual testing, API endpoints, security practices, and media licensing for the resources used in the greater code base. In addition to everything else, I spent a substantial time assisting Eva, Caleb, Conner, and Samantha in getting things up and running. Eva needed help with styling and a toggleable menu. Caleb needed help with some weirdness with NavLinks and active route styling which he eventually solved with withRouter. And Conner and Samantha needed information on the various API endpoints and how to use them so they could connect the iOS app to the backend.

## Whiteboarding Session

- [Whiteboarding playlist](https://www.youtube.com/playlist?list=PLw5W0SfMYtxWUrDu0Y0jDRIiNv3et_TZz)

## Tasks Pulled

### Front End

- Hook Settings component into Redux state
  - https://trello.com/c/wSIfW5LS/226-update-settings-component-actions-and-reducers
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/135
- Facebook AppID bugfix
  - https://trello.com/c/Y8brihtH/238-fix-setting-facebook-appid-in-the-web-client
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/140
- Log Out component implementation
  - https://trello.com/c/YNQM1U8J/211-implement-logout-frontend-component
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/153
- Settings bugfixes
  - https://trello.com/c/mRX5aqaa/273-trying-to-update-the-user-settings-in-the-web-client-redirects-to-the-login-page
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/180

### Back End

- Access token revocation
  - https://trello.com/c/rIeAIlwH/241-facebook-oauth2-token-revocation-in-backend
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/160

### Miscellaneous

- Manual web stack testing doc
  - https://trello.com/c/cvKb3Mxf/265-document-manual-testing-procedure-for-web-front-end
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/wiki/Manually-Testing-The-Web-Stack
- API endpoint doc for use with web stack testing doc
  - https://trello.com/c/VHMkhtNS/266-document-manual-testing-procedure-for-back-end-api-endpoints
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/wiki/API-Endpoints
- Security practices doc
  - https://trello.com/c/4vm7UAaG/269-documentation-on-security
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/wiki/Security
- Media Licensing doc
  - https://trello.com/c/4sS5B2gO/272-document-usage-rights-for-media-images-used-for-ui-etc
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/wiki/Media-Licenses
- Update root README.md
  - https://trello.com/c/5Qv7LD9Q/278-update-readmemd
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/181

## Detailed Analysis

<!-- Pick one of your tickets and provide a detailed analysis of the work you did. This should be approximately 1/4 page of text, and at least three screenshots. -->

The ticket that I spent the most cycles on this week was the web client sign out component. Calling the revoke token endpoint was a bit tricky due to the nature of asynchronous calls and wanting to clear Redux state all in the same component flow. Calling revoke token, then clearing the user and article state all in a componentDidMount proved to be unsuccessful, so I had to consider other routes. I eventually settled on just toggling the signed in flag in componentDidMount, then doing the revoke token and Redux state cleanup on componentWillUnmount. Going this route ended up providing a pretty clean workflow in getting the Redux state back to initial.

![Sign Out modal](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-12-14/sign-out.png 'Sign Out modal')

![componentDidMount & componentWillUnmoount](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-12-14/unmount.png 'componentDidMount & componentWillUnmoount code')

![Sign Out code](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-12-14/signout-code.png 'Sign Out code')

## Completing The Project

<!-- As a part of your journal entry, write ¼ to ½ a page reflecting on your experiences working with a team to bring an application to completion. The 90-90 rule is a quip referencing the very real difficulty of truly completing a project. Describe some of the final tasks that were the most difficult for your team to resolve - challenging bugs, layout and presentation woes, or anything else that was easy to get mostly working, but hard to get perfect -->

During the final week of the main project, much of the group finally began to hit their groove in working with others and getting stuff done. The iOS folks came out of their shell, working with the FSW members, most of the FSW members worked with each other to tackle those pesky final problems that plague all software projects when they're coming up one completion, and overall it was a pleasant experience wrapping things up. As far as the 90-90 rule was concerned, we definitely hit a lot of things we scrambled to get done in that last 10% of the project, making it feel as if we had started a major component of it all over again. Work on the offline feature of the app saw Andrew working diligently trying to get it to a usable state. Caleb saw himself working out some subtle bugs with the article scraper backend. Eva and Caleb as a team spent some rather long evenings getting the styling both pleasant and consistant across the board. Samantha and Conner hit a road block when they found out at the last minute that they couldn't use stripe in an iOS app due to restrictions in Apple's licensing. And I spent a large amount of time helping all of them work through various bugs and such while also making sure our documentation was in working order for any future development that may arise.

## Weekly Milestones

<!--
For your project, provide in 350 words or less each:

The tech stack used to build the project
A description of the application Also provide:
A link in the readme to a document that provides links for the location for all media files (images, etc.) on the sight, and evidence of the license for that media.
-->

### Tech Stack

We had three main code bases for the overall tech stack. The web frontend was written using React & Redux with some other various helper libraries to implement various smaller functionality. The web backend, which we exposed as a REST API, was written using Django. Finally, the iOS app was written primarily in Swift, with some Objective C thrown in for some libraries.

### Application Description

Anywhere Reader aims to be an application for iOS and the web that allows the user to grab articles and media from their favorite sources and display them in a clean, uncluttered interface. It also allows them to save these articles and media for offline viewing.

### [Media Licenses](https://github.com/Lambda-School-Labs/Labs8-OfflineReader/wiki/Media-Licenses)
