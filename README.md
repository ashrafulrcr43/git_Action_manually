# 1. Write yml File 
<pre>
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
</pre>
## Check The name Left side, Run Manually Form Right side select Brach and refresh

# 2. Create Button under workflow 
<pre>
name: manually run

on:
  workflow_dispatch:
    inputs:
      example_input:
        description: 'Choose your Service'
        required: true
        default: 'staging'
        type: choice
        options:
         - staging
         - production

jobs:
  manually_run_git_action:
    runs-on: ubuntu-latest

    steps:
     - name: Create Git Action
       uses: actions/checkout@v2
     - name: Print hello text file
       run: |
         cat hello.txt

  
  
</pre>
# 3. Print user input => staging, production that print when select 
<pre>

  name: manually run

on:
  workflow_dispatch:
    inputs:
      example_input:
        description: 'Choose your Service'
        required: true
        default: 'staging'
        type: choice
        options:
         - staging
         - production

jobs:
  manually_run_git_action:
    runs-on: ubuntu-latest

    steps:
     - name: Create Git Action
       uses: actions/checkout@v2
     - name: print user input
       run: |
          echo "user input: '${{inputs.example_input}}'"
     - name: Print hello text file
       run: |
         cat hello.txt

  
</pre>

# 4. if else statement on jobs 
<pre>
  name: manually run

on:
  workflow_dispatch:
    inputs:
      example_input:
        description: 'Choose your Service'
        required: true
        default: 'staging'
        type: choice
        options:
         - staging
         - production

jobs:
  manually_run_git_action:
    runs-on: ubuntu-latest

    steps:
     - name: Create Git Action
       uses: actions/checkout@v2
     - name: print user input
       run: |
          if [ "${{ github.event.inputs.example_input }}" == "staging" ]; then
            echo "You selected staging"
          elif [ "${{ github.event.inputs.example_input }}" == "production" ]; then
            echo "You selected production"
          else
            echo "Invalid input"
          fi


     - name: Print hello text file
       run: |
         cat hello.txt

  
</pre>
