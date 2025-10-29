# Exercise 3 - Create another step recording and handover data

In this exercise, you will extend your automation by creating a new recording for the Sales Order creation process using a Sales Quotation as reference. You’ll duplicate existing steps to save effort, structure them into a new folder, and modify values to match the new process. Finally, you’ll learn how to handover data—specifically the quotation number—between test cases to enable seamless end-to-end test automation.

## Exercise 3.1 Record process "Creating a Sales Order with Sales Quotation Reference"

1.Create a Test step folder and name it as "Create Sales Order" under Process.<br>![](/exercises/ex3/images/CALM_SO_01.png)

2. Hover over the **Search for the Application in Fiori Home Page** and Click on the  (3 dots) in the Create Sales Quotation folder<br>![](/exercises/ex3/images/CALM_SO_02.png)

3. Select **Duplicate** option <br>![](/exercises/ex3/images/CALM_SO_03.png)<br>
4. Hover over the duplicated step and click on the icon with the six dots and move the test step to Create Sales Order **<br>![](/exercises/ex3/images/CALM_SO_04.png)<br>
5. The folders **Create Sales Quotation** and **Create Sales Order** should appear below the folder **Process**<br>
6. Change value in the **Search in Apps** text box to *Manage Sales Orders* <br>![](/exercises/ex3/images/CALM_SO_05.png)<br>
7. Capture the Search results screen <br>![](/exercises/ex3/images/CALM_SO_06.png)<br>
8. Add the step to the Create Sales Order folder <br>![](/exercises/ex3/images/CALM_SO_07.png)<br>
9. In Manage Sales Order screen, Expand the Create with reference drop down <br>![](/exercises/ex3/images/CALM_SO_08.png)<br>
10. Capture this screen by using Select on Screen option in the Scan window <br>![](/exercises/ex3/images/CALM_SO_09.png)<br>
11. Search for the module and jump to the module. Module will open in new tab <br>![](/exercises/ex3/images/CALM_SO_10.png)<br>
12. Click on the icon with the six dots and move the Create with Reference button to the top and save it.<br>![](/exercises/ex3/images/CALM_SO_11.png)<br>![](/exercises/ex3/images/CALM_SO_12.png)<br>
13. Go back to the Test case tab and add this module to the Create Sales Order folder <br>![](/exercises/ex3/images/CALM_SO_13.png)<br>
14: Pass the Values in test step as below <br>![](/exercises/ex3/images/CALM_SO_14.png)<br>
15. Capture the next screen <br>![](/exercises/ex3/images/CALM_SO_15.png)<br>
16. Search & Add this module to the folder. Here we are going to use the Sales Quotation buffered in the previous process<br>
      In last step of previous exercise we stored the Sales Quotation value in “QuotationID”<br>
      **{B[Buffer Name]}**- is the syntax to re-use the stored buffered in the test step<br>
      These buffers are temporarily stored for the session across the workspace.<br>
      Test step should appear as below<br>
      In Sales order type text drop down box use the option available in Value column of the test step and select the value as below.<br>![](/exercises/ex3/images/CALM_SO_16.png)<br>
17. Capture the next screen <br>![](/exercises/ex3/images/CALM_SO_17.png)<br>
18. Pass the values in the test step as below <br>![](/exercises/ex3/images/CALM_SO_18.png)<br>
19. Create the module for the next screen , Select the **Standard Order 1#####11 has been saved.** control, Change the **Text** Property to "**Standard Order * has been saved.**" to make it flexible
20. Select **Identify by** in the scan window (next to **Select on Screen**), Select **Index**<br>![](/exercises/ex3/images/CALM_SO_20.png)<br>
21. In Identify by Index Pane in the right select the check, now the control will be unique. Remove the Sales order number from the name of the control to make it flexible. and save the module <br>![](/exercises/ex3/images/CALM_SO_21.png)<br>
22. Add the module as the test step and fill the value as below.
Here we need to save the Sales Order number for further process or may be to next test case 
So the {XB[SalesOrderNumber]} has been added in the place of Sales order number displayed in the screen and the action mode as Verify. This will verify the pattern and store the value.<br>![](/exercises/ex3/images/CALM_SO_22.png)<br>



## Summary

You’ve now created a new automated recording for Sales Order creation with Quotation Reference and learned how to reuse and adapt existing steps efficiently. By handing over the quotation number dynamically between test cases, you’ve established a data-driven link that supports end-to-end business process automation across multiple test scenarios.

Continue to - [Exercise 4 - (Optional) Exercise 4 - Advanced features of TTA](../ex3/README.md)
