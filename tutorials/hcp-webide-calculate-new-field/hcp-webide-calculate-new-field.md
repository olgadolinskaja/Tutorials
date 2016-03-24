---
title: Calculate and display a new field in an SAPUI5 app
description: Learn how to add an additional tab, and more data fields to an SAPUI5 app.
tags: [tutorial:product/hcp, tutorial:product/sapui5_web_ide, tutorial:product/mobile, tutorial:product/sap_ui5]
---

## Prerequisites
 - **Proficiency:** Intermediate
 - **Tutorials:** [Add a tab and additional fields to an SAPUI5 app](http://go.sap.com/developer/tutorials/hcp-webide-add-tab.html)

## Next Steps
 - Localizing your SAPUI5 app (coming soon)

## Details

### You will learn
There are times when a use case calls for the generation of a data field that is not available from the back-end system. One example of this would be calculation of a customized risk value for a sales opportunity and mapping the result to a high, medium or low category.

 ![Calculated Field Example](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-calculate-new-field/mob3-2_0.png)

### Time to Complete
**10-15 min**

---

1. Log into your HCP account and open SAP Web IDE in a Google Chrome browser.

    Open the **northwind** project folder and then the **view** folder. Double-click on `Detail.controller.js`, and scroll down to the `bindView` function.

    ![original bindview function](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-calculate-new-field/mob3-2_1.png)

2. The first step is to add some code to get the data passed in for the detail view. To do this, you will create a local variable (`record`) and make a call on the `oView` object to get the model and data (passing in the entity path). You will also insert the `debugger;` command to pause execution so you can review the data available to you in `record`.

    ```javascript


3. Select **index.html** and run your app. In the preview tab, open Developer Tools (F12 or Option-Command-I), then select one of the items in the master list.
     ![execution halted at debugger statement](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-calculate-new-field/mob3-2_3.png)

4. The next step is to compute the Current Inventory Value field, round the number, and then update the model/UI bindings.
    * Line 88: A constant for the mark up percentage that will be used to calculate the unit cost
6. Line 90 does the real work:

     ![rounding](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-calculate-new-field/mob3-2_7.png)

8. To add a label for the new field, open the **i18n > messageBundle.properties** file and add a new line for the inventory value label:

    ```xml
    label_CurrentInventoryValue=Current Inventory Value

9. Open the **view > Detail.view.xml** file, add the following XML to the `ObjectHeader`, Beautify and save your change.

    ![Detail.view.xml file](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-calculate-new-field/mob3-2_9.png)

10. With all changes saved, switch back to your preview tab (with Developer Tools open), and reload the page by right-clicking on the browser refresh button and selecting Empty Cache and Hard Reload.  


11. When the app loads, it will pause on the debugger statement again. Click on the **Step Over** button to advance the debugger line by line, and watch the **Scope** pane for variable values as the execution proceeds.

    ![Detail.view.xml file](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-calculate-new-field/mob3-2_11.png)

    ![computed but unrounded](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-calculate-new-field/mob3-2_12.png)

    Click the **Step Over** button again and the value is now rounded.

13. Click the **Resume script execution** button to allow the execution to continue. If you look in the detail view header, you will see the Current Inventory Value field displayed.

14. For clean-up, you can remove the `debugger;` statement in `Detail.controller.js` along with the blank lines, save your changes and re-deploy to HCP.  

    ![cleaned up function](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-calculate-new-field/mob3-2_14.png)

## Next Steps
 - Localizing your SAPUI5 app (coming soon)