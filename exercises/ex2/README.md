# Exercise 2 - Best Practices for Automation

In this exercise, we will create...

## Exercise 2.1 Adding Dynamic waits & Increasing Cardinality to re-use the attribute

**Dynamic waits** are used to wait for the specific field to appear before doing any actions. It is recommended to use Dynamic wait (WaitOn) while moving from one page to next, dropdown to appear, search results to appear. In our test case, dynamic wait can be placed on All dropdown.
**Cardinality**: We need this *All* dropdown should appear twice in the test step. Instead of duplicating (as it will increase the memory space), TTA have a feature to increase the occurrence.

1. Navigate to the first step of folder **Process**.
2. Select the **searchFieldinShell-select** and navigate in the properties of it to **Cardinality**.
3. Change the value of Cardinality to 1-n to increase the occurence in this test step. This step should now appear several times successively
4. For the first appearance of it add:
   - **Value:** *Apps * (please remove the space between Apps and the asterisk -> not possible in GitHub ;-) )
   - **Action mode:** WaitOn
5. For the second appearance of **searchFieldinShell-select** add:
   - **Value:** Apps
  
6. Trail run this test step to check the stability and flow check. Once done, add the waits for the next page (Results page).
7. For this, replace in the second step of folder **Process**, which should be **Search for results** the field **Results**:
   - **Value:** *Result * (please remove the space between Apps and the asterisk -> not possible in GitHub ;-) )
   - **Action mode:** WaitOn
   
   As mentioned before, Dynamic wait is recommended every time when navigating to a new page (this includes dialog boxes, dynamic menus).

## Exercise 2.2 Naming of Each Test steps & Folders should be Business Relevant

As per the best practices, naming of Test steps should be Business relevant.
Please find the image below.

## Summary

You've now ...

Continue to - [Exercise 3 - Excercise 3 ](../ex3/README.md)
