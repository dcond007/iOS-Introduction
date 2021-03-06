# Tableview Implementation
Learn how to create a table view, and populate it with an array of data.

<img src="https://github.com/dcond007/iOS-Introduction/blob/main/TableViewGIFs/bonusDemo.gif">


### Create a new Xcode project
* Set Interface to Storyboard
* Set Language to Swift
* Save project to your location of choice
<img src="https://github.com/dcond007/iOS-Introduction/blob/main/TableViewGIFs/createAProject.gif">



### Add Objects to Main Storyboard
* Add a TableView
* Add a Cell
  * Place the cell inside the tableview
* Add a Label
  * Place the label inside the cell
<img src="https://github.com/dcond007/iOS-Introduction/blob/main/TableViewGIFs/addObjects.gif">



### Create a new Cell Class
* Right click on the project folder
* Create a new iOS Cocoa Touch Class
* Lets name it: TableViewCell
  * The class type is UITableViewCell
<img src="https://github.com/dcond007/iOS-Introduction/blob/main/TableViewGIFs/createCellClass.gif">



### Configure the Cell and Cell Class
* Go to the Main Storyboard
* Click and highlight the table view cell
* Show the inspectors on the upper right corner
  * Identity Inspector: (license looking icon) fill in the class name, TableViewCell
    * tap enter when done
  * Attributes Inspector: (3 sliders icon) fill in the Reuse Identifier, TableViewCell
    * tap enter when done
* Add an IBOutlet to the TableViewCell class
* Hold down the ALT key and click on the TableViewCell file
  * You'll want the storyboard and TableViewCell class side by side for the next step
* Click and highlight the Label
  * While holding the CONTROL key, click and drag from the Label to the TableViewCell class
  * On the click release, set the connection to an Outlet, and name the new outlet. 
<img src="https://github.com/dcond007/iOS-Introduction/blob/main/TableViewGIFs/configureCellClass.gif">

### Implement TableView Features to our View Controller
* Go to the ViewController file
* Implement the following classes:
  * UITableViewDelegate
  * UITableViewDataSource
* After doing this, some protocols (methods) will be need to be added
  * Click the red icon, and fix the error, two methods are now generated:
    * numberOfRowsInSection
    * cellForRowAt
<img src="https://github.com/dcond007/iOS-Introduction/blob/main/TableViewGIFs/implementClasses.gif">



### Table View Outlet and more
* We can use a handy feature called assistant editor
* Click and highlight the Main storyboard
* Click on the paragraph looking icon, and select the assistant editor
  * the controller associated with the main storyboard is now side by side
* While holding the CONTROL key, click and drag from the table view object to the ViewController class
  * Release the click, create and name the Outlet (example: myTableView)
* Go to the viewDidLoad() method and add the following lines of code:
  * myTableView.dataSource = self
  * myTableView.delegate = self
<img src="https://github.com/dcond007/iOS-Introduction/blob/main/TableViewGIFs/tableViewAndMore.gif">



### Populate the Tableview with data
* Create an array, and give it some values (example: myArray)
* update the numberOfRowsInSection() method
  * This will return myArray.count
* Update the cellForRowAt() method
  * create a cell variable of the TableViewCell class type
  * update the cells label attribute to myArray[indexPath.row]
  * return the cell
``` 
   func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell 
   {
          let myCell = myTableView.dequeueReusableCell(withIdentifier: "TableViewCell") as! TableViewCell
          myCell.myLabel.text = myArray[indexPath.row]
          return myCell
    }
```
``` 
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int 
    {
        return myArray.count
    }
```
<img src="https://github.com/dcond007/iOS-Introduction/blob/main/TableViewGIFs/giveTableViewData.gif">



### I ran the code, but my layout is smooshed.
* Without adding contraints or enabling auto layout, the cells may not render properly
* Add constraints to the Label
<img src="https://github.com/dcond007/iOS-Introduction/blob/main/TableViewGIFs/doesItRun.gif">



### Bonus Feature
* Create a text edit field and a button to add more to the list
* place a check to avoid posting blank items
* Besure to add contraints to all the objects in the View.
``` 
    @IBAction func onPostClick(_ sender: Any) 
    {  
        if (!(myTextField.text!.isEmpty)) {
            myArray.append(myTextField.text!)
            myTableView.reloadData()
        }
    }
```
<img src="https://github.com/dcond007/iOS-Introduction/blob/main/TableViewGIFs/bonus.gif">
