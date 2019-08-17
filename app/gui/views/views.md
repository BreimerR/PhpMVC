# View
A view is a simple page

## Logic

- App selects ViewController from provided url
- ViewController gets data from the database if a model class exists
	- If ModelClass exist in relation the view name
	- The model is called upon and fetches data in relation to the view page requested i.e Home/index
	- The fetched data is stored in a data variable that is to be available in the view it's self 
- ViewController gets its view contents from the defined view directory
	- variables from here are retrieved from the data stored in the ViewController instance data set
	- view is loaded inside app 
	- view is sent to the user
	
#### view retrieval

 A ViewController either gets its items form the directory if the view is a multi paged view else from a single file
 this is to reduce creation of unnecessary directories just having one file i.e index.php files inside them
 
#### View Content
Views are made up of fragments i.e header fragment
Footer fragment
SidePanelFragment
BodyFragment etc 


The base View should be able to call fragments only

The Site view should extend the base view and then set its default loaded views 
for all pages i.e since sites have similar content in some pages i.e CRM's commonly 
static pages differ here as some have different content across all pages i.e blogs

###### NB
```text
Placement of the items on the view is dependant on fragment name as called i.e
// footer containing the html for the section
<?=$footer?>
Or alternatively due to similar name conflicts we can have
<?=$fragment_footer?>
// current use state
<?=$c->fragment("footer")?>
// also viable, simpler syntax also lesser code
<?=$c->fragment->footer?>
``` 

#### Theming
Run time theming is something that is so far hard but look into it
this would mean that html defined will have a constant structure across all
thus the only thing changing is the class naming dependant on the theme
```php
<?php
$app = new App();
$app->theme = new MaterialTheme();
$app->theme = new AdminTheme();
$app->theme = new Theme("user defined theme i.e coloring etc");
```