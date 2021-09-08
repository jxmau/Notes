<h1> Java's IO library </h1>

<h2> Files and Directories Management</h2>

<h3> Load a file </h3>

```java 
File file = new File(
    // Will get the path of the home directory.
    System.getProperty("user.home") + File.separator +
    // Get a directory
    "directory" + File.separator +
    // Get a file
    "test.txt";
)

file.exists()
// >> Will return true if it does exist.
```

<h3> How to create a file </h3>

```java 
try {
    String FILE_PATH = System.getProperty("user.home") + File.separator + "test" + File.separator + test.txt;
    FileWriter file = new FileWriter(FILE_PATH);
    // Write something in the file. 
    file.write("hello");
    // Will replace everything in the file
    file.flush();
} catch (IOException e) {
    // Will catch if the directory doesn't exist.
    e.printstack();
}
```

<h3> Create a directory </h3>

```java 
File directory = new File(System.getProperty("user.home") + File.separator + "test");
directory.mkdir();

// Will create several directories in the written path at once.
directory.mkdirs(); 
```

 