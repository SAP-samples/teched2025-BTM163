# Exercise 1 - Creating an automated test case with TTA from SAP Cloud ALM

In this exercise, we will create a test case in SAP Cloud ALM, that is then recorded with Tricentis Test Automation tool.

## Exercise 1.1 - Creating an automated test case in SAP Cloud ALM and enter TTA

1. Click on tab **Implementation** and on tile **Test Preparation**.
<br>![](/exercises/ex1/images/CALM_Imp_TestPrep.png)
  

2.	Check, if Project **TechEd Transformation Project** is selected. Press than button "Create"
<br>![](/exercises/ex1/images/CALM_Create_TC.png)

3.  To create a new test case, enter on the side panel the following values:
    <br>**Type:** Automtated
    <br>**Automation Provider:** TTA_for_SAP
    <br>**Title:** ###-Sales Order Processing for Non-Stock Material (2ET)     *(replace the ### with your user number)*
    <br>**Project:** TechEd Transformation Project
    <br>**Scope:** BTM163 - Cloud ALM & TTA
    <br>**Solution Process:** Sales Order Processing for Non-Stock Material (2ET)
    <br>**Country/Region:** Germany
<br>![](/exercises/ex1/images/CALM_Create_TC_save.png)

4.   The test case is now created on Cloud ALM side, as well as on TTA side. Jump to TTA by **clicking on the test case name** in the context area.
<br>![](/exercises/ex1/images/CALM_link_TTA.png)

## Exercise 1.2 - Install the Launcher

1. Before starting any recording in TTA, the Launcher needs to be installed. For this press the **Download** button at the upper right corner and click then on Download.
   <br>![](/exercises/ex1/images/Launcher_Setup.png)
3. Run the Launcher Setup and wait for it to completed. Close the success message

## Exercise 1.3 - Initial Setup of the automated test case

1. Once TTA URL Launched, create a new parameter. It will define the browser for execution.
    <br>**Name:** Browser
    <br>**Data Type:** String
    <br>**Value:** Chrome
<br>![](/exercises/ex1/images/TTA_Create_Parameter.png)

2.	Create 3 Test step folders
    <br> - Precondition   *(Contains login flows and prerequisites)*
  	<br> - Process        *(Contains the actual business flow, Validation flow)*
  	<br> - Postcondition  *(Contains post validation steps (Ex: Logout & Close browser))*
<br>![](/exercises/ex1/images/TTA_Create_Folders.png)

## Exercise 1.4 - Create new module for the Login to S/4HANA system

1. Click to open [SAP S/4HANA system](https://btm163-7rq549xc.eu10-004.alm.cloud.sap/launchpad#Shell-home) and follow the steps below:
   # add infos here

2. Go back to TTA and click on tab **Modules** in the left panel and then **Create module**
   <br>![](/exercises/ex1/images/TTA_Create_Module.png)

3. After clicking Create Module button, below pop-up appears. Select the Web Application from the list (This screen is to select the type of application (Web, Desktop, etc…))
    <br>![](/exercises/ex1/images/TTA_Scan_App_Popup.png)

4. It might happen, that the Tricentis Launcher is starting a setup. If this takes longer than 2 minutes, just let us know. The XScan application as shown in the below screenshot appears. Select the browser window with the opened S/4HANA system and press button **Scan**.
   <br>![](/exercises/ex1/images/TTA_XScan_App_Select.png)

5. Capture the fields *User Name*, *Password* and the button *Log On*. Mark the title of the Log On button more dynamic and unique and rename the module accordingly so that you can easily find it later in the module area (e.g. *S/4HANA Fiori Login*)
   <br>![](/exercises/ex1/images/TTA_Capture_Login&Rename.png)

6. Close the scanning.

## Exercise 1.5 - Add the module to the Test Case and adapt it

1. Under **Standard objects** tab on the left panel, search for *OpenURL*, click on + icon next to the module as shown to add it to the test case.
2. Move the step under the folder **Precondition** and edit the name of the Test step to “Launch Fiori”.
3. Under **Modules** tab on the left panel, search for your newly created module *S/4HANA Fiori Login*. Click on + icon next to the module and move it below the *Launch Fiori* step.
4. Pass the value of the user by adding the parameter *Username* as shown below. Enter the password and set the Data type as “Password” for the encryption.
5. Click on **Save** and then on button **Run** to run these two steps for a dry run until login.
6. Once login is completed, eave the browser window open - you need it for the next exercise.

## Exercise 1.6 Re-Scanning of Modules to modify or add extra fields

1. Click on *Create Module* button on the top left menu. In Scan application screen, select the S/4HANA screen.
2. Capture the *All* dropdown menu, rename the module to "Fiori Home" and save the module.
3. Run this step to select the *Apps* in the dropdown. Observe the UI change after selecting Apps from the dropdown; “Search text box” properties changes after selecting the dropdown option. 
4. Search for the newly created module *Fiori_Home*, click on Jump to Module next to the + icon.
5. Module will open in new tab will open, click then on Rescan. (Fiori web page should be kept in the state where you want to capture the new fields)
6. Add the required fields from the page and save it. Once saved, close the scan window and refresh the module page.
7. Create a folder and rename it as *Create Sales Quotation* under **Process folder** in the test case.
8. Add the newest created module. Rename the test step to *Search for the Application in Fiori Home Page* and enter the following values:
   <br> **Menu-Dropdown:** Apps
   <br> **Search In: "Apps":** Manage Sales Quotations
   <br> **Search:** {Click}
9. Do a run for this test step.
10. Click on Create Module button, select **Web Application** and click **Start Scan**.
11. Select again the S/4HANA system browser window and click on button **Scan**.
12. Select the button *Create Quotation* in the screen, rename the module to *Manage Sales Quotation - Home Screen* and save.
13. Search for the module in the test case screen and add it.
14. Add {Click} as Input to the **Create Quotation button**.
15. Do a dry run for this test step.

## Exercise 1.7 - Record steps for Quoation creation

1. Once the next page is loaded, click on button **Create Module**, select Web Application, select the S/4HANA system and click on **Scan**.
2. Select the following controls on this page:
    <br> **Quotation Type, Sales Organization, Distribution Channel, Division, Sales Office, Sales Group**
3. Select the *(iframe) Application*; the properties of it appear on the right side. Scroll down to the property **Id** and change it to “__container*-iframe”. The “*” is needed to make the property flexible because the number changes whenever the iframe is refreshed or loaded.
4. Remember the module name and save the module.
5. Add this module now to the test case and insert the following values in the test step
6. “X” can be used instead of {Click} for Buttons & Links.
7. Do a dry run for this test step.
8. Once the next page is loaded, follow the process of creating a new module for the next screen
    <br> - Click on Create Module button
    <br> - Select Web Application
    <br> - Select the browser window with the S/4HANA system
    <br> - Select the controls you need in this page: **Input Fields:** Quotation, Sold-to-Party, Ship-to-Party, Cust. Reference, Cust. Ref. Date, Valid To, **Tables:** All Items, **Buttons:** Save, Cancel
9. Select the (iframe) for *Application* and scroll the properties on the right side up to *Id'* property
10. Edit the *Id* property to “__container*-iframe” to make it independent
11. Save the module. Remember the name of the modules to search later for it.
12. Add the new module to the test case and insert the following values to the step:
    - **Sold-to-Party:**
    - **Ship-to-Party:**
    - **Cust. Reference:**
    - **Save:**

## Exercise 1.8 Dynamic Placeholders & Buffers for future use (e.g. to use it on following test case)

1. Change the value of **Valid To** to: *{Date[][+1y][yyyy.MM.dd]}* This will replace a static date value, which makes the test case independent from the date of execution. It will now always use todays date + one year.
2. As next step, we are going to buffer the output data for future use. For this, we are using the command {XB[Buffer Name]} - X buffers are used to verify the pattern and buffer the required section.
3. Enter in the **SAP Statusbar** value: Quotation {XB[QuotationID]} hase been saved.
4. Try now for a complete run of Create Sales Quotation test case.

5. Are you getting the sync error while Navigating between the pages? The next exercise will solve that issue ;-)

## Summary

You've now created your first automated test case with SAP Cloud ALM and Tricentis Test Automation tool.

Continue to - [Exercise 2 - Design the Test Case in Tricentis Test Automation](../ex2/README.md)
