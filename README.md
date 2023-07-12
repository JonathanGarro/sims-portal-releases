![DC Metro Map Isolated](https://github.com/JonathanGarro/sims-portal-releases/assets/8890661/88a441fe-47b6-4874-90e6-83d3a64f0341)

- Patch (0.0.X) releases are minor bug fixes and code enhancements. 
- Minor (0.X.0) and major (X.0.0) releases introduce new features and follow the Washington DC Metro system's station names on the Red Line, starting at Shady Grove.

# 1.2.4 (Twinbrook) - 2023-07-12

## Changes

- **Assignment Quick Access**: The quick access button released with **1.2.3** has been updated with improved visual styling.
- **Better Date Formatting**: Dates on the dashboard and emergency page now use an easier-to-read format of month day, year (e.g. "July 12, 2023")

# 1.2.3 (Twinbrook) - 2023-07-10

## New Features

### User Profiles

- **Delete Skills**: Users can now delete skills they've assigned themselves from their profile edit page. 

### Emergencies

- **Assignment Quick Access**: When viewing an emergency for which the user has an active remote support assignment, an alert box in the left pane appears, offering quick access to the assignment record.

### Changes

- **Paginated Member Cards**: To reduce load times on members page on public view, the cards are now be limited to four rows with 'next' and 'previous' buttons conditionally appearing at the bottom.

## Fixes

- **Logging Issues Related to Alembic**: After implementing `flask-migrate` to handle database model changes, it broke logging to our Logtail instance. This was related to an [identified issue](https://github.com/miguelgrinberg/Flask-Migrate/issues/227) in `flask_migrate.upgrade()` during initialization.

# 1.2.2 (Twinbrook) - 2023-07-05

## New Features

### Availability

- **Better Data Management and Visualization**: Building off the availability reporting feature introduced in 1.2.0, users can now more easily make changes to their previous reports. Past reports are overwritten rather than appended. The availability tab on the emergency page now summarizes the data for the week in a bar chart.

## Changes

- **Separated Support Tables**: The emergency page now splits up supporters into three distinct tables: Remote Coordinators, Remote Supporters, and deployed IM delegates, the latter being a collapsed table that can be expanded.
- **PEP-8 Compliant Imports**: As part of a larger effort to clean up the codebase, the imports on various routes have been reorganized to make them easier to read.

## Fixes

- **DataTable Error in Admin View**: Fixed an error thrown by a conflicting javascript function when viewing the assigned profiles table.

# 1.2.1 (Twinbrook) - 2023-07-01

## Changes

- **Verify Slack ID on Approval**: In order to validate that users are not spoofing the registration process, a link to their Slack DM has been added to the new user approval route for Admins that asks them to check the Slack ID with a quick link.

## Fixes

- **D3.js Map**: Fix the timing on the map markers so they stay on until the horizon and reappear correctly.
- **Broken Slack DM Link**: The URL pattern for direct linking to a user's Slack DM was previously not properly configured.

# 1.2.0 (Twinbrook) - 2023-06-30

## New Features

### Availability

- **Weekly Availability**: Users can now report their availability for providing remote support to operations. When users open the emergency's page, there is an option to provide their availability for the current week. As the next week approaches (starting Thursdays), they can also report for the upcoming week. A calendar provides a visual summary of the days they have selected. 
- **Cron Job Trigger**: A function has been added that runs on Monday morning which loops over active emergencies and sends a Slack message to the relevant disaster channel with a direct link to the reporting form. This is currently toggled off, pending socialization with the SIMS network.

## Changes

- **Slack API Caching**: Added caching to the Slack API calls that get the list of users and IDs. There is a rate limit of one call per minute, which caused an error if multiple people were registering at once. The cache now stores the results for two minutes to avoid the limit.
- **Hide Map on Landing Page**: Users reported that some mobile phones would freeze when viewing the index page as a result of the D3.js animation. This element is now hidden when viewing the site on smaller screens.
- **Emergency Page Navigation**: The layout and available actions on emergency pages have been redesigned. Only administrators can assign the first SIMS Remote Coordinator (subsequent rounds can be assigned by either administrators or existing/previous SIMS Remote Coordinators). Regular users cannot assign themselves to emergencies any more—Coordinators must do this.

# 1.1.1 (Rockville) - 2023-06-15

## Changes

- **Navbar Font Sizing**: The title and nav menu links have been shrunk to ensure text doesn't get cutoff on mobile devices.

## Fixes

- **Forgot Password Error**: A bug that would give the user an error message when using the "Forgot Password" feature, which was related to a logging issue, has been fixed.

# 1.1.0 (Rockville) - 2023-06-03

## New Features

### Portfolios

- **KM Link**: Added linkage for portfolio view back to the relevant tutorial or guide in learn-sims.org. When `km_article_id` is not null, a button will appear that links to the guide. Updating this field must be done in the admin area by editing the product's information in the "Portfolio" tab.

## Fixes

- **Member Count**: Emergency pages now count each person only once, whereas it used to count each assignment (meaning if someone served as a remote coordinator then as a remote supporter, they were getting double counted).
- **Root URL**: With migration from CloudFront staging domain to rcrcsims.org, update the `ROOT_URL` in the `config.py` file to support external links.

# 1.0.3 (Shady Grove) - 2023-05-29

## Fixes

- **New Assignment Form**: Removed "FACT/CAP" from assignment type.
- **Limited Edition Image Path**: Fix for limited edition paths stored in S3.

# 1.0.2 (Shady Grove) - 2023-05-25

## Changes

- **All Emergencies Search Removed**: Remove broken link to old custom search page.
- **Manual Refresh of User Locations**: Temporary stopgap solution to allow administrators to regenerate the CSV that feeds the landing page's red dots that represent the locations of SIMS members around the world.

# 1.0.1 (Shady Grove) - 2023-05-23

## New Features

### Other

- **Release Tracker on GitHub**: A new page for tracking release features. We'll be following the Red Line stations from the Washington, DC Metro system for major new releases.

## Changes

- **Release Tracker Link**: The new release tracker has been added to the `layout.html` file.
- **Footer Redesign**: A new layout was added to include additional links and remove generic SIMS blurb.

# 1.0 (Shady Grove) - 2023-05-20

## New Features

### User Profiles

- **Registration**: SIMS members can sign up using their Slack ID in the SIMS Slack account to verify. Once registered, they are placed into a queue for an administrator to approve. This helps triage who needs to be onboarded for the portal, and ensure only qualified members have full access. 
- **Support History**: Users can maintain a running record of the emergencies to which they have provided support.
- **Bio**: Users can share information about themselves in markdown format. 
- **Portfolio Highlights**: Users can post their finished products and supporting design assets to the Portal for each emergency they support, and have them appear on their profile.
- **Support Profiles**: SIMS Administrators can assign members one or more support profiles, which lets others know what types of products they can create and services they can provide. Each profile has an associated tier, with guidance around who qualifies for what tier.
- **Skills and Languages**: Users can tag the relevant technical skills they possess across a variety of areas, and tag the languages they speak in order to help others find the right person for specific questions.
- **Badges**: Achievement and recognition badges that are given to users appear on their profiles, along with the justification for getting it.
- **Location**: Users can take advantage of the Google Maps integration to search for a location where they work from, in order to help visualize our reach and organize our support across time zones.

### Emergencies

- **Emergency Records**: Each SIMS activation gets its own emergency record, where our collective response is maintained. 
- **Activation Details**: Information can be entered about the emergency itself, as well as the process involved with activating SIMS to support it.
- **Trello Integration**: Each emergency can parse the tagged Trello board to extract open (unassigned) Trello tasks.
- **Learning**: Individual remote supporters and SIMS Remote Coordinators can provide feedback and learning for each response. Remote supporters are given the option of answering a brief survey at the end of their assignment, and Remote Coordinators can provide real-time feedback in a longer-form mechanism. 
- **Badge Assignment**: SIMS Remote Coordinators can assign remote supporters specific badges as they recognize stellar work.
- **Assignment Table and Gantt**: A table summarizes each remote supporter's involvement, and can be visualized with a D3-based Gantt chart.
- **Response Products**: As users post products, if they tag them as "Public", they get placed into a queue for the SIMS Remote Coordinator to review. If approved—meaning it is appropriate to share externally—it will appear for site visitors without having to log in. Products are uploaded by the Portal to Dropbox, where other members can access the underlying assets to reuse or remix them.
- **Response Tools Linkages**: The Portal connects with Slack, Dropbox, and Trello to ensure visitors can find the most important products, assets, and communication channels. 
- **Response Stories**: SIMS Remote Coordinators can draft markdown-friendly blog posts that summarize our response, document key learnings and achievements, and automatically synthesize our statistics. 

### Assignments

- **Tagging to Emergencies**: Each remote supporter's involvement in an emergency is saved as an assignment (only one assignment is necessary even if the person works on multiple products with gaps in between). 
- **Basic Information**: Assignments store basic info about what the person was generally tasked with doing, when they started and ended their support (as estimates), and serves as the vehicle for saving products that the remote supporter created or supported on for that particular emergency.
- **Availability**: For larger-scale, high-volume emergencies, the availability feature can be utilized. Remote supporters can navigate to their assignment and report which days they are available to support. This can help with organizing coverage during intense periods of field requests.

### Public Marketing

- **About Page**: The about page automatically updates with key metrics, including the full list of our activations, a count of active members, and a D3.js map that displays our response history.
- **Profile Types**: Dedicated pages are linked to from the about page that show the basics about each of our remote support profiles, as well as granular descriptions of how each tier (from 1 to 4) differ.
- **Public Portfolio**: Products that are requested to be public and approved by SIMS Remote Coordinators are visible in the portfolio, and filterable by type. 
- **Member Directory**: A full list of active members is available to site visitors, along with individual profiles for each member. These profiles closely match the profile one sees when logged in, but with only publicly-visible portfolio items visible.

### Admin Controls

- **Profile Management**: Admins can assign one ore more support profiles to members.
- **Badge Assignment**: While SIMS Remote Coordinators will typically be the person assigning badges as part of a given response, admins can also assign badges. These include "Special Edition" badges that SIMS Remote Coordinators do not have access to.
- **Member Approvals**: When new users sign up, their accounts are tagged as conditional until an admin approves it.
- **Open Reviews**: A listing of all the SIMS Remote Coordinators' learning records. Admins can see the full list and approve or reject the information in order to process it into standard operating procedures or other change management tools. 
- **Skill Picklist Controls**: Admins can add to the list of skills we track on member profiles.
- **New Badge Uploads**: Admins can create new badges. When created, the badge automatically populates the badges index page and calculates how common it is among SIMS members.

### Learning and Reference Resources

- **Organization by Support Profile**: The resources page organizes our knowledge management articles and guides by our primary support profiles. There are also hubs for standard operating procedures, style guides, and SIMS Portal documentation for admins.
- **learn-sims.org**: In order to make our guide-drafting process open and collaborative, the guides are hosted on a separate site running WordPress. Users can be added to that site and author their own guides and tutorials. 

### Other

- **GO Surge Alerts**: The Portal runs a cron job that downloads the latest surge alerts from the GO API and summarizes them on the dashboard for logged-in members. New alerts trigger a Slack message that gets posted to the Availability channel on the SIMS account, along with basic information about the deployment request.
- **Data Overview**: A few basic visualizations are embedded in the dashboard, to support simple reporting on key metrics.
