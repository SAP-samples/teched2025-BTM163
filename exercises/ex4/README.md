
# (Optional) Exercise 4 - Advanced features of TTA 

In this exercise, ...

## Exercise 3.1 Reusable Test Blocks

Reusable test steps are sets of steps that you can reuse across multiple test cases. If anything changes in your application under test and you update your reusable test steps, Tricentis Test Automation for SAP integrated with SAP Cloud ALM automatically updates all test cases that contain them. This reduces test maintenance effort, so you can focus on getting your application ready for release.

1. Open your test case and add a new Test Steps Folder. Name it Create Sales Quotation.
2. Place the test steps according to the flow which are reusable as per the business requirements.
3. Select the folder, click on the three dots at the end of the selected line and select the option "Convert to reusable test step"
4. In the following dialog, select the option "Manually set up business parameters later" and click button "Apply".
5. The folder and its content is now migrated to a Reusable Test Block. You can access it via click on the options button (with the three dots) and "Jump to reusable test step"
6. The reusable Test Block will open in a new tab. Select the folder and click again the options button (with the three dots). Click on "Create parameter (child to selected)".
7. Pass the values in the parameters instead of in the Test steps to make it independent.

## Exercise 3.2 Creation of Test Data Set

If you want to keep your data in cloud and you need to make periodic/regular update of those data using Automation, TTA have the inbuilt feature called Test Data set.



## Summary

You've now ...

Continue to - [Exercise 3 - Excercise 3 ](../ex3/README.md)

