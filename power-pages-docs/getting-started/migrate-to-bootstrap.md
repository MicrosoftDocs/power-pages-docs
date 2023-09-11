## Migrate existing site from Bootstrap v3 to Bootstrap v5 using PAC CLI

**Pre-requisite**

1.  You need PAC CLI to use the Bootstrap upgrade tool to migrate your v3 sites to Bootstrap v5

2.  We suggest for migration of your existing website, please create a dev environment to run the migration tool and test the changes with respect to the production website.

3.  You can migrate power pages site based out of **any** template.


### **Installation Instructions**

1.  Install the Power Platform Tools for Visual Studio Code: [Microsoft Power Platform CLI - Power Platform \| Microsoft Learn](https://learn.microsoft.com/en-us/power-platform/developer/cli/introduction#install-using-power-platform-tools-for-visual-studio-code)

2.  You'll have to **enable FCB** in PAC CLI to use the command required to migrates sites from v3 to v5. Before beginning this step, ensure that the PAC version is 1.23.3 or higher.

    1.  If PAC is installed using the VS Code extension -

        1.  Steps -

            1.  open the file : C:\\Users\\&lt;User&gt;\\AppData\\Roaming\\Code\\User\\globalStorage\\microsoft-isvexptools.powerplatform-vscode\\pac\\tools\\featureflags.json and

            2.  change the value of the flag **verbPAPortalBootstrapMigrate** from 'off' to 'on'

    2.  If PAC tool is installed using [PAC CLI](https://aka.ms/PowerAppsCLI),

        1.  Steps

            1.  open the file &lt;install-directory&gt;\\tools\\featureflags.json and

            2.  change the value of the flag **verbPAPortalBootstrapMigrate** from 'off' to 'on'

3.  Authenticate to the Dataverse Org from where the website record will be downloaded for migration.

    1.  Open the command prompt.

    2.  Command: pac auth create --url https://dataverseOrg.crm10.dynamics.com

    3.  PAC CLI Auth ref: [Pac Auth](https://learn.microsoft.com/en-us/power-platform/developer/cli/reference/auth)

### **Running the migration tool**

1.  If your site user SVG file anywhere. Please make sure you enabled .svg file support for your site in your environment. Steps -

    1.  Choose Gear icon in top bar and then choose **advanced** settings

    2.  Click on dropdown next to settings and choose **Customizations**

### **Step 1: Creating two sites in Bootstrap v3**

1.  We **suggest** to create two sites with Bootstrap v3 in your environment. Use one of these sites in the migration process. The second site created is only for a reference to compare with the migrated site. Migration can be performed with just one site.

**Note** – This is not a prerequisite but a suggestion from our end.

### **Step 2: Downloading the website folder**

1.  List the websites in the current organization using the command :  
 **pac paportal list**

2.  Download the website folder using PAC CLI download command( [PAC CLI Doc](https://learn.microsoft.com/en-us/power-platform/developer/cli/reference/paportal#pac-paportal-download) ).

    1.  Command Prompt: pac paportal download -p "DownloadDestinationPath" -id "WebsiteID"

    2.  Where **-p refers to the folder path and -id refers to the website id**

### **Step 3: Running the migration tool on the website folder**

1.  Use the bootstrap-migrate command to run the tool on the downloaded website folder.

    1.  Command : pac paportal bootstrap-migrate -p "WebsiteFolderPath"

2.  A new folder is created after running the migration with "**V5**" appended to the name of the folder.

### **Step 4: Reviewing the diffs using the custom VS code extension: BootstrapMigrationDiff**

1.  Open the V5 folder which was created after the migration process in VS Code

2.  Open a html/css file to compare the difference.

    1.  Ex: check the header web template.

    2.  Go to "web templates/header". Open the header source html file: "Header.webtemplate.source.html"

3.  Run the bootstrap diff extension to compare the changes.

    1.  In VS code execute "Ctrl + Shift + P" to open the command palette.

    2.  In the command palette execute the command "Bootstrap Diff".

    3.  On execution V3 file will open on the right alongside the V5 file in a different window, with the changes being highlighted.

    4.  V5 file on the left will also show the breaking change as a tooltip when you hover over the highlighted change.

### **Step 5: Uploading the migrated website record**

1.  Use the PAC CLI upload command to upload the migrated website record to the org

    1.  Command : pac paportal upload -p "MigratedWebsiteFolderPath"

### **Step 6: Comparing the two websites.**

1.  After uploading, the migrated site will be a Bootstrap v5 compliant website.

2.  Compare the diffs using the diff extension and compare the rendering of Site 1 (on Bootstrap v3) and Site 2 (on Bootstrap v5).

3.  Based on the above comparisons, you can make changes to the code of Bootstrap v5 site as needed based on the changes introduced with Bootstrap v5.

## FAQ (Frequently Asked Questions)

### I see some UX changes on the new sites created with Bootstrap v5. Is this expected?

While we have tried to preserve the look and feel of the Bootstrap v5 templates in comparison to Bootstrap v3, there are certain changes which have been introduced with Bootstrap v5 which render a slightly different UX. The functionality of the Bootstrap v5 site with respect to components remains exactly same including forms, lists etc. Here are few known UX/UI tweaks that users can expect -

1.  Icons tweaks

    1.  Breadcrumb icon changes from ![](media/image7.png) to ![](media/image8.png)

    2.  Action button item changes from ![](media/image9.png) to ![](media/image10.png)

2.  Spacing tweaks

3.  UX tweaks to text control

    1.  Text box edges are curvy ![](media/image12.png)

4.  Color and margin tweaks.

