# DevLake - Installation and Configuration Guide

## Introduction

**DevLake** is a data engineering platform designed to collect, store, and analyze software development data from various tools.

This guide provides detailed instructions to set up and use DevLake in your local environment.

## Requirements

- Docker and Docker Compose installed  
- A **GitHub Access Token** (for GitHub integration)

## Installation

1. Clone the DevLake repository:

   ```sh
   git clone https://github.com/leds-org/leds-dashboard.git
   cd leds-dashboard
   ```

2. Configure the variables in `docker-compose.yml` and `.env` as needed.

3. Generate the `ENCRYPTION_SECRET` using the following command:

   ```sh
   openssl rand -base64 2000 | tr -dc 'A-Z' | fold -w 128 | head -n 1
   ```

4. Start DevLake by running:

   ```sh
   docker-compose up -d
   ```

   This will start the containers needed to run the DevLake environment.

5. Access the DevLake dashboard at [`http://localhost:4000`](http://localhost:4000).  
   - Use the **username** and **password** configured in `docker-compose.yml` to log in.

## Configuration and Integration

### Creating a GitHub Connection

1. In the side menu, click on **Connections**.  
2. Select **GitHub** and click on **Create a New Connection**.

   ![Manage Connections](./images/manage_connections.png)

3. Fill in the required information and enter the **GitHub Access Token** for authentication.

   ![Manage Connections Details](./images/manage_connections_details.png)

4. Test the connection by clicking **Test Connection**.  
5. Click **Save Connection**. After saving, you'll be redirected to the connection screen:

   ![Connection Details](./images/connection_details.png)

6. Click on **+ Add Data Scope**, select the desired repositories, and click **Save**.

### Creating a Project

1. In the side menu, click **Projects** and then **+ New Project**.  
2. Enter a project name and click **Save**.  
3. When editing the project, in the **Data Connection** section, click **+ Add a Connection**.  
4. Select the previously created connection, choose the desired repositories, and click **Save**.  
5. Adjust the data sync frequency under the **Sync Policy** menu within the project.

Your DevLake environment is now configured and ready to use!

## Data Visualization with Grafana

DevLake uses **Grafana** to display the collected data.

1. Access Grafana at [`http://localhost:4000/grafana`](http://localhost:4000/grafana).  
2. Use the default credentials **admin:admin** to log in (it's recommended to change the password after the first login).  
3. Access Grafana’s main dashboard:

   ![Grafana dashboards](./images/grafana_dashboards.png)

4. In the side menu, click on **Dashboards** to view the available dashboards.

   Example of a GitHub dashboard:

   ![Dashboard GitHub](./images/dashboard_github.png)

## Conclusion

Your DevLake environment is ready to use! You can now explore and analyze the data collected from the integrated tools.

For more information, check out the [official documentation](https://devlake.apache.org/docs/GettingStarted).