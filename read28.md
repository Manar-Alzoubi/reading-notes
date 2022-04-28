# RecyclerView

### Create dynamic lists with RecyclerView   
* large sets of data can be displayed using RecyclerView
* when defind data define how many time to used, RecyclerView creates libraries when needed
* RecyclerView recycles individual elements, reuses the view for new items that have scrolled onscreen when destroy happened

### Key classes
* to build your dynamic list many classes work together:
    * `RecyclerView` is the `ViewGroup` that contains the views corresponding to your data, It's a view itself
    * `RecyclerView.ViewHolder` defines the view holder, After the view holder is created, the `RecyclerView` binds it to its data.
    * `RecyclerView.Adapter` defines the adapter (by call it's methodes the views can requested or bind)
    * `LayoutManager` abstract class  arranges the individual elements in the list

### Steps for implementing RecyclerView
   * decide what the list or grid is going to look like
   * Design how each element in the list is going to look and behave, extend the `ViewHolder`, the view holder is a wrapper around a `View`, and that view is managed by `RecyclerView`
   * Define the `Adapter` that associates your data with the `ViewHolder` views

### Plan your layout
   * LayoutManager class arranged items in RecyclerView
   * The RecyclerView library provides three layout managers:
        * `LinearLayoutManager` arranges the items in a one-dimensional list
        * `GridLayoutManager`arranges all items in a two-dimensional grid
            *  vertically: elements in each row have the same width and height, different rows can have different heights.
            *  horizontally: elements in each column have the same width and height, different columns can have different widths.
        * `StaggeredGridLayoutManager` the items in a row or column can end up offset from each other


### Implementing adapter and view holder
   * `Adapter` and `ViewHolder` working together to define how data is displayed. 
      * `ViewHolder` is a wrapper around a View that contains the layout for an individual item in the list. 
      *  `Adapter` creates `ViewHolder` objects and sets the data for views.
    * override three key methods:
        * onCreateViewHolder()
        * onBindViewHolder()
        * getItemCount()

