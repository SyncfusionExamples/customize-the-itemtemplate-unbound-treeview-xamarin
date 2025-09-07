# customize-the-itemtemplate-unbound-treeview-xamarin

This repository demonstrates how to customize the item template in an unbound Xamarin.Forms TreeView (SfTreeView) control. It provides a sample implementation that shows how to define and style TreeView nodes directly in XAML without data binding, enabling flexible and visually distinct hierarchical layouts.

## Sample

### XAML
```xaml
<ContentPage.Resources>
        <ResourceDictionary>
            <helper:TextColorConverter x:Key="textColorConverter"/>
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>
    <syncfusion:SfTreeView x:Name="treeView">
        <syncfusion:SfTreeView.ItemTemplate>
            <DataTemplate>
                <Grid>
                    <Label Text="{Binding Content}" TextColor="{Binding Level, Converter={StaticResource textColorConverter}}" VerticalOptions="Center"/>
                </Grid>
            </DataTemplate>
        </syncfusion:SfTreeView.ItemTemplate>

        <syncfusion:SfTreeView.Nodes>
            <treeviewengine:TreeViewNode Content="Australia" IsExpanded="True">
                <treeviewengine:TreeViewNode.ChildNodes>
                    <treeviewengine:TreeViewNode Content="New South Wales">
                        <treeviewengine:TreeViewNode.ChildNodes>
                            <treeviewengine:TreeViewNode Content="Sydney"/>
                            <treeviewengine:TreeViewNode Content="Canberra"/>
                            <treeviewengine:TreeViewNode Content="Newcastle–Maitland"/>
                        </treeviewengine:TreeViewNode.ChildNodes>
                    </treeviewengine:TreeViewNode>
                    <treeviewengine:TreeViewNode Content="Victoria">
                        <treeviewengine:TreeViewNode.ChildNodes>
                            <treeviewengine:TreeViewNode Content="Melbourne"/>
                        </treeviewengine:TreeViewNode.ChildNodes>
                    </treeviewengine:TreeViewNode>
                </treeviewengine:TreeViewNode.ChildNodes>
            </treeviewengine:TreeViewNode>            
        </syncfusion:SfTreeView.Nodes>
    </syncfusion:SfTreeView>
    </StackLayout>
```

### TextColorConverter
```csharp
public class TextColorConverter : IValueConverter
{
    public object Convert(object value, Type targetType, object parameter, CultureInfo culture)
    {
        var level = (int)value;
        if (level == 0) return Color.Red;
        else if (level == 1) return Color.Blue;
        else return Color.Green;
    }

    public object ConvertBack(object value, Type targetType, object parameter, CultureInfo culture)
    {
        throw new NotImplementedException();
    }
}
```

## Requirements to run the demo

To run the demo, refer to [System Requirements for Xamarin](https://help.syncfusion.com/xamarin/system-requirements)

## Troubleshooting
### Path too long exception
If you are facing path too long exception when building this example project, close Visual Studio and rename the repository to short and build the project.
