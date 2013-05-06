# listSort

Just another list drag and sort jQuery plugin that takes into account relative parent positioning, window viewport and support for some callbacks for extended customization.

## Usage:

1. Insert jQuery and the plugin in your document:
   
        <script type='text/javascript' src='jquery.js'></script>
        <script type='text/javascript' src='jquery.list-sort.js'></script>

2. Initialise the plugin:

        <script type='text/javascript'>
         $(function() {
	       $('ul.sort li').listSort();
	     });
        </script>

##  Options:

- **dragElement**: An element within the list element to serve as drag anchor.
- **cloneClass**: CSS class to add to the cloned copy of the element
- **dropClass**: CSS class to add to the element at the location the currently draggeed element can be dropped
- **customClone**: Custom object to use as clone

        <script type='text/javascript'>
         $(function() {
	       $('ul.sort li').listSort(
		     'customClone': function ($obj) {
			   return $('p', $obj).text(); 
			 }
		   );
	     });
        </script>
		
- **onStartDrag**: This will be called before dragging starts.

        <script type='text/javascript'>
         $(function() {
	       $('ul.sort li').listSort(
		     'onStartDrag': function ($draggedElement, event, $elements) {
			   // do somethings
			 }
		   );
	     });
        </script>
		
- **onEndDrag**: This will be called when dragging ends AND a new position is found

		<script type='text/javascript'>
         $(function() {
	       $('ul.sort li').listSort(
		     'onEndDrag': function (order) {
			   var data = $(order).map(function() { return $(this).attr('id'); }).get();
			   console.log(data);
			 }
		   );
	     });
        </script>

