# FHNWConnect
Part 1: Analysis
Scenario

FHNWConnect is a university event platform that helps students discover what is happening on campus. It brings together events from student clubs and sports teams in one place. Students can browse upcoming events, search and filter them, follow clubs and sport teams, and respond to events with statuses like “Going”. Clubs and sports teams can show events, post announcements, and check how many people have applied.
User Stories

    As a Student, I want to browse all campus events so that I can find interesting activities easily.
    As a Student, I want to search and filter events by category, date, club, and location so that I can quickly find relevant events.
    As a Student, I want to follow clubs and sports teams so that I get a more personalized feed.
    As a Student, I want to mark myself as Going so that I can keep track of events I care about.
    As a Club/Sports Team, I want to post announcements for events so that students can see our activities.
    As a Club/Sports Team, I want to post announcements so that I can inform students about tryouts, reminders, or schedule changes.
    As a Club/Sports Team, I want to view registration counts so that I can better plan my events.
    As a User, I want to access the application through a web browser so that I can use it easily on my device.

Use Cases

    UC-1 [Show all Events]: Students can view all available campus events.
    UC-2 [Show Event Details]: Students can open a specific event and see its full information.
    UC-3 [Search and Filter Events]: Students can search events and filter by category, date, club, or location.
    UC-4 [Follow Club]: Students can follow a club or sports team to personalize their feed.
    UC-5 [RSVP to Event]: Students can mark an event as Going or Interested.
    UC-6 [Manage Community Content]: User/Clubs and sports teams can create, edit, and delete community posts.
    UC-7 [Post Announcement]: Clubs and sports teams can publish announcements in the community section related to their activities.
    UC-8 [Verify Club]: Users receive notifications for clubs/sports/communities they follow.

Part 2: Design

The design of FHNWConnect focuses on a clean, modern, and user-friendly web interface suitable for a university environment. A color scheme based on yellow, white, and light gray ensures visual consistency and reflects a university-style identity. Typography is simple, clean, and highly readable to improve accessibility. The layout is optimized for desktop and laptop screens, while remaining responsive to different screen sizes. The interface supports: List view for browsing events efficiently. Calendar view for time-based event navigation.

The user experience is designed to allow students to discover events quickly with minimal interaction, supported by clear navigation and filtering options.
Wireframe

he wireframe of the home page defines the main structure of the web application. The interface is organized with a sidebar on the left, which serves as the primary navigation element. This sidebar includes sections such as Home, Clubs, Sports, and Community, allowing users to easily access the main areas of the platform. Below these navigation options, a calendar is displayed to provide an overview of activities. Under the calendar, additional sections such as Upcoming Activities, Favorite Clubs, and Favorite Sports are included to highlight personalized and relevant content for the user.

At the top of the page, a horizontal bar contains a search function for quickly finding events, as well as options for Help, Login, and Sign Up. The central area of the home page is used to present key content, such as featured events, announcements, or recommended activities.
Prototype

At this stage, the main goal is to test the layout, navigation, and user experience. The front-end does not need to be fully connected to the backend in the beginning. Important prototype screens would include the home page, event list, event detail page, club profile page, and community page.
Domain Design

The domain model of FHNWConnect can include the following main entities:

    User
    Club
    Activity (Event)
    Community_Post
    User_ Activity
    Favorite_ Club
    Favorite_Activity

Relationships: The relationships between the entities define how different parts of the system interact with each other. A User can participate in multiple Activities through the User_Activity entity, which stores information such as the RSVP status. In addition, a User can create multiple Community Posts and mark both Activities and Clubs as favorites. A Club can organize multiple Activities and can be followed by many users through the Favorite_Club relationship. Each Activity belongs to a single Club and can have multiple participating users. Community Posts are created by users and may optionally be associated with a Club. The User_Activity entity acts as a junction table between User and Activity, enabling a many-to-many relationship while also storing additional attributes related to user participation.
Business Logic

The business logic of FHNWConnect manages user interactions with events, clubs, and community features. The RSVP service allows users to respond to events, ensuring that each user has only one response per event by either creating a new RSVP or updating an existing one. The system also supports personalization by allowing users to mark clubs and activities as favorites, which are used to generate tailored content. Additionally, users can create and manage community posts, with permissions ensuring that only authorized users can modify or delete content. Clubs and sports teams can create and manage events and announcements, ensuring that all information is accurate and properly linked within the system.

Example API:

    Path: /api/events/{eventId}/rsvp
    Method: POST

Request Body Example:

{
  "studentId": 12,
  "status": "GOING"
}

Expected Logic:

    Check if the event exists
    Check if the user exists
    Check if the student already has an RSVP for that event
        If yes, update the status
        If no, create a new RSVP entry
    Return the updated RSVP count for the event
