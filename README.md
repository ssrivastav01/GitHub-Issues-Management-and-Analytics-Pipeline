# GitHub-Issues-Management-and-Analytics-Pipeline
This project creates a structured pipeline for importing, processing, and visualizing GitHub issues data. Using ElasticSearch and Docker, it enables a scalable approach to analyze and query issue data, and visualize trends using Python. The analysis includes detecting issue phases, assigning priorities, and generating comprehensive visual reports.

## Features

Automated GitHub Issues Import: Uses the GitHub API to import issues from specified repositories, allowing seamless data integration.

Data Labeling and Processing: Categorizes issues based on predefined phases, priorities, and statuses, enabling a structured approach to data handling.

ElasticSearch Data Storage: Utilizes a Dockerized ElasticSearch environment to store and manage issue data for efficient querying and retrieval.

Visualization and Reporting: Generates visualizations of issue trends, including issue creation and closure rates, using Python's data visualization libraries.

Dockerized Environment: The entire project is Dockerized, ensuring consistency and ease of setup across different environments.

## Workflow and Phases
The project is organized into three phases, each focusing on specific aspects of GitHub issue management and analysis.

### Phase 1: Initial Setup and Issue Management
GitHub Setup: Create a GitHub ID following specific naming conventions. This ID is used for collaboration and tracking.

Fork Repository: The main repository is forked, and collaborators are added for direct access.

Issue Creation and Labeling: Issues are created using OpenAI's ChatGPT to generate titles and descriptions. Each issue is labeled based on a structured scheme:

OriginationPhase: Categorizes the initial phase of the issue (e.g., Coding, Testing, Requirements).

DetectionPhase: Marks the phase where the issue was detected.

Priority: Assigns a priority level to each issue.

Status: Indicates the current state of the issue (e.g., inProgress, Approved).

Category: Classifies the issue type (e.g., Bug, Enhancement).

### Phase 2: Data Update and Advanced Labeling
Issue Labeling Update: Issues are revisited, with labels assigned based on specific criteria.

Repository Synchronization: The repository is updated to ensure alignment with the latest main repository changes.

Commit and Push: After making updates, changes are committed with the issue number referenced in the commit message, ensuring traceability.

### Phase 3: ElasticSearch Integration and Visualization
ElasticSearch Setup: Dockerized ElasticSearch is used to index and manage issue data, allowing for quick access and querying of stored issues.
### Data Import and Visualization:
A Jupyter Notebook (Importing_Issues_from_GitHub.ipynb) imports issue data into ElasticSearch using a GitHub token.

Another notebook (Charting_imported_issues.ipynb) generates charts, such as:

Daily issues closed by phase (bar chart).

Issues created by status (stacked chart).

Docker and ElasticSearch for Data Querying: Dockerized ElasticSearch is used to create and pull data indexes. The data is queried based on various filters, including:
Top similar issues within the repo.

Specific issues tagged with "Rendering React" between certain dates.

### Visualization Examples
Some example visualizations included in this project:

Total Issues Closed per Origination Phase: A bar chart visualizing the number of issues closed daily, categorized by the origination phase.

Issues Created by Status: A stacked bar chart showing issues created by their current status.

ElasticSearch Query Results: Top 5 similar issues for specified tags and date ranges.

### Technologies Used
Programming Languages: Python (with Jupyter Notebooks for data manipulation and visualization).

Database: ElasticSearch (Dockerized for easy deployment and management).

Data Visualization: Matplotlib, Pandas.

APIs: GitHub API for issue data import.

Containerization: Docker, ensuring a portable and scalable environment.

### Challenges and Learnings
Throughout the project, several challenges were addressed:

API Rate Limits: Handling GitHub API rate limits during issue import, managed by implementing controlled query intervals.

Data Management with ElasticSearch: Setting up and using ElasticSearch with Docker for large-scale issue data storage and fast retrieval.

Complex Labeling: Developing a robust labeling scheme for issues based on predefined criteria and managing it across multiple project phases.

### Future Enhancements
Enhanced Query Capabilities: Incorporate more sophisticated search queries to improve issue tracking and prioritization.

Dashboard Integration: Build a real-time dashboard for tracking issue trends, priorities, and phases.

Automated Reporting: Add a feature for scheduled generation of PDF reports summarizing issue metrics and trends.

### Conclusion
This project demonstrates a comprehensive approach to GitHub issues management and analysis. By leveraging Docker, ElasticSearch, and Python, it creates a scalable system for data ingestion, storage, and visualization, providing valuable insights into GitHub issue trends and workflows.
