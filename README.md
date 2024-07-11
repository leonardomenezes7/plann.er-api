<h1 align="center">plann.er API📆</h1> 

![Thumbnail](https://github.com/leonardomenezes7/plann.er-api/assets/145611761/fa0ea5ea-c25a-48b8-8576-7ddbd9617e60)

#### A REST API that enables users to create trips with destinations and start and end dates, add participants by sending email invitations, and also include useful links and scheduled activities for the trip

### Status🟢: Development completed🚀

## Project design📁
![327563251-167db63d-fa8e-40ab-9634-36a460e5ea49](https://github.com/leonardomenezes7/plann.er-api/assets/145611761/b050117d-f2b7-4a96-b121-ff3114680668)

## Features⚙️
- Create a trip: Allows users to create a new trip.
- Update a trip by ID: Updates the details of an existing trip by its ID.
- List a trip: Allows users to view trip details.
- Invite trip participants: Allows the trip owner to invite new participants by email.
- Confirm trip participants on e-mail: Invited participants can accept the invitation via e-mail.
- List trip participants: Retrieves a list of all participants.
- List a participant: Allows users to view an participant details.
- Add trip links: Allows the trip owner to add links to the trip.
- List trip link: Retrieves a list of all links.
- Add trip activities: Allows the trip owner to add scheduled activities to the trip.
- List trip activities: Retrieves a list of all activities.

## Technologies used🛠️
- Node.js
- TypeScript
- prisma ORM
- sqlite
- git

## Database structure💾
![Captura de tela 2024-07-11 023846](https://github.com/leonardomenezes7/plann.er-api/assets/145611761/e65dabd9-7603-4229-aae9-e217532e9c4f)

### Business Rules:
#### trips:
- `id` - Unique identifier for each trip.
- `destination` - Final destination of the trip.
- `starts_at` - Date when the trip starts.
- `ends_at` - Date when the trip ends.
- `created_at` - Date when the trip was created on database.

#### participants:
- `id` - Unique identifier for each participant.
- `trip_id` - Identifier of which trip the participant is from (references `id` on table `trips`).
- `name` - Participant name.
- `email` - Participant e-mail.
- `is_confirmed` - Checks if the participant has confirmed their presence on the trip.
- `is_owner` - Checks if the participant is the owner of the trip.

#### links:
- `id` - Unique identifier for each link.
- `trip_id` - Identifier of which trip the link is from (references `id` on table `trips`).
- `title` - Link title.
- `url` - Link url.

#### activities:
- `id` - Unique identifier for each activity.
- `trip_id` - Identifier of which trip the activity is from (references `id` on table `trips`).
- `title` - Activity title.
- `occurs_at` - Date when the activity occurs.

## Routes🔃
- `POST /trips` - Create a trip in the database, sending `destination`, `starts_at`, `ends_at`, `owner_name`, `owner_email`, `emails_to_invite` fields through the request body.
When creating a trip, the fields `id`, `is_confimed = false`, `is_owner = true (on table participants)` and `created_at` will be automatically populated.
- `GET /trips/:tripId/confirm ` - Receives `tripId` as route parameter, confirms the trip and sends attendance confirmation emails to invited participants.
- `PUT /trips/:tripId` - Receives `tripId` as route parameter and updates the trip data by sending the fields `destination`, `starts_at`, `ends_at` through the request body.
- `GET /trips/:tripId` - Receives `tripId` as route parameter and displays data from the selected trip.
- `GET /trips/:tripId/participants` - Receives `tripId` as route parameter and shows a list of all registered participants for a trip.
- `POST /trips/:tripId/invites` - Receives `tripId` as route parameter and sends an invitation email to a new participant by sending the field `email` through the request body.
- `POST /trips/:tripId/activities` - Receives `tripId` as route parameter and creates a new scheduled activity for the trip  by sending the fields `title` and `occurs_at` through the request body.
- `GET /trips/:tripId/activities` - Receives `tripId` as route parameter and shows a list of all registered activities for a trip.
- `POST /trips/:tripId/links` - Receives `tripId` as route parameter and creates a link to the selected trip by sending the `title` and `url` fields in the request body.
- `GET /trips/:tripId/links` - Receives `tripId` as route parameter and shows a list of all registered links for a trip.
- `GET /participants/:participantId/confirm` - Receives `participantId` as route parameter and confirms the participant presence by changing the `is_confirmed` field in the participants table.
- `GET /participants/:participantId ` - Receives `participantId` as route parameter and shows a single participant of the trip.`

## How to run👨‍💻
```bash
# Clone the project to the desired location on your computer.
$ git clone https://github.com/leonardomenezes7/plann.er-api.git

# Navigate to the directory
$ cd plann.er-api

# Install necessary dependencies
$ npm install

# Create the database
$ npx prisma db push

# Create a .env file and enter the necessary environment variables

# Use postman link to use the client
https://www.postman.com/leonardomnz/workspace/nlw-journey

# boot the server
$ npm run dev

```
