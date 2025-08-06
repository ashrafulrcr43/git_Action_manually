# 1. Write yml File 
name: manually run

on:
  workflow_dispatch:

jobs:
  manually_run_git_action:
    runs-on: ubuntu-latest

    steps:
     - name: Create Git Action
       uses: actions/checkout@v2
     - name: Print hello text file
       run: |
         cat hello.txt

# Check The name Left side, Run Manually Form Right side select Brach and refresh
