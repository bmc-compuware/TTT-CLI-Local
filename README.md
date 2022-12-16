# TTT-CLI-Local

The TTT-Scenario-Execute action allows your GitHub Actions workflow to trigger a workflow in your instance of BMC Compuware where you want to execute scenario based on you program. This action can be used in scenarios where your test scenario source is stored in Git, or when you want your GitHub Actions workflow to operate on source that is already stored in your local workspaces. <br>
          
# Table of Contents

  * TTT-CLI-Local
    * [Table of Contents](https://github.com/marketplace/actions/ttt-cli-local-test-scenario/#Table%20of%20Contents)
    * [Prerequisite](https://github.com/marketplace/actions/ttt-cli-local-test-scenario/#Prerequisite)
    * [Usage](https://github.com/marketplace/actions/ttt-cli-local-test-scenario/#Usage)
    * [Inputs](https://github.com/marketplace/actions/ttt-cli-local-test-scenario/#Inputs)
    * [Outputs](https://github.com/marketplace/actions/ttt-cli-local-test-scenario/#Outputs)
    * [Troubleshooting](https://github.com/marketplace/actions/ttt-cli-local-test-scenario/#Troubleshooting)
    * [License summary](https://github.com/marketplace/actions/ttt-cli-local-test-scenario/#License%20summary)
    * [Limitation](https://github.com/marketplace/actions/ttt-cli-local-test-scenario/#Limitation)

# Prerequisite

 * You can host your own runners and customize the environment used to run jobs in your GitHub Actions workflows, Click [here](https://docs.github.com/en/actions/hosting-your-own-runners/about-self-hosted-runners).
 * User need to setup Topaz workbench CLI into local system.

# Usage

          #Triggers the workflow on push or pull request events but only for the "xxxxx" branch that may be main, master or your feature branch

          push:<br>
                    branches: ["xxxxxx"]
          pull_request:
                    branches: ["xxxxx"]
          #Allows you to run this workflow manually from the Actions tab
          workflow_dispatch:
          #A workflow run is made up of one or more jobs that can run sequentially or in parallel
          jobs:
          #This workflow contains a single job called "build"
          build:
          #The type of runner that the job will run on
          runs-on: self-hosted    
          #Steps represent a sequence of tasks that will be executed as part of the job
          steps:
          - run: git config --global core.longpaths true
          #Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it
          - uses: actions/checkout@v2
          with:
          clean: false
          path: ${{ github.workspace }}
          name: ${{ env.VERSION_MAJOR }}.${{ env.VERSION_MINOR }}

          #Runs a single command using the runners shell
          - name: Calling the CLI function
          run: C:\\Topaz\\topazworkbenchcli.20.12.03.134\\TotalTestFTCLI.bat -data "${{ inputs.workspace }}" -host "${{ inputs.hciconnection }}" -port "${{ inputs.port }}" -u "pinaka0" -p "fresp0rt" -s "${{ inputs.repository_server }}" -cesu "pinaka0" -cesp "fresp0rt" -f "${{ inputs.testFolderPath }}" -R -G -v "6" -l "jenkins" -loglevel "info"
     
 
# Inputs


| Input name | Required | Description |
| --- | --- | --- |
| hciconnection | Required  | HCI connection required to connect the system |
| port  | Required  | port reuired to run the CLI |
| testFolderPath | Required  | testFolderPath is your local path where you test cases being executed |
| workspace  | Required  | workspace is required for local setup |
| repository_server  | Required  | Repository server is required to connect and get the data from the server |
| User id  | Required  | LPAR user id required for connection |
| Password  | Required  | Password is required for connection |


# Outputs

Output will saved in testlocationpath in your local system.

# Troubleshooting

To enable debug logging in your GitHub actions workflow, see the guide [here](https://docs.github.com/en/actions/monitoring-and-troubleshooting-workflows/enabling-debug-logging).

# License summary

This code is made available under the MIT license.

# Limitation


   
