
# (Optional) Exercise 4 - Advanced features of TTA 

In this optional exercise, you will explore advanced features of Tricentis Test Automation (TTA) that help improve test reusability and maintainability. You’ll learn how to create Reusable Test Blocks to standardize common processes across multiple test cases and how to manage Test Data Sets to store, update, and dynamically use data in the cloud. These advanced capabilities will help you reduce test maintenance and streamline large-scale automation scenarios.

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

Get your test data into Tricentis Test Automation by SAP, you have 2 options
1.Create your test data manually 
2.Upload a test data file

**Create test data manually**

To add a small data sample for experimenting or debugging, follow these steps:

1.Go to  Prepare > Test data<br>![](/exercises/ex4/images/CALM_DS_01.png)
2.Click Create data set.Data set & Columns names should be business relevant <br>![](/exercises/ex4/images/CALM_DS_03.png)
3.In the subsequent dialog, define the name of the data set and its first column. Then, select Create.<br>![](/exercises/ex4/images/CALM_DS_04.png)

4.Data set is created with first column, add the columns as per the requirement
Use the edit options to update your data set. For example, add cell values or more columns/rows.<br>![](/exercises/ex4/images/CALM_DS_05.png)<br>![](/exercises/ex4/images/CALM_DS_06.png)


To use test data in a test case, you need to link the two:

1.In your test case, hover over the Value column of the line where you want to use test data. Then, select the wrench icon icon.

Let's say your test case steers a text box called Sales Organization , and you want TTA to enter test data into this text box at runtime. In this case, hover over the Value column of Sales Organization.
<br>![](/exercises/ex4/images/CALM_DS_07.png)

In the subsequent dialog, select Prefill expression values. Then, define the data you want to link.
<br>![](/exercises/ex4/images/CALM_DS_09.png)

Specify your data set or subset, as well as the column that contains the data. 
<br>![](/exercises/ex4/images/CALM_DS_10.png)

Select Prefill values.

To finalize the link, select Apply.
<br>![](/exercises/ex4/images/CALM_DS_08.png)

You can also directly enter these values by using the syntax : **{TDM[Subset][ColumnName]}
**
And that's it! Your test data is now linked to this particular test action.<br>![](/exercises/ex4/images/CALM_DS_11.png)

Repeat the same process for all the values you want to flow from Test Data Set ( Cloud Storage)
<br>![](/exercises/ex4/images/CALM_DS_12.png)

## Summary

You’ve now explored the advanced capabilities of Tricentis Test Automation for SAP, learning how to create Reusable Test Blocks for modular automation and how to leverage Test Data Sets for dynamic, cloud-based data handling. By using these features, you can make your automated tests more scalable, adaptable, and easier to maintain.

# Congratulation to finish all exercises!
