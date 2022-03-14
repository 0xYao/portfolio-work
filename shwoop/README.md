In just over half a year, I rearchitected and built the entire app in React Native, GraphQL and NodeJS. I also helped scale it from 0 to thousands of users. As the CTO myself, I led a team of 3 junior engineers across all areas of development. I had to make critical technical architectural decisions, help the founder iterate on the product design and UX constantly and implement and deploy the whole solution. 

# My Shwoop GitHub Metrics

Note: the metrics are from Nov 2020 to June 2021 (7 months).

- **Total no. of commits**: 830

# Infrastructure

We built the frontend using React Native, [Formik](https://formik.org/), vanilla stylesheets and [React Query](https://react-query.tanstack.com/) and we made the backend using GraphQL, Prisma, PostgreSQL and [Nexus](https://github.com/graphql-nexus/nexus) (a code-first GraphQL development tool).

We use GitHub Action as our CICD pipeline, deploy the mobile apps using Fastlane and Microsoft CodePush for Over-The-Air updates, and deploy the backend using Docker, Amazon ECR, and Amazon ECS with auto-scaling group enabled.

# Tooling

## Admin Dashboard

The app is similar to a treasure hunt, and we have to create the challenges in the database manually ourselves. Initially, the founder created the challenges in a spreadsheet. He passed the spreadsheet to me, and I had to validate the data with the correct types and IDs before successfully uploading it to the relational database.

As you can see, uploading data is cumbersome because it requires an intermediate step, e.g. the developer needs to validate the data. So I built an admin dashboard from scratch using NextJS Ant Design UI to upload the data directly using the dashboard. The dashboard helped reduce the time it takes to roughly upload the data by 3x.

`/admin-dashboard/CreateChallengeForm.tsx`

![Create Shwoop Challenge](https://i.imgur.com/2HUEtpZ.png)

## Data Upload Script (for development)

Initially, during the development phase, you had to upload the data manually if you removed the data from the local DB or an empty DB. I created some scripts using Python and Pandas that read the data from JSON files, and I uploaded the data using the Apollo client. 

See `/data-services/graphql_formatter.py` and `/data-services/GraphQLUploader.ts` for more info.

# App Development

`/app/Map.tsx`: The map is built using `react-native-maps`. There are many types of markers on the map, e.g. a challenge is a treasure hunt, a user will be rewarded with a prize if they complete it. An event market represents a real-life event happening at that location, and other markers include in-app surveys and nearby users etc.

`/server/graphql/Mutations.ts`: The entry point of the GraphQL mutations.

`/server/graphql/Queries.ts`: The entry point of the GraphQL queries.

`/server/graphql/Schema.ts`: The code-first GraphQL schema constructed using Nexus.

`/server/App.ts`: The GraphQL express server with some custom API endpoints.

<img alt="How Shwoop Works" height="500" src="https://media.giphy.com/media/fONBvfHyr7uwEQ0vLC/giphy.gif" />
