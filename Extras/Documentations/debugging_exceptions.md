Exceptions
==========

1
=
**Exception** : IllegalArgumentException, Event-Id should be a positive integer

**Thrower** : EfficientChildViewsClickHandler

**Fix** : Whenever you are registering a child present inside row for EffecientClicking then event-Ids should be positive identifiers for click events.

2
=
**Exception** : IllegalArgumentException, Unable to tag position data to getClass().getSimpleName() in your view-holder object currently only View, java.util.List of Custom-View-Wrappers, Array of Custom-View-wrappers are supported within ViewHolder class if you have custom datastructure within your ViewHolder class consider passing subclass of ViewHolderPositionTagger with your handling in handleCustomDataObject(), and passing that subclass to adapter by overriding getPositionTagger() method in your adapter this class.

**Thrower** : ViewHolderPositionTagger

**Fix** : Whenever you pass a ViewHolder instance, its instance is scanned (by Using Java Reflections) for "View" Object references present inside,This scanning is performed so that it can tag row position value to child views which are registered for efficient clicking, Currently library can only scan few type of objects namely 
 1) Views present directly as member variables in ViewHolder. 
 2) Array of View/View-wrapping-POJOs present as member variables in ViewHolder.
 3) java.util.List of View/View-wrapping-POJOs present as member variables in ViewHolder.
If you pass "Custom objects" within your View Holder then library doesn't know about your custom Objects so it will throw error to fix this error you need to make subclass of ViewHolderPositionTagger & override handleCustomDataObject() method & traverse your custom object to find Objects wrapped in it once Object is recieved call tagObjectIfViewInstanceOrScanObjectForEnclosedViews() method to tag it. Pass this custom class to adapter via overriding getPositionTagger() method.

3
=
**Exception** : IllegalArgumentException, Atleast register 1 RowViewSetter  class

**Thrower** : EasyBaseAdapter

**Fix** : Whenever you are registering a RowViewSetter classes via getListRowViewSetters()/getCursorRowViewSetters() method within your adapter then passing null or empty array in this method results in this crash.

4
=
**Exception** : IllegalStateException, Two different RowViewSetter classes can not have same Row-Type, make sure you pass unique row types in each getRowType() method.

**Thrower** : EasyBaseAdapter

**Fix** : Whenever you are registering a RowViewSetter classes via getListRowViewSetters()/getCursorRowViewSetters() method within your adapter then passing same value in getRowType() method for more than one RowViewSetter results in this crash. Use Enum Values for defining different row types to avoid this kind of exception.

5
=
**Exception** : IllegalArgumentException, Illegal rowtype : #ILLEGAL-VALUE Valid rowTypes are from 0 to #ALLOWED-VALUE both inclusive

**Thrower** : EasyBaseAdapter

**Fix** : Row types should be unique integer values starting from 0 to (number of types of row - 1) Use Enum Values for defining different row types to avoid this kind of exception ie if there are three types of rows supported in your list then correct values for row-types are 0,1,2.

6
=
**Exception** : IllegalStateException, this should only be called when the cursor is valid

**Thrower** : EasyCursorAdapter

**Fix** : this crash is literally very RARE & should never come in practical cases.

7
=
**Exception** : IllegalStateException, couldn't move cursor to position 

**Thrower** : EasyCursorAdapter

**Fix** : this crash is literally very RARE & should never come in practical cases.

8
=
**Exception** : IndexOutOfBoundsException, Position requested #Position Available Cursor size #Total

**Thrower** : EasyCursorAdapter

**Fix** : this crash is when user tries to request #Position of data when its not avaiable in Cursor, for example requesting data for position=100 from a Cursor whose size is less than 100 will result in such crash.

9
=
**Exception** : IndexOutOfBoundsException, Position requested #Position Available list size #Total

**Thrower** : EasyListAdapter

**Fix** : this crash is when user tries to request #Position of data when its not avaiable in list, for example requesting data for position=100 from a list whose size is less than 100 will result in such crash.

