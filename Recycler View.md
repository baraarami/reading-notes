# Read: 28 - RecyclerView

## [](https://developer.android.com/guide/topics/ui/layout/recyclerview#java)

**Create dynamic lists with RecyclerView**
  * RecyclerView makes it easy to efficiently display large sets of data. You supply the data and define how each item looks, and the RecyclerView library dynamically creates the elements when they're needed.
  * RecyclerView recycles those individual elements, and is also the name of the library. When an item scrolls off the screen, RecyclerView doesn't destroy its view. Instead, RecyclerView reuses the view for new items that have scrolled onscreen. This vastly improves performance, improving your app's responsiveness, and reducing power consumption.
  * Key classes: 
    - RecyclerView - the ViewGroup that contains the views corresponding to your data. 
    -  RecyclerView.ViewHolder - Each individual element in the list is defined by a view holder object, and after the view holder is created, the RecyclerView binds it to its data. 
    -  RecyclerView.Adapter - RecyclerView requests those views, and binds the views to their data, by calling methods in the adapter. 
    -  LayoutManager - arranges the individual elements in your list. 
  * Plan your layout:
    - Items in your RecyclerView are arranged by a LayoutManager class. The RecyclerView library provides three layout managers: 
      * LinearLayoutManager arranges the items in a one-dimensional list
      * GridLayoutManager arranges all items in a two-dimensional grid
      * StaggeredGridLayoutManager is similar to GridLayoutManager, but it does not require that items in a row have the same height or items in the same column have the same width. The result is that the items in a row or column can end up offset from each other.
  * Implementing your adapter and view holder:
    - Adapter and ViewHolder classes work together to define how your data is displayed.
    - The ViewHolder is a wrapper around a View that contains the layout for an individual item in the list.
    - The Adapter creates ViewHolder objects as needed, and also sets the data for those views. 
    - When you define your adapter, you need to override three key methods: 
      * onCreateViewHolder() - RecyclerView calls this method whenever it needs to create a new ViewHolder. 
      * onBindViewHolder() - RecyclerView calls this method to associate a ViewHolder with data. 
      * getItemCount() - RecyclerView calls this method to get the size of the data set. 


#  RecyclerView
![](https://miro.medium.com/max/2686/1*OB895Pqa7AQkPLSScRfsYQ.png)
- What is a RecyclerView in Android?
  - ***The RecyclerView***  is a widget that is more flexible and advanced version of GridView and ListView. It is a container for displaying large datasets which can be scrolled efficiently by maintaining limited number of views. 
  - It is a library which use to creates dynamic the elements when they are needed. RecyclerView recycles it's individual elements, when you scroll down RecyclerView doesn't destroy its view, it is reusing it for a different element.
- How does RecyclerView work?
  - `RecyclerView` does not allocate an item view for every item in your data source. Instead, it allocates only the number of item views that fit on the screen(Viewport) and it reuses those item layouts as the user scrolls. ... When a view scrolls out of sight and is no longer displayed, it becomes a scrap view .
##### Key classes
- `RecyclerView` is the `ViewGroup` that contains the views corresponding to your data 
- Each individual element in the list is defined by a view holder object.You define the view holder by extending `RecyclerView.ViewHolder`.
- The `RecyclerView` requests those views, and binds the views to their data, by calling methods in the adapter. You define the adapter by extending `RecyclerView.Adapter`.
- The layout manager arranges the individual elements in your list.Layout managers are all based on the library's `LayoutManager` abstract class.

#### Implementing your adapter and view holder
- `onCreateViewHolder()`: RecyclerView calls this method whenever it needs to create a new ViewHolder. The method creates and initializes the ViewHolder and its associated View, but does not fill in the view's contents—the ViewHolder has not yet been bound to specific data.

- `onBindViewHolder()`: RecyclerView calls this method to associate a ViewHolder with data. The method fetches the appropriate data and uses the data to fill in the view holder's layout. For example, if the RecyclerView dislays a list of names, the method might find the appropriate name in the list and fill in the view holder's TextView widget.

- `getItemCount()`: RecyclerView calls this method to get the size of the data set. For example, in an address book app, this might be the total number of addresses. RecyclerView uses this to determine when there are no more items that can be displayed.
#### CODE EXAMPLE :
```

public class CustomAdapter extends RecyclerView.Adapter<CustomAdapter.ViewHolder> {

    private String[] localDataSet;

    /**
     * Provide a reference to the type of views that you are using
     * (custom ViewHolder).
     */
    public static class ViewHolder extends RecyclerView.ViewHolder {
        private final TextView textView;

        public ViewHolder(View view) {
            super(view);
            // Define click listener for the ViewHolder's View

            textView = (TextView) view.findViewById(R.id.textView);
        }

        public TextView getTextView() {
            return textView;
        }
    }

    /**
     * Initialize the dataset of the Adapter.
     *
     * @param dataSet String[] containing the data to populate views to be used
     * by RecyclerView.
     */
    public CustomAdapter(String[] dataSet) {
        localDataSet = dataSet;
    }

    // Create new views (invoked by the layout manager)
    @Override
    public ViewHolder onCreateViewHolder(ViewGroup viewGroup, int viewType) {
        // Create a new view, which defines the UI of the list item
        View view = LayoutInflater.from(viewGroup.getContext())
                .inflate(R.layout.text_row_item, viewGroup, false);

        return new ViewHolder(view);
    }

    // Replace the contents of a view (invoked by the layout manager)
    @Override
    public void onBindViewHolder(ViewHolder viewHolder, final int position) {

        // Get element from your dataset at this position and replace the
        // contents of the view with that element
        viewHolder.getTextView().setText(localDataSet[position]);
    }

    // Return the size of your dataset (invoked by the layout manager)
    @Override
    public int getItemCount() {
        return localDataSet.length;
    }
}
```
#### The layout for the each view item
```
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="@dimen/list_item_height"
    android:layout_marginLeft="@dimen/margin_medium"
    android:layout_marginRight="@dimen/margin_medium"
    android:gravity="center_vertical">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/element_text"/>
</FrameLayout>
```
