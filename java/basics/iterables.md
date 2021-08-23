<h2> Primitive Array </h2>

```java

// Create an Array
int[] list = {1, 2, 3};

// Get the size
list.length
// >> 3

```


<h2> List </h2>

```java 

// Create a list
List<String> firstName = Arrays.asList("James", "Jon");

firstName.get(0);
// >> "James"

firstName.add("Amy");
// >> firstName = ("James", "Jon", "Amy")

firstName.size();
// >> 3

firstName.forEach(System.out::println) // Will print each element
// >> James
// >> Jon

```

<h3> List and primitive array </h3>

```java
int[] primitiveList = {1, 2, 3};
List<Integer> list = Arrays.stream(primitiveList).boxed.toList();
```


<h2> Map </h2>

<h3> Create a Map </h3>

```java

// Create an empty map
Map<String, String> map = new HashMap<>();
map.put("James", "Bond"); // To add a key and a value.
map.get("James"); // To get the value associated to the key.

// Create a map from two lists
List<String> firstName = Arrays.asList("Jon", "James");
List<String> lastName = Arrays.asList("Snow", "Bond");
Map<String, String> names = IntStream.range(0, firstName.size()) // Create a stream of the length of the first List
                                .boxed() 
                                .collect(Collectors.toMap(firstName::get, lastname::get)); // Interate through each index of the first list and returns a Collectors transformed to a Map.
```

