# Exercise 1 - Creating an automated test case with TTA from SAP Cloud ALM

In this exercise, you will learn how to create and record an automated test case using SAP Cloud ALM together with Tricentis Test Automation (TTA). You will go through the non-polished end-to-end process — from creating a new automated test case in SAP Cloud ALM to configuring parameters, capturing screens, and building the login and process flows in TTA.

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
3. Run the Launcher Setup from Downloads and wait for it to completed. Close the success message

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

Save your script on the upper right with a click on button **Save**

## Exercise 1.4 - Capturing the Login screen fields (Attributes) of S/4HANA system

1. Click via right mouse click > Open in new window [SAP S/4HANA system](https://flp.tdc.sap.com:50081/sap/bc/ui2/flp?sap-client=001&sap-language=EN#Shell-home).

2. Switch back to TTA tab and click on tab **Modules** in the left panel and then **Create module**
   <br>![](/exercises/ex1/images/TTA_Create_Module.png)

3. After clicking Create Module button, below pop-up appears. Select the Web Application from the list (This screen is to select the type of application (Web, Desktop, etc…))
    <br>![](/exercises/ex1/images/TTA_Scan_App_Popup.png)

4. It might happen, that the Tricentis Launcher is starting a setup. If this takes longer than 2 minutes, just let us know. You might also to login again:
   <br>**User:** BTM163-XXX@education.cloud.sap *(replace the XXX with the number which is assigned to you!)*
   <br>**Password:** Acce$$teched25
   
6. The XScan application as shown in the below screenshot appears. Select the browser window with the opened S/4HANA system and press button **Scan**.
   <br>![](/exercises/ex1/images/TTA_Xscan_Select_App.png)

7. Capture the fields *User Name*, *Password* and the button *Log On*. Mark the title of the Log On button more dynamic and unique and rename the module accordingly so that you can easily find your own module later in the module area (e.g. *XXX S/4HANA Fiori Login* (replace XXX by your user number)
   <br>![](/exercises/ex1/images/TTA_Capture_Login&Rename.png)

8. Click on **Finish Screen** and close the scanning.

## Exercise 1.5 - Creating Login flow as Precondition

1. Under **Standard objects** tab on the left panel, search for *OpenURL*, click on + icon next to the module as shown to add it to the test case.
2. Move the step under the folder **Precondition** and edit the name of the Test step to “Launch Fiori”.
3. Add the URL of S/4HANA system as value for URL.
    <br>![](/exercises/ex1/images/TTA_Module_OpenURL.png)
4. Under **Modules** tab on the left panel, search for your newly created module *XXX S/4HANA Fiori Login*. Click on + icon next to the module and move it below the *Launch Fiori* step.
    <br>![](/exercises/ex1/images/TTA_Add_Module_Login.png)
5. Enter the value of the user and the password and set the Data type for password to “Password” for the encryption. Select *'{Click}* as value for the Logon button.
    - **User:** BTM163-XXX *(replace XXX with your assigned user number)*
    - **Password:** Teched2025
    <br>![](/exercises/ex1/images/TTA_Enter_Login_Data.png)
6. Click on **Save**, select the Fiori Login step and click on button **Run** to run only these steps for a dry run until login. You need to focus on the S/4HANA logon window for this.
7. Once login is completed, leave the browser window open - you need it for the next exercise.

## Exercise 1.6 - Creating Modules for Application search in Fiori homepage

1. Click on *Create Module* button on the top left menu. In Scan application screen, select the S/4HANA screen.
2. Capture the Search button, rename it to *XXX Click on Search* (replace XXX with your user number) and save the module.
3. Search for the module in the test case screen, add it and run this step to click on the Search field.
4. Repeat the steps 1-3 for the search field (name: *XXX Search for Application in Fiori Home page* (replace XXX with your user number).) 
5. Repeat the steps 1-3 for tile **Manage Sales Quotation** (name: *XXX Manage Sales Quotation -Tile* (replace XXX with your user number)).
6. Repeat the steps 1-3 for button **Create Quotation** in the screen (name: *Manage Sales Quotation - Home Screen*) and save.
   <br>![](/exercises/ex1/images/TTA_Quot_Start.png)


## Exercise 1.7 - Record steps for Quoation creation

1. Once the next page is loaded, click on button **Create Module**, select Web Application, select the S/4HANA system and click on **Scan**.
2. Select the following controls on this page:
    <br> **Quotation Type, Sales Organization, Distribution Channel, Division**
3. Select the *(iframe) Application*; the properties of it appear on the right side. Scroll down to the property **Id** and change it to “__container*-iframe”. The “*” is needed to make the property flexible because the number changes whenever the iframe is refreshed or loaded.
4. Remember the module name and save the module.
5. Add this module now to the test case and insert the following values in the test step
  - **Quotation Type:** QT
  - **Sales Organization:** 1710
  - **Distribution Channel:** 10
6. “X” can be used instead of {Click} for Buttons & Links.
  <br>![](/exercises/ex1/images/TTA_Quot_Entry_Data.png)
7. Do a dry run for this test step.
8. Once the next page is loaded, follow the process of creating a new module for the next screen (you know already how it works :) )
<br> - Click on Create Module button
<br> - Select Web Application
<br> - Select the browser window with the S/4HANA system
<br> - Select the controls you need in this page: 
    - **Input Fields:** Sold-to-Party, Ship-to-Party, Cust. Reference, Cust. Ref. Date, Valid To
    - **Tables:** All Items
    - **Buttons:** Save, Cancel
9. Select the (iframe) for *Application* and scroll the properties on the right side up to *Id'* property
10. Edit the *Id* property to “__container*-iframe” to make it independent
11. Save the module. Remember the name of the modules to search later for it.
12. Add the new module to the test case and insert the following values to the step:
    - **Sold-to-Party:** USCU-L-210
    - **Ship-to-Party:** USCU-L-210
    - **Cust. Reference:** XXX-Test Automation Ref *(replace XXX by your user number)*
    - **Cust. Ref. Date:** *todays date*
    - **Valid To:** *todays date + 7 days*
    - **Material:** DM_210
    - **Quantity:** 2
    - **Save:** X
  <br>![](/exercises/ex1/images/TTA_Quotation_Ready.png)
   
## Exercise 1.8 - Rescan Module
1. After Quotation has been successfully saved, click on the last created module (Details of Quotation) and jump to the module
 <br>![](/exercises/ex1/images/TTA_Jump_Module.png)
2. Click on Rescan and scan the Save Button in the dialog window
3. Save your changes, go back to your test steps and click refresh
4. Set as value for the save button a "X"
5. Run the test step and repeat from step 1 to rescan the SAP Statusbar to capture the success message on the bottom left corner.

## Exercise 1.9 - Dynamic Placeholders & Buffers for future use (e.g. to use it on following test case)

1. Change the value of **Valid To** to: *{Date[][+7d][yyyy.MM.dd]}* This will replace a static date value, which makes the test case independent from the date of execution. It will now always use todays date + 7 days. Replace also the **Customer Reference Date* to {Date} to use always todays date.
2. As next step, we are going to buffer the output data for future use. For this, we are using the command {XB[Buffer Name]} - X buffers are used to verify the pattern and buffer the required section.
3. Enter in the **SAP Statusbar** value: Quotation {XB[QuotationID]} has been saved.
4. Try now for a complete run of Create Sales Quotation test case.

5. Are you getting the sync error while Navigating between the pages? The next exercise will solve that issue ;-)

## Summary

You have successfully created your first automated test case from SAP Cloud ALM with Tricentis Test Automation. By completing this exercise, you learned how the  tools works together, capture application elements, define reusable modules, and automate a business process from login to quotation creation.

Continue now to - [Exercise 2 - Best Practices for Automation](../ex2/README.md)
