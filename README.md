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
