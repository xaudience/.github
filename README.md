# XAudience Project

## Description
A service that provides statistics, metrics, insights based on audience data from various social networks.

## Details
Planned platforms to support: currently Telegram only, also Twitter is in question due to its API policy, Discord looks suitable to start support it, but still needs research.

### Goals
Create platform-agnostic and scalable analytics service that preserves the anonymity of users.

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

### User Web Interface
React application with GraphQL hooks for data fetching. The application's static files are delivered to users via CDN.

### Stuff Web Interface
Allows stuff to monitor and control internal systems.

### Stuff Web Server
Watches all internal systems, collects statistical data, logs errors and other useful info.

### Business Logic
Processes user logic, acts as a backend for User Web Application.

### Calculation Controller
Acts as a middleware between business logic and calculation services.

### Analyzer
Reads and analyzes audience data and writes results to database.

### Data Aggregator
Collects, parses, scrapes raw data from social network or another type of social platform and writes it to the database.

## Decisions
Since the libraries for working with platforms API are implemented using different technologies, it's a good way to use the libraries natively, without any bindings or interactions with the ABI or FFI. Therefore, data aggregators implementations depends on the platform API library technology.