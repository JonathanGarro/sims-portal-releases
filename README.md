# SIMS Portal Release Notes

## 1.0 - Shady Grove

### Features

#### User Profiles

- **Registration**: SIMS members can sign up using their Slack ID in the SIMS Slack account to verify. Once registered, they are placed into a queue for an administrator to approve. This helps triage who needs to be onboarded for the portal, and ensure only qualified members have full access. 
- **Support History**: Users can maintain a running record of the emergencies to which they have provided support.
- **Bio**: Users can share information about themselves in markdown format. 
- **Portfolio Highlights**: Users can post their finished products and supporting design assets to the Portal for each emergency they support, and have them appear on their profile.
- **Support Profiles**: SIMS Administrators can assign members one or more support profiles, which lets others know what types of products they can create and services they can provide. Each profile has an associated tier, with guidance around who qualifies for what tier.
- **Skills and Languages**: Users can tag the relevant technical skills they possess across a variety of areas, and tag the languages they speak in order to help others find the right person for specific questions.
- **Badges**: Achievement and recognition badges that are given to users appear on their profiles, along with the justification for getting it.
- **Location**: Users can take advantage of the Google Maps integration to search for a location where they work from, in order to help visualize our reach and organize our support across time zones.

#### Emergencies

- **Emergency Records**: Each SIMS activation gets its own emergency record, where our collective response is maintained. 
- **Activation Details**: Information can be entered about the emergency itself, as well as the process involved with activating SIMS to support it.
- **Trello Integration**: Each emergency can parse the tagged Trello board to extract open (unassigned) Trello tasks.
- **Learning**: Individual remote supporters and SIMS Remote Coordinators can provide feedback and learning for each response. Remote supporters are given the option of answering a brief survey at the end of their assignment, and Remote Coordinators can provide real-time feedback in a longer-form mechanism. 
- **Badge Assignment**: SIMS Remote Coordinators can assign remote supporters specific badges as they recognize stellar work.
- **Assignment Table and Gantt**: A table summarizes each remote supporter's involvement, and can be visualized with a D3-based Gantt chart.
- **Response Products**: As users post products, if they tag them as "Public", they get placed into a queue for the SIMS Remote Coordinator to review. If approved—meaning it is appropriate to share externally—it will appear for site visitors without having to log in. Products are uploaded by the Portal to Dropbox, where other members can access the underlying assets to reuse or remix them.
- **Response Tools Linkages**: The Portal connects with Slack, Dropbox, and Trello to ensure visitors can find the most important products, assets, and communication channels. 
- **Response Stories**: SIMS Remote Coordinators can draft markdown-friendly blog posts that summarize our response, document key learnings and achievements, and automatically synthesize our statistics. 

#### Assignments

- **Tagging to Emergencies**: Each remote supporter's involvement in an emergency is saved as an assignment (only one assignment is necessary even if the person works on multiple products with gaps in between). 
- **Basic Information**: Assignments store basic info about what the person was generally tasked with doing, when they started and ended their support (as estimates), and serves as the vehicle for saving products that the remote supporter created or supported on for that particular emergency.
- **Availability**: For larger-scale, high-volume emergencies, the availability feature can be utilized. Remote supporters can navigate to their assignment and report which days they are available to support. This can help with organizing coverage during intense periods of field requests.

#### Public Marketing

- **About Page**: The about page automatically updates with key metrics, including the full list of our activations, a count of active members, and a D3.js map that displays our response history.
- **Profile Types**: Dedicated pages are linked to from the about page that show the basics about each of our remote support profiles, as well as granular descriptions of how each tier (from 1 to 4) differ.
- **Public Portfolio**: Products that are requested to be public and approved by SIMS Remote Coordinators are visible in the portfolio, and filterable by type. 
- **Member Directory**: A full list of active members is available to site visitors, along with individual profiles for each member. These profiles closely match the profile one sees when logged in, but with only publicly-visible portfolio items visible.

#### Admin Controls

- **Profile Management**: Admins can assign one ore more support profiles to members.
- **Badge Assignment**: While SIMS Remote Coordinators will typically be the person assigning badges as part of a given response, admins can also assign badges. These include "Special Edition" badges that SIMS Remote Coordinators do not have access to.
- **Member Approvals**: When new users sign up, their accounts are tagged as conditional until an admin approves it.
- **Open Reviews**: A listing of all the SIMS Remote Coordinators' learning records. Admins can see the full list and approve or reject the information in order to process it into standard operating procedures or other change management tools. 
- **Skill Picklist Controls**: Admins can add to the list of skills we track on member profiles.
- **New Badge Uploads**: Admins can create new badges. When created, the badge automatically populates the badges index page and calculates how common it is among SIMS members.

#### Learning and Reference Resources

- **Organization by Support Profile**: The resources page organizes our knowledge management articles and guides by our primary support profiles. There are also hubs for standard operating procedures, style guides, and SIMS Portal documentation for admins.
- **learn-sims.org**: In order to make our guide-drafting process open and collaborative, the guides are hosted on a separate site running WordPress. Users can be added to that site and author their own guides and tutorials. 

#### Other

- **GO Surge Alerts**: The Portal runs a cron job that downloads the latest surge alerts from the GO API and summarizes them on the dashboard for logged-in members. New alerts trigger a Slack message that gets posted to the Availability channel on the SIMS account, along with basic information about the deployment request.
- **Data Overview**: A few basic visualizations are embedded in the dashboard, to support simple reporting on key metrics.

### Changes

- N/A

### Fixes

- N/A
