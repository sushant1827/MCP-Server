# MCP-Server

This repository contains workflow configurations for a Model Context Protocol (MCP) server that integrates AI capabilities with n8n automation platform.

## Overview

The project consists of two main components:

1. **MCP Server** - A server that exposes AI tools through n8n's MCP Trigger and connects various services.
2. **Social Media Post Generator** - A workflow that uses AI to create professional social media content.

## Features

- AI-powered social media post generation
- Todo list management via Airtable
- Calculator functionality
- Extensible architecture for adding more AI tools

## Workflows

### MCP Server

![image](https://github.com/user-attachments/assets/1a9339a3-2d40-40f2-8c73-bb97bd665c5f)

The MCP Server workflow acts as the central hub for all AI functionality. It:

- Exposes a webhook endpoint at `/test`
- Provides access to the following tools:
  - Calculator
  - Social Media Post Generator
  - Airtable Todo List Management (List, Add, Update)

### Social Media Post Generator

![image](https://github.com/user-attachments/assets/13c576df-cdc8-4dd1-9d89-bed65455d645)

This workflow is designed to:

- Accept a query input
- Use OpenAI's GPT-4o-mini model to generate professional social media content
- Return the generated content to the calling workflow

## Requirements

- n8n version 1.0.0 or higher
- OpenAI API account
- Airtable account with appropriate permissions

## Setup Instructions

1. **Import Workflows**
   - Import `MCP_Server.json` and `Social_Media_Post_Generator.json` into your n8n instance

2. **Configure Credentials**
   - Set up OpenAI API credentials for the Chat Model node
   - Configure Airtable Personal Access Token for the Airtable Tool nodes

3. **Airtable Setup**
   - Ensure you have a base with ID `appEVZyRnoMDAkayU` (or update the configuration to match your base)
   - Create a table named "Table 1" with columns:
     - Name (string)
     - Completed (boolean)

4. **Activate the Workflows**
   - Activate both workflows in your n8n instance

## Usage

### Using the MCP Server

The MCP Server exposes various AI capabilities through the n8n interface. You can interact with it by:

1. **Creating Social Media Posts**
   ```
   Use the create_social_media_content tool with a query parameter
   ```

2. **Managing Todo Items**
   ```
   - List all todos using the List_ToDos tool
   - Add a new todo with the Add_ToDo tool (provide Name and Completed status)
   - Update an existing todo with the Update_ToDo tool (provide record ID, Name, and Completed status)
   ```

3. **Performing Calculations**
   ```
   Use the calculator tool for mathematical operations
   ```

## Technical Details

### Workflow Connections

- The MCP Server Trigger connects to all available tools
- The Social Media Post Generator is triggered by the Social Post Generator tool
- All Airtable operations are configured as separate tools

### Configuration Notes

- The Social Media Post Generator uses the GPT-4o-mini model
- Airtable interactions are configured for a specific base and table

## Contributing

Contributions are welcome! Here are some ways you can contribute:

- Add new AI tools to the MCP Server
- Improve existing tool functionality
- Create documentation and usage examples
- Fix bugs and optimize performance

## Acknowledgements

- This project uses n8n (https://n8n.io) as the automation platform
- AI capabilities are powered by OpenAI's models
- Data storage is handled by Airtable
