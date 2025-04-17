# irs-appdynamics-machineagent-kt

This repository contains the instructions and sample configuration for installing the AppDynamics Machine Agent.

## Prerequisites

1. **Java Installation**: Ensure that Java 8 or later is installed on the machine.
   - Verify Java installation:
     ```sh
     java -version
     ```
   - If Java is not installed, download and install it from [Oracle's Java Downloads](https://www.oracle.com/java/technologies/javase-downloads.html) or use your system's package manager.

2. **AppDynamics Account**: You need an AppDynamics account to download the Machine Agent and access the Controller.

## Installation Steps

1. **Download the Machine Agent**:
   - Visit the [AppDynamics Downloads](https://download.appdynamics.com/) page.
   - Download the Machine Agent for your operating system.

2. **Extract the Agent**:
   - Extract the downloaded `.zip` or `.tar.gz` file to a directory of your choice:
     ```sh
     unzip machineagent.zip -d /path/to/machineagent
     ```

3. **Configure the Agent**:
   - Navigate to the `conf` directory inside the extracted Machine Agent folder.
   - Edit the `controller-info.xml` file to include your Controller details:
     ```xml
     <controller-info>
         <controller-host>your-controller-host</controller-host>
         <controller-port>your-controller-port</controller-port>
         <account-name>your-account-name</account-name>
         <account-access-key>your-access-key</account-access-key>
         <application-name>your-application-name</application-name>
         <tier-name>your-tier-name</tier-name>
         <node-name>your-node-name</node-name>
     </controller-info>
     ```

4. **Start the Machine Agent**:
   - Run the following command to start the agent:
     ```sh
     java -jar machineagent.jar
     ```

5. **Verify Installation**:
   - Log in to the AppDynamics Controller and check if the Machine Agent is reporting data.

## Configuration Files

### `conf/controller-info.xml`
This file contains the configuration details for connecting the Machine Agent to the AppDynamics Controller. Key fields include:
- `controller-host`: The hostname or IP address of the AppDynamics Controller.
- `controller-port`: The port number for the Controller (default is 8090 for HTTP or 443 for HTTPS).
- `account-name`: Your AppDynamics account name.
- `account-access-key`: The access key for your account.
- `application-name`: The name of the application being monitored.
- `tier-name`: The tier within the application.
- `node-name`: The node name within the tier.

### `logging-config.xml`
This file defines the logging configuration for the Machine Agent. You can adjust the log level (e.g., INFO, DEBUG) and log file location.

### Custom Extensions
You can add custom monitoring extensions by placing them in the `monitors` directory. Refer to the [AppDynamics Extensions](https://www.appdynamics.com/community/exchange/) page for available extensions.

#### `extensions/ServerMonitoring/conf/ServerMonitoring.yml`
To add tags for your VM in the ServerMonitoring.yml file, you can include a tags section under the server configuration. Tags are useful for categorizing and filtering your VMs in the AppDynamics Controller.

## Troubleshooting

- **Agent Not Reporting**: Check the logs in the `logs` directory for errors.
- **Java Issues**: Ensure the correct version of Java is installed and accessible in your `PATH`.

For more details, refer to the [AppDynamics Machine Agent Documentation](https://docs.appdynamics.com/).

---
