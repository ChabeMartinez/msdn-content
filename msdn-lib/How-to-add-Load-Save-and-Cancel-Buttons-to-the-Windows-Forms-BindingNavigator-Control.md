
[Source](https://msdn.microsoft.com/en-us/library/vstudio/safa4957(v=vs.100).aspx "Permalink to Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control")

# Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control


The [BindingNavigator][2] control is a special-purpose [ToolStrip][3] control that is intended for navigating and manipulating controls on your form that are bound to data.

Because it is a [ToolStrip][3] control, the [BindingNavigator][2] component can be easily modified to include additional or alternative commands for the user.

In the following procedure, a [TextBox][4] control is bound to data, and the [ToolStrip][3] control that is added to the form is modified to include load, save, and cancel buttons.

### To add load, save, and cancel buttons to the BindingNavigator component

1. Add a [TextBox][4] control to your form.

2. Bind it to a [BindingSource][5], which is bound to a data source. For this example, the [BindingSource][5] is bound to a database.

3. After the dataset and table adapter are generated, drag a [BindingNavigator][2] control to the form.

4. Set the [BindingNavigator][2] control's [BindingSource][6] property to the [BindingSource][5] on the form that is bound to the controls.

5. Select the [BindingNavigator][2] control.

6. Click the smart tag glyph (![Smart Tag Glyph][7]) so the BindingNavigator Tasks dialog appears and select Edit Items.
The Items Collection Editor appears.

7. In the Items Collection Editor, complete the following:

    1. Add a [ToolStripSeparator][8] and three [ToolStripButton][9] items by selecting the appropriate type of [ToolStripItem][10] and clicking the Add button.

    2. Set the [Name][11] property of the buttons toLoadButton,SaveButton, andCancelButton, respectively.

    3. Set the [Text][12] property of the buttons toLoad, Save, andCancel.

    4. Set the [DisplayStyle][13] property for each of the buttons toText. Alternatively, you can set this property toImageorImageAndTextand set the image to be displayed in the [Image][14] property.

    5. Click OK to close the dialog box.The buttons are added to the [ToolStrip][3].
	
8. Right-click the form and choose View Code.

9. In the Code Editor, find the line of code that loads data into the table adapter. This code was generated when you set up the data binding in step 2. The code should be similar to the following: TableAdapterName.Fill(DataSetName.TableName). It will most likely be in the form's [Load][15] event.

10. Create an event handler for the [Click][16] event of theLoad[ToolStripButton][9] you created earlier and move this data-loading code into it.

Your code should now look similar to the following:

[Visual Basic]

    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click
        TableAdapterName.Fill(DataSetName.TableName)
    End Sub

[C#]

    private void LoadButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Fill(DataSetName.TableName);
    }

11. Create an event handler for the [Click][16] event of the Save[ToolStripButton][9] you created earlier and write code to update the data within the table the control is bound to.

[Visual Basic]

        Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click
        TableAdapterName.Update(DataSetName.TableName)
    End Sub

[C#]

        private void SaveButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Update(DataSetName.TableName);
    }
	
>In some cases, the [BindingNavigator][2] component will already have aSave button, but no code will have been generated by the Windows Forms Designer. In this case, you can place the preceding code in the [Click][16] event handler for that button, rather than creating an entirely new button on the [ToolStrip][3]. However, the button is disabled by default, so you must set the [Enabled][18] property of the button to true to have the button function correctly.

12. Create an event handler for the [Click][16] event of theCancel[ToolStripButton][9] you created earlier and write code to cancel any changes to the data record that is displayed.

[Visual Basic]

    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click
        BindingSourceName.CancelEdit()
    End Sub

[C#]

    private void CancelButton_Click(System.Object sender, System.EventArgs e)
    {
        BindingSourceName.CancelEdit();
    }

>The [CancelEdit][19] method is scoped to the row of data. Save any changes you make while viewing that individual record before navigating to the next record.

##See Also
###Reference
[BindingSource Component Overview][20]

[BindingNavigator][21]

[BindingSource][22]

[ToolStrip][23]

###Other Resources
[BindingNavigator Control (Windows Forms)][24]

[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
[2]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.bindingnavigator(v=vs.100).aspx
[3]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.toolstrip(v=vs.100).aspx
[4]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.textbox(v=vs.100).aspx
[5]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.bindingsource(v=vs.100).aspx
[6]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.bindingnavigator.bindingsource(v=vs.100).aspx
[7]: https://i-msdn.sec.s-msft.com/dynimg/IC14376.gif "Smart Tag Glyph"
[8]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.toolstripseparator(v=vs.100).aspx
[9]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.toolstripbutton(v=vs.100).aspx
[10]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.toolstripitem(v=vs.100).aspx
[11]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.toolstripitem.name(v=vs.100).aspx
[12]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.toolstripitem.text(v=vs.100).aspx
[13]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.toolstripitem.displaystyle(v=vs.100).aspx
[14]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.toolstripitem.image(v=vs.100).aspx
[15]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.form.load(v=vs.100).aspx
[16]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.toolstripitem.click(v=vs.100).aspx
[17]: https://i-msdn.sec.s-msft.com/dynimg/IC101471.gif "Note"
[18]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.toolbarbutton.enabled(v=vs.100).aspx
[19]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.bindingsource.canceledit(v=vs.100).aspx

[20]: https://msdn.microsoft.com/en-us/library/vstudio/xxxf124e(v=vs.100).aspx
[21]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.bindingnavigator(v=vs.100).aspx
[22]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.bindingsource(v=vs.100).aspx
[23]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.toolstrip(v=vs.100).aspx
[24]: https://msdn.microsoft.com/en-us/library/vstudio/b9y7cz6d(v=vs.100).aspx