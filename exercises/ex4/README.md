
# (Optional) Exercise 4 - Advanced features of TTA 

In this exercise, ...

## Exercise 4.1 Reusable Test Blocks

Reusable test steps are sets of steps that you can reuse across multiple test cases. If anything changes in your application under test and you update your reusable test steps, Tricentis Test Automation for SAP integrated with SAP Cloud ALM automatically updates all test cases that contain them. This reduces test maintenance effort, so you can focus on getting your application ready for release.

1. Open your test case and add a new Test Steps Folder. Name it Create Sales Quotation.
   <br>![](/exercises/ex4/images/CALM_RTB_01.png)
2. Place the test steps according to the flow which are reusable as per the business requirements.
3. Select the folder, click on the three dots at the end of the selected line and select the option "Convert to reusable test step"
  <br>![](/exercises/ex4/images/CALM_RTB_02.png)
4. In the following dialog, select the option "Manually set up business parameters later" and click button "Apply".<br>![](/exercises/ex4/images/CALM_RTB_03.png)
5. The folder and its content is now migrated to a Reusable Test Block. You can access it via click on the options button (with the three dots) and "Jump to reusable test step"<br>![](/exercises/ex4/images/CALM_RTB_04.png)
6. The reusable Test Block will open in a new tab. Select the folder and click again the options button (with the three dots). Click on "Create parameter (child to selected)".<br>![](/exercises/ex4/images/CALM_RTB_05.png)
7. Go to Test Steps and enter the parameter name in curly brackets: {PL[<Business Parameter Name>]}.<br>![](/exercises/ex4/images/CALM_RTB_06.png)
8. Pass the values in the parameters instead of in the Test steps to make it independent.
<br>![](/exercises/ex4/images/CALM_RTB_07.png)
## Exercise 4.2 Creation of Test Data Set

If you want to keep your data in cloud and you need to make periodic/regular update of those data using Automation, TTA have the inbuilt feature called Test Data set.
To use test data in a test case, you need to link the two:
1.In your test case, hover over the Value column of the line where you want to use test data. Then, select the <br>![](/exercises/ex4/images/Wrench Symbol.svg)icon.

Let's say your test case steers a text box called First name, and you want SAP Enterprise Continuous Testing by Tricentis to enter test data into this text box at runtime. In this case, hover over the Value column of First name.

In the subsequent dialog, select Prefill expression values. Then, define the data you want to link:

Specify your data set or subset, as well as the column that contains the data.

Select Prefill values.

To finalize the link, select Apply.

And that's it! Your test data is now linked to this particular test action.




## Summary

You've now ...

Continue to - [Exercise 3 - Excercise 3 ](../ex3/README.md)

