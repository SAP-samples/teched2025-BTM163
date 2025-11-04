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

2.	Create 3 Test step folders to have a clear structure of your test case.
    <br> - Precondition   *(Contains login flows and prerequisites)*
  	<br> - Process        *(Contains the actual business flow, Validation flow)*
  	<br> - Postcondition  *(Contains post validation steps (Ex: Logout & Close browser))*
<br>![](/exercises/ex1/images/TTA_Create_Folders.png)

Save your script on the upper right with a click on button **Save**

## Exercise 1.4 - Capturing the Login screen fields (Attributes) of S/4HANA system

1. Click via right mouse click > Open in new window [SAP S/4HANA system](https://flp.tdc.sap.com:50081/sap/bc/ui2/flp?sap-client=001&sap-language=EN#Shell-home). It is important that the S/4 system is opened in a seperate window in Chrome Browser.

2. You are now prepared for creating your first module. Modules are collections of technical controls (objects) that TTA identifies and stores from the application. Each control corresponds to an UI element or API endpoint TTA can automate.
To create one, switch back to TTA tab and click on tab **Modules** in the left panel,then Click on**Create** button and select **Create Module** button
   <br>![](/exercises/ex1/images/TTA_Create_Module.png)

   Close these Launcher Popups if you find it ( It only appears one time after the launcher installation)
    <br>![](exercises/ex1/images/Launcher Popup1.png)
    <br>![](exercises/ex1/images/Launcher Popup2.png)

4. After clicking Create Module button, below pop-up appears. Select the Web Application from the list (this screen is to select the type of application e.g. Web, Desktop, etc…)
    <br>![](/exercises/ex1/images/TTA_Scan_App_Popup.png)

5. It might happen, that the Tricentis Launcher is starting a setup. If this takes longer than 2 minutes, just let us know. You might also to login again with your Cloud ALM credentials. Here they are again for your reference:
   <br>**User:** BTM163-XXX@education.cloud.sap *(replace the XXX with the number which is assigned to you!)*
   <br>**Password:** Acce$$teched25
   
6. The XScan application as shown in the below screenshot appears. Select the browser window with the opened S/4HANA system and press button **Scan**.
   <br>![](/exercises/ex1/images/TTA_Xscan_Select_App.png)

7. We recommend to use the advanced mode of Xscan. You can activate it by clicking on "Advanced". Click on **Select on Screen** option in the Xscan Window.
Capture the fields *User Name*, *Password* and the button *Log On*, by just clicking on the UI fields. The captured fields will immediately shown as selected elements in the Xscan Application.

8. Rename the module accordingly so that you can easily find your own module later in the module area (e.g. *XXX S/4HANA Fiori Login* (replace XXX by your user number)
   <br>![](/exercises/ex1/images/TTA_Capture_Login&Rename.png)

9. Click on **Finish Screen** and close the scanning (Close XScan window).

## Exercise 1.5 - Creating Login flow as Precondition

1. Switch back to the browser window *Builder | Default | Tricentis Tosca*. Under **Standard objects** tab on the left panel, search for *OpenURL*, Hover over the OpenURL module and click on + icon next to the module as shown to add it to the test case.

2. Move the step *OpenURL* under the folder **Precondition** 
    - Hold curser over the step, on the very left of the line, 6 dots appear
    - Hold left mouse click to move
 
3. Copy the full URL of S/4HANA system and enter that as value for URL.
    <br>![](/exercises/ex1/images/TTA_Module_OpenURL.png)
    
4. Edit the name of the Test step *OpenURL* to “Launch Fiori”.
5. Under **Modules** tab on the left panel, search for your newly created module *XXX S/4HANA Fiori Login*. Click on + icon next to the module and move it below the *Launch Fiori* step.
    <br>![](/exercises/ex1/images/TTA_Add_Module_Login.png)
6. Enter the value of the user and the password and set the Data type for password to “Password” for the encryption. Select *'{Click}* as value for the Logon button.
    - **User:** BTM163-X *(replace X with the second digit of your assigned user number, e.g. User = 43 then replace the X with 3)*
    - **Password:** Teched2025
    - **Logon:** {Click}
    <br>![](/exercises/ex1/images/TTA_Enter_Login_Data.png)
7. Click on **Save**,
8. Select specifically only the Fiori Login step and click on button **Run** to run only these steps for a dry run until login. You need to focus on the S/4HANA logon window for this.
    <br>![](/exercises/ex1/images/TTA_SelectStep_Run.png)
9. If the logon failed in S/4 due to cookie issue (timeout), just click again on run.
10. Once login is completed, close the unnecessary windows in S/4 system like Tour and confirm that you **Never** want to save your password. Leave the S/4HANA browser window open. We are going to build on that.
    <br>![](/exercises/ex1/images/TTA_NeverSave_PW.png)

## Exercise 1.6 - Use prepared Testing Block for your test script

1. Switch back to your test script. For saving time of recording modules, we have prepared for you a Reusable Test Block, which you can use directly inside your test script. We are going to show you later, how to create such Reusable Test Blocks.
2. In the left panel, click on tab **Reusable test steps**. Click on + for *App Navigation via Tiles* to add it to your script.
   <br>![](/exercises/ex1/images/TTA_Add_ReusableTB.png)

3. Move your Reusable Test Block under the *Process* folder and enter a X as value for Manage Sales Quotations, as shown in the screenshot below.
   <br>![](/exercises/ex1/images/TTA_ReusableTB_Move_Value.png)

3. Select only the step *App Navigation via Tiles* and click on **Run**.
   <br>![](/exercises/ex1/images/TTA_RTB_Run.png)

3. After the run was successfull, leave the S/4HANA system as it is. Switch now back to your Builder (Tosca) and open the Modules again. Add the module "** Template** Click Create Quotation" to add it to your script. You see, you can build your test case from different sources.
   <br>![](/exercises/ex1/images/TTA_Add_TemplateModule.png)

4. Move the module also to **Process** folder, under the step *App Navigation via Tiles* and enter an "X" as value for Create Quoation button. It is an alternative of using {Click} as value. Select only the "** Template** Click Create Quotation" and click on **Run** to run only this step in the target system.
      <br>![](/exercises/ex1/images/TTA_Run_Click_CreateQuot.png)

5. We are now ready to create a new Quotation. Let's continue with it and repeat what we have learned by creating again a new module to capture the screen.

## Exercise 1.7 - Record steps for Quoation creation

1. Switch back to your Builder (Tosca) and click on button **Create Module**, select Web Application, select the S/4HANA system and click on **Scan** (as shown in [Exercise 1.4](/exercises/ex1/README.md#exercise-14---capturing-the-login-screen-fields-attributes-of-s4hana-system) )
2. Select the following controls on this page:
   <br> **Input Fields:** Quotation Type, Sales Organization, Distribution Channel, Division
   <br> **Buttons:** Continue
   <br> Rename the module e.g. *XXX - Create Quotation (Header Data)*, click on **Finish Screen** and close Xscan.
   <br>![](/exercises/ex1/images/TTA_Quot_Capture_Header.png)
<!--- 3. Select the *(iframe) Application*; the properties of it appear on the right side. Scroll down to the property **Id** and change it to “__container*-iframe”. The “*” is needed to make the property flexible because the number changes whenever the iframe is refreshed or loaded.'' --->
4. Add this module now to the test case, move it the last position in folder *Process* and insert the following values in the test step
  - **Quotation Type:** QT
  - **Sales Organization:** 1710
  - **Distribution Channel:** 10
  - **Division:** 00
  - **Continue:** X *(Remember: “X” can be used instead of {Click} for values of Buttons & Links.)*
  <br>![](/exercises/ex1/images/TTA_Quot_Entry_Data2.png)
6. Run only this test step (just select the step *XXX - Create Quotation (Header Data)* and click **Run**)
7. Once the next page is loaded, follow the process of creating a new module for the next screen (you know already how it works :) )
<br> - Click on Create Module button
<br> - Select Web Application
<br> - Select the browser window with the S/4HANA system
<br> - Select the controls you need in this page: 
    - **Input Fields:** Sold-to-Party, Ship-to-Party, Cust. Reference, Cust. Ref. Date, Valid To
    - **Tables:** All Items
    - **Buttons:** Save, Cancel
  <br>![](/exercises/ex1/images/TTA_Quot_Capture_Details.png)
8. Rename the module (e.g. *XXX - Create Quotation (Details Data)*) and save it.
9. Switch back to Builder (Tosca) Add the new module to the test case and insert the following values to the step:
    - **Sold-to-Party:** USCU-L-210
    - **Ship-to-Party:** USCU-L-210
    - **Cust. Reference:** XXX-Test Automation Ref *(replace XXX by your user number)*
    - **Cust. Ref. Date:** *todays date*
    - **Valid To:** *todays date + 7 days*
    - **Material:** DM_210
    - **Quantity:** 2
    - **Save:** X
  <br>![](/exercises/ex1/images/TTA_Quotation_Ready2.png)

10. Select the step for entering Details Data for Quotation and click Run. Lets the script do the work until a pop-up appear.
   
## Exercise 1.8 - Rescan Module
1. After Quotation was not able to be successfully saved, we need to rescan the page, because now we want to click on button save again.
2. Switch back to your Builder (Tosca), click on the last created module (*XXX - Create Quotation (Details Data)*) and click onjump to the module
 <br>![](/exercises/ex1/images/TTA_Jump_Module2.png)
3. Click on Rescan and scan the Save Button in the dialog window
4. Save your changes, go back to your module and click refresh to see the newly captured item.
  <br>![](/exercises/ex1/images/TTA_Quot_Details_Rescan1.png)
5. Switch to your test script, click refresh to see the new item and set as value for the save button a "X"
6. Run the test step and repeat from step 3 to rescan also the SAP Statusbar to capture the success message on the bottom left corner (we need the Quotation number later to create a Sales Order). Move the SAP Statusbar message in the module themselve to the last position
7. Finally, it should look like in the screenshot below.
 <br>![](/exercises/ex1/images/TTA_Quot_Details_Rescan2.png)

## Exercise 1.9 - Dynamic Placeholders & Buffers for future use (e.g. to use it on following test case)

1. That the script still runs in two weeks or later, we need to adapt the fixed date values. Therefor change the value of 
  - **Valid To** to: *{Date[][+7d][dd.MM.yyyy]}*  It will now always use todays date + 7 days. 
  - **Customer Reference Date** to: *{Date[][][dd.MM.yyyy]}* to use always todays date.
2. As next step, we are going to buffer the output data for future use. For this, we are using the command {XB[Buffer Name]} - X buffers are used to verify the pattern and buffer the required section. For this
  - Enter in the **SAP Statusbar** value: *Quotation {XB[QuotationID]} has been saved.* and set the Action Mode to *Verify*
 <br>![](/exercises/ex1/images/TTA_Quot_DynamicPlaceholders.png)
4. Try now for a complete run of Create Sales Quotation test case:
  - Close the S/4 browser window, select all steps (or none) of your test script and click on button **Run**
5. Are you getting the sync error while Navigating between the pages? The next exercise will solve that issue ;-)

## Summary

You have successfully created your first automated test case from SAP Cloud ALM with Tricentis Test Automation. By completing this exercise, you learned how the  tools works together, capture application elements, define reusable modules, and automate a business process from login to quotation creation.

Continue now to - [Exercise 2 - Best Practices for Automation](../ex2/README.md)
