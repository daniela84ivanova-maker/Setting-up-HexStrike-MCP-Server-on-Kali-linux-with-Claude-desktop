     Cybersecurity with Networkwalks Week 3
    
# Password Hash Extraction and Cracking Using John the Ripper (JtR) and AI

Project Overview

This project explores AI-assisted password recovery using John the Ripper (JtR), Hexstrike-AI, and Claude Desktop in a Kali Linux virtual machine.

The objective was to configure an AI-assisted cybersecurity environment and use it to extract password hashes from three password-protected PDF files and perform password-cracking attempts.

Lab Environment

Operating System: Kali Linux (Virtual Machine)

AI Assistant: Claude Desktop

MCP Server: Hexstrike-AI

Password Cracking Tool: John the Ripper (JtR)

Protocol: Model Context Protocol (MCP)

# Task 1: Setting Up Hexstrike-AI MCP Server with Claude Desktop

Step 1: Install Claude Desktop on Kali Linux

Download and install Claude Desktop using the following commands.

Add the GPG key:

curl -fsSL https://pkg.claude-desktop-debian.dev/KEY.gpg | sudo gpg --dearmor -o /usr/share/keyrings/claude-desktop.gpg

Add the repository:

echo "deb [signed-by=/usr/share/keyrings/claude-desktop.gpg arch=amd64,arm64] https://pkg.claude-desktop-debian.dev stable main" | sudo tee /etc/apt/sources.list.d/claude-desktop.list

Update package lists and install Claude Desktop:

sudo apt update
sudo apt install claude-desktop

Step 2: Download and Configure Hexstrike-AI

Clone the Hexstrike-AI GitHub repository:

git clone https://github.com/0x4m4/hexstrike-ai.git
cd hexstrike-ai

Create a Python virtual environment:

python3 -m venv hexstrike-env

Activate the virtual environment:

source hexstrike-env/bin/activate

Install the required Python dependencies:

pip3 install -r requirements.txt

Step 3: Start the Hexstrike-AI Server

Navigate to the project directory, activate the virtual environment, and start the server:

cd ~/hexstrike-ai
source hexstrike-env/bin/activate
python3 hexstrike_server.py

Step 4: Configure the MCP Server in Claude Desktop

Edit the Claude Desktop MCP configuration file and add the following configuration:

{
  "mcpServers": {
    "hexstrike-ai": {
      "command": "/home/kali/hexstrike-ai/hexstrike-env/bin/python",
      "args": [
        "/home/kali/hexstrike-ai/hexstrike_mcp.py",
        "--server",
        "http://localhost:8888"
      ]
    }
  }
}

Refer to the Hexstrike-AI GitHub repository for configuration instructions.

  # Task 2: Password Hash Extraction and Cracking Using John the Ripper (JtR) and AI

Lab Environment

Hexstrike-AI MCP Server

Claude Desktop

Kali Linux Virtual Machine

John the Ripper (JtR)

Objective

Extract password hashes from three password-protected PDF files and use John the Ripper to perform password-cracking attempts.

Claude Desktop was used to interact with the Hexstrike-AI MCP server through prompts, assisting with the password recovery workflow.

Key Activities

Extract password hashes from three PDF files.

Use John the Ripper to attempt to crack the extracted hashes.

Interact with AI-assisted security tools using Claude prompts.

Review and document the password-cracking results.

Results


