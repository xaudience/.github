# XAudience Project

## Description
A service that provides statistics, metrics, insights based on audience data from various social networks.

## Details
Planned platforms to support: currently Telegram only, also Twitter is in question due to its API policy, Discord looks suitable to start support it, but still needs research.

How a user can interact with the service: through the user web interface or through a bot, if the platform provides this feature.

### Goals
Create platform-agnostic analytics service that preserves the anonymity of users.

### Use Cases
- A user can explore audiences
- A user can inspect a specific audience
    - Audience preferences
- A user can see the audience comparison
    - Count of mutual audience
    - General audience preferences
- A user can see an interactive graph of audiences

*The term audience in this context means audience of a channel, account, group, etc.*

## System Design
![System design](assets/system-design.drawio.png)

### User Web Application
React application with GraphQL hooks for data fetching. The application's static files are delivered to users via CDN.

### Stuff Web Application
Allows stuff to monitor and control internal systems.

### Stuff Web Server
Watches all internal systems, collects statistical data, logs errors and other useful info.

### Analyzer
Reads and analyzes audience data and writes results to database.

### Data Aggregator
Collects, parses, scrapes raw data from social network or another type of social platform and writes it to the database.