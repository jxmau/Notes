<h2> Primitive Array </h2>

```java
// Create an empty array of a size of 5.
int[] emptyList = new int[5];

// Add an int in the first index of the array
emptyList[0] = 5;

System.out.println(emptyList[0]);
// >> 5


// Create an Array with data
int[] list = {1, 2, 3};

// Get the size
list.length
// >> 3

```


<h2> List </h2>

<h3> Arrays.asList() </h3>

Elements can be replaced, but cannot be added or removed.

```java 

// Create a list
List<String> firstName = Arrays.asList("James", "Jon");

firstName.get(0);
// >> "James"

firstName.replace(0, "Amy")

firstName.size();
// >> 3

firstName.forEach(System.out::println) // Will print each element
// >> Amy
// >> Jon

```

<h4> List and primitive array </h4>

```java
int[] primitiveList = {1, 2, 3};
List<Integer> list = Arrays.stream(primitiveList).boxed.toList();
```

<h3> ArrayList </h3>

```java

// Will create an ArrayList from an Array.
List<Integer> firstList = Arrays.asList(1, 2, 3, 4);
ArrayList<Integer> integers = new ArrayList<>(firstList);

// Will add a element at the end of the Arraylist
integers.add(1);

// Will remove the second element.
integers.remove(1);

// When using a Integer ArrayList, you'll need to specify that you want the Object removal method by using a Wrapper.
// It will remove the first parameter's occurence.
integers.remove((Integer) 1);

```

<h3> Remove if from collection </h3>

```java 

// To remove when isDone() is true.
list.removeIf(Task::isDone);

// To remove when isDone() is false.
list.removeIf(Predicate.not(Task::isDone));

```


<h2> Map </h2>

<h3> Create a Map </h3>


<h4> Empty Map </h4>

```java

Map<String, String> map = new HashMap<>();
map.put("James", "Bond"); // To add a key and a value.
map.get("James"); // To get the value associated to the key.

```

<h4> Map from two lists </h4>

```java

List<String> firstName = Arrays.asList("Jon", "James");
List<String> lastName = Arrays.asList("Snow", "Bond");

// Create a stream of the length of the first List
// You need also to make sure that the List that'll be the KeySet doesn't 
// contains any duplicate or a DuplicateKeyException will be thrown
Map<String, String> names = IntStream.range(0, firstName.size()) 
                                .boxed() 
                                .collect(Collectors.toMap(firstName::get, lastname::get)); // Interate through each index of the first list and returns a Collectors transformed to a Map.

```

Notes regarding IntStreal.range() : When creating a Map from two lists with variable lists' size, you should use the size of the smallest list of avoid an IndexOutOfBoundException by using the method min() of the Math library :

 ```java
IntStream.range(0, Math.min(firstList.size(), secondList.size()));
```

Notes regarding data type for the Map : If you want change the data type when creating the map, you'll need a lambda function. Example for a Int -> String : i -> firstName.get(i).toString().



<h2> Set </h2>

<h3> Create a set </h3>

Note : A Set is a collection with no duplicate element

```java 
    // Will use those lists when creating Sets from different ways.
    List<Integer> firstList = Arrays.asList(1, 2, 3, 4);
    List<Integer> lastList = Arrays.asList(1, 2, 3, 4, 5);


    // Create an empty HashSet
    Set<Integer> set = new HashSet<>();
    set.addAll(firstList); // Will add to the set all firstList's elements.


    // Create a new HashSet from a list
    // It's similar from the previous manner
    Set<Integer> set = new HashSet<>(firstList); 

    // Create an immutable Set
    Set<Integer> set = Set.copyOf(firstList);

    // Create a new HashSet with two lists
    Set<Integer> set = Stream.concat(firstList.stream(), lastList.stream())
        .collect(Collectors.toSet());
```