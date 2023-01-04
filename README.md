# Overview
BMC Compuware Topaz for Total Test Auto Run is the extension which can be used to execute the Unit test or functional test scenarios automatically when a pipeline is started. 

# BMC AMI DevX Total Test

The TTT-Scenario-Execute action allows your GitHub Actions workflow to trigger a workflow in your instance of BMC Compuware where you want to execute scenario based on you program. This action can be used in scenarios where a test scenario source is stored in Git, or when you want your GitHub Actions workflow to operate on source that is already stored in your local workspaces. <br>
          
# Table of Contents

  * TTT-CLI-Local
    * [Table of Contents](https://github.com/marketplace/actions/ttt-cli-local-test-scenario/#Table%20of%20Contents)
    * [Prerequisite](https://github.com/marketplace/actions/ttt-cli-local-test-scenario/#Prerequisite)
    * [Usage](https://github.com/marketplace/actions/ttt-cli-local-test-scenario/#Usage)
    * [Inputs](https://github.com/marketplace/actions/ttt-cli-local-test-scenario/#Inputs)
    * [Outputs](https://github.com/marketplace/actions/ttt-cli-local-test-scenario/#Outputs)
    * [Troubleshooting](https://github.com/marketplace/actions/ttt-cli-local-test-scenario/#Troubleshooting)
    * [License summary](https://github.com/marketplace/actions/ttt-cli-local-test-scenario/#License%20summary)
    * [Product Assistance](https://github.com/marketplace/actions/ttt-cli-local-test-scenario/#Limitation)

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

Output will saved in Output folder created under Test Location Path in your local system.

# Troubleshooting

To enable debug logging in your GitHub actions workflow, see the guide [here](https://docs.github.com/en/actions/monitoring-and-troubleshooting-workflows/enabling-debug-logging).

# License summary

This code is made available under the BMC license.

# Product Assistance

BMC provides assistance for customers with its documentation, the BMC Support Center web site, and telephone customer support.

### BMC Support Center

You can access online information for BMC products via our Support Center site at [https://support.bmc.com](https://support.bmc.com/). Support Center provides access to critical information about your BMC products. You can review frequently asked questions, read or download documentation, access product fixes, or e-mail your questions or comments. The first time you access Support Center, you must register and obtain a password. Registration is free.

### Contacting Customer Support

At BMC, we strive to make our products and documentation the best in the industry. Feedback from our customers helps us maintain our quality standards. If you need support services, please obtain the following information before calling BMC\'s 24-hour telephone support:

- The Azure pipeline job output that contains any error messages or pertinent information.

- The name, release number, and build number of your product. This information is displayed in the installed extensions page. Apply filter: BMC in order to display all of the installed BMC extension.

- Environment information, such as the operating system and release on which the Topaz CLI is installed.

You can contact BMC in one of the following ways:


#### Web

You can report issues via BMC Support Center: [https://support.bmc.com](https://support.bmc.com/).

Note: Please report all high-priority issues by phone.

### Corporate Web Site

To access BMC site on the Web, go to [https://www.bmc.com/](https://www.bmc.com/). The BMC site provides a variety of product and support information.


   
