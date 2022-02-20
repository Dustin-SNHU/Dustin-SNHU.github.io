## Enhanced Artifact: [TooDoo2 Repository](https://github.com/Dustin-SNHU/TooDoo2)<br>

### Description
An enhanced version of the original list making application I created as part of IT-390. Written in Swift with Xcode, this application was developed for an iOS device. Primarily as a way to test my skills by learning a new language, I chose iOS because it is my preferred mobile operating system and used by millions of others.

### Overview
Like my original artifact, the iOS task list application supports functionality to perform CRUD (create, read, update, and delete) functions against a database which hosts a list of tasks that a user manipulates. The database is stored locally by using the UserDefaults local storage that is built into Swift. 

### Development
Creating a brand-new application from scratch came with many challenges. The first hurdle I had to get over was how to get started with development in Xcode. Luckily, I found that the [Apple Developer](https://developer.apple.com) website had some getting started guides. After following a few of these videos to get acclimated with the environment, I found that there were a lot of similarities between this development suite and the tools offered for Android development. The language had similarity to Java, but some syntax did differ. Using the SwiftUI support documentation on Apple’s website, I took notes on important terms and syntax that would be required for the new app. I referenced this site a lot during my development.

After I settled on the application’s name, TooDoo, I created a template file structure and began work. From previous development courses, I did know that I needed to update the code using regular commits to a remote repository. This allowed me to review major changes made over time and also allowed peers and professors to review and iterate on my work. Setting up the connection to GitHub was difficult in the beginning, but once I had it established, committing files became easier and gave me some security knowing that the files would be backed up in case of a local workstation crash.

 After establishing the skeleton of the application, I began working on creating an appealing UI (user interface) and creating the framework for the application’s functionality. Working each week on this app, I soon came to the realization that the database portion of the project would be difficult to create after the framework was done. In the fifth week of the course, I hit a roadblock and I could not figure out how to clean up my code and supply user information into a database array. It was then that I decided to rework the application from the ground up.

This was one of the most stressful parts of the project, but it did pay off. Instead of trying to keep all of the work within the Content View of the application, I created separate view and model folders. Splitting up workloads, it was easier for me to approach the application. I isolated all of the variables that needed to be stored within a single ItemModel Swift file and populated it with the appropriate information.

```swift
// ItemModel Structure
struct ItemModel: Identifiable, Codable { // Make ItemModel structure identifiable and codable
    let id: String // Generate ID String
    let title: String // Initialize title
    let isCompleted: Bool // Initialize boolean value to check for completed tasks
    let description: String // Initilize description
    let date: Date // Initialize date
    
    // Initialize ItemModel Structure
    init(id: String = UUID().uuidString, title: String, isCompleted: Bool, description: String, date: Date) { // Automatically create a unique ID for storing data
        self.id = id
        self.title = title
        self.isCompleted = isCompleted
        self.description = description
        self.date = date

    }
    
    // Update Completed ItemModel
    func updateCompleted() -> ItemModel { // Note: Call function within the ItemModel
        return ItemModel(id: id, title: title, isCompleted: !isCompleted, description: description, date: date)
    }
}
```

The above source code represents the breakdown of the ItemModel structure I created to host the database information. Keeping it all in a single structure would allow me to add, remove, and update the private keys that dictate where the program is at in the database array.

After verifying the database could retrieve information, it was then important to have functions created for manipulating the database.
```swift
// Add item function
func addItem(title: String, description: String, date: Date) {
    let newItem = ItemModel(title: title, isCompleted: false, description: description, date: date) // A new item will be added with title and isCompleted as being false
    items.append(newItem) // Add new item
}
```

```swift
// Delete item function
func deleteItem(indexSet: IndexSet) {
    items.remove(atOffsets: indexSet) // Index where item is deleted from
}
```

The above two examples represent how the application handles the addition and removal of items from the task list. Using the index as the private key, an item is either added or removed from the database.

The final goal of mine was to clean up the user interface and make an application that looks presentable and something you would see on the App Store. I accomplished this by working with the different styles available in SwiftUI. A screen recording of the final product can be viewed below.

<p align="center"><iframe width="560" height="315" src="https://www.youtube.com/embed/o4pGAJIfTDI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe><br>
<i>Artifact 1 - TooDoo2 Demo</i></p>


### Reflection
This project tested my skills, but I believe I have created a product that I can show off to peers and future employers alike. It achieves all the goals I set out to complete in my original proposal for this artifact enhancement. The skills that I obtained with this project and throughout my school career will set me up for future opportunities in the Computer Science field. In addition, I have proven to myself that I can create an application on both iOS and Android platforms. This could lead to side opportunities that I may not have considered in the past.

While the application does complete the goals that I set out, there are still areas where it could be improved. One major topic in the capstone course was regarding security. In today’s landscape it is extremely to make sure that anything developed for a computing device is secure from external risks such as identity theft and ransomware. These security features were not necessarily tested against in my code. Due to time constraints and the entire rework of the project, this is one area that I could not tackle. 

Another what this application could be enhanced is the use of more specific internal application tests. This was neglected due to time constraints as well, but it is an important topic to cover. To test my application, I ran it and verified all the functions worked as I expected. Where this type of testing falls short is in the time it takes and what it covers. An enhancement here could help avoid memory leaks and mishandled inputs. 

This will very unlikely be the last application I develop. I have aspirations of creating personal projects and enhancing my skills for a potential professional career in the field as well.  

<hr style="border:2px solid gray">

**ePortfolio Pages**<br>
[Self-Assessment](https://dustin-snhu.github.io)<br>
[Code Review](https://dustin-snhu.github.io/code_review)<br>
[Original Artifact](https://dustin-snhu.github.io/original_artifact)<br>
[Enhanced Artifact](https://dustin-snhu.github.io/enhanced_artifact)<br>
[Narratives](https://dustin-snhu.github.io/narratives)
