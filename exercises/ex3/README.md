# (Optional) Exercise 3 - Create another step recording and handover data

In this exercise, you will extend your automation by creating a new recording for the Sales Order creation process using a Sales Quotation as reference. You’ll duplicate existing steps to save effort, structure them into a new folder, and modify values to match the new process. Finally, you’ll learn how to handover data—specifically the quotation number—between test cases to enable seamless end-to-end test automation.

## Exercise 3.1 Record process "Creating a Sales Order with Sales Quotation Reference"

1. Create a Test step folder for "Create Sales Quotation" under Process and in the left panel, click on tab User assets. Click on + for App Navigation via Tiles to add it to your script., like shown in the screenshot.
<br>![](/exercises/ex3/images/CALM_SO_01.png)

2. Move your Reusable Test Block under the Create Sales Order folder and enter a X as value for Manage Sales Order, as shown in the screenshot below.
<br>![](/exercises/ex3/images/CALM_SO_02.png)

3. Select the above step only and click on Run. You should land Manage Sales Order screen.
4. In Manage Sales Order screen, Expand the Create with reference drop down <br>![](/exercises/ex3/images/CALM_SO_08.png)<br>
5. Capture this screen by using **Select on Screen** option in the Scan window <br>![](/exercises/ex3/images/CALM_SO_09.png)<br>
6. Search for the module and jump to the module. Module will open in new tab <br>![](/exercises/ex3/images/CALM_SO_10.png)<br>
7. Click on the icon with the six dots and move the Create with Reference button to the top and save it.<br>![](/exercises/ex3/images/CALM_SO_11.png)<br>![](/exercises/ex3/images/CALM_SO_12.png)<br>
8. Go back to the Test case tab and add this module to the Create Sales Order folder <br>![](/exercises/ex3/images/CALM_SO_13.png)<br>
9: Pass the Values in test step as below <br>![](/exercises/ex3/images/CALM_SO_14.png)<br>
10. Capture the next screen <br>![](/exercises/ex3/images/CALM_SO_15.png)<br>
11. Search & Add this module to the folder. Here we are going to use the Sales Quotation buffered in the previous process<br>
      In last step of previous exercise we stored the Sales Quotation value in “QuotationID”<br>
      **{B[Buffer Name]}**- is the syntax to re-use the stored buffered in the test step<br>
      These buffers are temporarily stored for the session across the workspace.<br>
      Test step should appear as below<br>
      In Sales order type text drop down box use the option available in Value column of the test step and select the value as below.<br>![](/exercises/ex3/images/CALM_SO_16.png)<br>
12. Capture the next screen <br>![](/exercises/ex3/images/CALM_SO_17.png)<br>
13. Pass the values in the test step as below <br>![](/exercises/ex3/images/CALM_SO_18.png)<br>
14. Create the module for the next screen , Select the **Standard Order 1#####11 has been saved.** control, Change the **Text** Property to "**Standard Order * has been saved.**" to make it flexible (/exercises/ex3/images/CALM_SO_23.png)<br>
15. Select **Identify by** in the scan window (next to **Select on Screen**), Select **Index**<br>![](/exercises/ex3/images/CALM_SO_20.png)<br>
16. In Identify by Index Pane in the right select the check, now the control will be unique. Remove the Sales order number from the name of the control to make it flexible. and save the module <br>![](/exercises/ex3/images/CALM_SO_21.png)<br>
17. Add the module as the test step and fill the value as below.
Here we need to save the Sales Order number for further process or may be to next test case 
So the {XB[SalesOrderNumber]} has been added in the place of Sales order number displayed in the screen and the action mode as Verify. This will verify the pattern and store the value.<br>![](/exercises/ex3/images/CALM_SO_22.png)<br>



## Summary

You’ve now created a new automated recording for Sales Order creation with Quotation Reference and learned how to reuse and adapt existing steps efficiently. By handing over the quotation number dynamically between test cases, you’ve established a data-driven link that supports end-to-end business process automation across multiple test scenarios.

Continue to - [Exercise 4 - (Optional) Exercise 4 - Advanced features of TTA](../ex3/README.md)
