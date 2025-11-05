# Exercise 2 - Best Practices for Automation

In this exercise, you will apply best practices for automation using Tricentis Test Automation (TTA). You’ll learn how to enhance your automated test by introducing dynamic waits for improved stability and cardinality adjustments to optimize attribute reuse. In addition, you’ll follow best practices for naming test steps and folders to ensure your automation remains clear, reusable, and business-relevant.

## Exercise 2.1 Adding Dynamic waits & Increasing Cardinality to re-use the attribute

**Dynamic waits** are used to wait for the specific field to appear before doing any actions. It is recommended to use Dynamic wait (WaitOn) while moving from one page to next, dropdown to appear, search results to appear. In our test case, dynamic wait can be placed on All dropdown.
**Cardinality**: We need this *All* dropdown should appear twice in the test step. Instead of duplicating (as it will increase the memory space), TTA have a feature to increase the occurrence.

1. Navigate to the **Create Quotations (Header Data)** step under **Process** folder. Hover over it and click on 3 dots. Select jump to module option.
2. Module is now opened in a new tab Select the **Create Quotations** button and on the right side navigate in the properties of it to **Cardinality**. (Note: If you don't have this button, rescan and add this field to the module as you did it on Exercise 1.8)
3. Change the value of Cardinality to 1-n to increase the occurence in this test step. This step should now appear several times successively
<br>![](/exercises/ex2/images/TTA_Cardinality.png) Save the module & Close the tab.

4. Go back to Test case tab (Usually you will land here after you close the module Tab).Save the Test case and refresh the page.
   Open the Process folder and select the first step.For the first appearance of **Create Quotations** button add:
   - **Value:** Create Quotations (Same as the button name as we are waiting & verifying the text here) )
   - **Action mode:** WaitOn
     
5. Fill the other values as per the requirement
   <br>![](/exercises/ex2/images/TTA_WaitOn.png)
  
6. Trail run this test step to check the stability and flow check. Once done, add the dynamic waits for the next page **(Create Quotations (Detail Data))**.
7. For this, Select the the second step **(Create Quotations (Detail Data))** of folder **Process**, which should have the button **(Create Quotations Overview)** : (If there is no such field then rescan the module add the field.
   Hover the the this step Click on 3 dots , jump to the module. Modules opens in a new tab.
   Select the **Create Quotations Overview** button. Change the Cardinalilty Property to **1-n*** as above. Save the module & Close the module tab
   <br>![](/exercises/ex2/images/Results.png)
   Navigate to Test case tab and set the value as below
   
   - **Value:** Create Quotations* (please remove everything afer Quotations and insert asterisk -> not possible in GitHub ;-) )
   - **Action mode:** WaitOn
   - <br>![](/exercises/ex2/images/Results1.png)
   
   As mentioned before, Dynamic wait is recommended every time when navigating to a new page (this includes dialog boxes, dynamic menus).

## Exercise 2.2 Naming of Each Test steps & Folders should be Business Relevant

As per the best practices, naming of Test steps should be Business relevant.
Please find the image below and rename your script like shown.
    <br>![](/exercises/ex2/images/TTA_Business_Relevance.png)

This ensures, that also others can understand the flow of the test script, without looking into the details. Renaming the steps in the script do not change the name of the module in the library themselve.


## Summary

You’ve now improved your automated test by applying best practices that make it more stable, efficient, and maintainable. You learned how to use dynamic waits to handle page transitions smoothly, adjust cardinality for reusability, and rename test steps for better readability and business alignment.

Continue with the next step - [Exercise 3 - Create another step recording and handover data](../ex3/README.md)
