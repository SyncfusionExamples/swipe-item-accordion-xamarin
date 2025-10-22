# swipe-item-accordion-xamarin

This sample demonstrates how to implement swipeable items inside a Syncfusion SfAccordion control for Xamarin.Forms. The project shows a practical pattern where each accordion header uses a Xamarin.Forms `SwipeView` to expose actions when the user swipes the header. 

To learn more about SfAccordion, check out the official user guide topics:

- [Getting Started with Xamarin Accordion (SfAccordion)](https://help.syncfusion.com/xamarin/accordion/getting-started)



## xaml
The accordion is bound to a view-model collection (`Info`) using `BindableLayout.ItemsSource`. Each `AccordionItem` contains a header that is a `SwipeView` with a left swipe `SwipeItem` exposing a "Favourite" action. The content area contains a simple `Label` for the description. 

```
<ContentPage.BindingContext>
    <local:ItemInfoRepository/>
</ContentPage.BindingContext>

<ContentPage.Content>
    <accordion:SfAccordion x:Name="accordion" BindableLayout.ItemsSource="{Binding Info}" ExpandMode="SingleOrNone">
        <BindableLayout.ItemTemplate>
            <DataTemplate>
                <accordion:AccordionItem HeaderBackgroundColor="{Binding HeaderColor}">
                    <accordion:AccordionItem.Header>
                        <SwipeView BackgroundColor="Transparent">
                            <SwipeView.LeftItems>
                                <SwipeItems>
                                    <SwipeItem Text="Favourite" BackgroundColor="#98acf8" Command="{Binding Path=BindingContext.FavouriteCommand, Source={x:Reference accordion}}" CommandParameter="{Binding .}"/>
                                </SwipeItems>
                            </SwipeView.LeftItems>
                            <Grid>
                                <Label TextColor="#495F6E" Text="{Binding Name}" VerticalOptions="Center" HorizontalOptions="Center" HeightRequest="50" VerticalTextAlignment="Center"/>
                            </Grid>
                        </SwipeView>
                    </accordion:AccordionItem.Header>
                    <accordion:AccordionItem.Content>
                        <Grid BackgroundColor="#e8e8e8" Padding="5,0,0,0">
                            <Label Text="{Binding Description}" VerticalOptions="Center"/>
                        </Grid>
                    </accordion:AccordionItem.Content>
                </accordion:AccordionItem>
            </DataTemplate>
        </BindableLayout.ItemTemplate>
    </accordion:SfAccordion>
</ContentPage.Content>
```

## How it works
- SfAccordion: provides a list of expandable items where at most one item is expanded at a time when `ExpandMode="SingleOrNone"` is used.
- SwipeView: placed inside the `AccordionItem.Header` so swipe gestures are handled on the visible header area. Left swipe reveals actions defined in `SwipeItems`.
- Binding to ViewModel: `BindableLayout.ItemsSource` drives item generation. The `DataTemplate` uses item-level bindings (`{Binding Name}`, `{Binding Description}`, `{Binding HeaderColor}`) and also references the outer accordion's `BindingContext` for command bindings via `Source={x:Reference accordion}`.


##### Conclusion
I hope you enjoyed learning about how to use SfAccordion in SwipeView in Xamarin.Forms.

