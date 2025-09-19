trigger:
- main

pool:
  vmImage: 'ubuntu-latest'

steps:
- script: echo "Installing dependencies..."
- script: echo "Running tests..."
- script: echo "Building project..."
