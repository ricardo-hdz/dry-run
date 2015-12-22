### Ricardo Hernandez - Interview Dry-Run

iOS Interview Dry-Run for iOS Nanodegree

######Question 1 - What have you learned recently about iOS development? How did you learn it? Has it changed your approach to building apps?

I have learned that the design process is important or even more important than the actual coding. A thoughtful design process will streamline and drive a successful iOS development. This changed my initial approach when I started doing iOS development: I used to start dragging components into the storyboard and coding right away. Now, I have a systemic approach to research, design, and test ideas and turn them into useful apps.

I gained all this knowledge while working on the final project for my Udacity iOS Nanodegree.

######Question 2 - Can you talk about a framework that you've used recently (Apple or third-party)? What did you like/dislike about the framework?
I recently worked with Facebook’s API and Google Places API. I like the fact that almost any framework offered by a third-paryt is very easy to integrate, its just plug-and-play. On the other side, some of these frameworks do not have updated or useful documentation which makes the development process a bit harder as you need additional research to fill those gaps.

######Question 3 - Describe how you would construct a Twitter feed application (here is an example of Udacity's Twitter feed) that at minimum can display a company's Twitter page. Please include information about any classes/structs that you would use in the app. Which classes/structs would be the model(s), the controller(s), and the view(s)?

For a twitter feed application I’d use the following:

**Controllers**

_ListViewController_: main controller to display and manage cells of tweets, should implement UITableViewDataSource and UITableViewDelegate to handle a table view presentation for all tweets.

_TwitterRequestHelper_: A network helper to interface with ListViewController and manage all network request required to get Twitter data. This will provide an array of Tweet instances it feed the UITableView.

_CoreDataHelper_: A simple helper to interact with core data.

**Models**

_Tweet_: A class to model all data and metadata related to the tweet, e.g. message, link, user, datetime, retweet count, favorite count.

_User_: A class to define a twitter user and its metadata, e.g. display name, username, avatar, followers, tweet, location, description.

_NetworkRequestHelper_: A singleton offering network related utilities to make HTTP requests and parse the response data.

_NetworkConstants_: An struct containing all constants required to make network requests, such as API key, network endpoints, method keys and properties.

**Views**

_TweetCell_: A custom UITableViewCell to display all information of a tweet. The custom tweet cell should implement the following outlets: UIImages, UILabels, UIButtons

_Main Storyboard_: View containing an instance of UITableView, a custom table view cell, activity indicator and UILabels to display messages to the User.

######Question 4 - Describe some techniques that can be used to ensure that a UITableView containing many UITableViewCell is displayed at 60 frames per second.

The first and de-facto solution is that iOS lazy loads each cell and displays only those currently displaying in the view. This is achieved by implementing the delegate’s method dequeueReusableCellWithIdentifier, which reuses an instance of a cell and updates its content with the data located at a specific index.

Another good practice is to load any images requiring network requests inside the dequeueReusableCellWithIdentifier logic, that way the cell is displayed promptly to the user and displayed asynchronously when the data comes back from the service.

######Question 5 - Imagine that you have been given a project that has this ActorViewController. The ActorViewController should be used to display information about an actor. However, to send information to other ViewControllers, it uses NSUserDefaults. Does this make sense to you? How would you send information from one ViewController to another one?

The use of NSUserDefaults is an overkill solution and will impact the performance of the app. Instead of that I will instantiate the destination controller and specify the values for each of the required properties, then we can segue manually and send this controller instance and information using either pushViewController or displayViewController methods of the navigation controller.

######Question 6 - Imagine that you have been given a project that has this GithubProjectViewController. The GithubProjectViewController should be used to display high-level information about a GitHub project. However, it’s also responsible for finding out if there’s network connectivity, connecting to GitHub, parsing the responses and persisting information to disk. It is also one of the biggest classes in the project.

How might you improve the design of this view controller?

I would refactor this controller into the following components:

**Controllers**

_GithubRequestHelper_: A controller to make network requests and to provide the main controller with fully modeled data related to a github project.

_GithubProjectViewController_: This controller will be responsible only for displaying alert views and display updates to the UI.

_NetworkConnectivityHelper_: A class to verify network connectivity status.

**Extensions**

_GithubTable_: An extension for GithubProjectViewController implementing UITableViewDelegate and UITableViewDataSource. This extension will be responsible for stylizing the cell and managing cell interactions for the table view.

_GithubCollection_: An extension for GithubProjectViewController implementing UICollectionViewDelegate, UICollectionViewDataSource. his extension will be responsible for stylizing the cell and managing cell interactions for the collection view.

**Models**

_NetworkRequestHelper_: A low level helper to make HTTP requests and expose various function for data request and parsing. The main consumer would be GithubRequestHelper.

_CoreDataHelper_: A class offering miscellaneous functions for CRUD operations using Core Data.

######Question 7 - If you were to start your iOS developer position today, what would be your goals a year from now?

My goal is to have a profound understanding of iOS development: threading, architecture, software design and performance so I can step up as a mobile leader in any organization and be recognized as an innovator and the person to-go for any mobile development.
