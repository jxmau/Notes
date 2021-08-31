<h1> Workflow </h1>

<h2> If - Else If - Else </h2>

```java

public String getWaterState(int degree){

    if ( degree >= 100) {
        return "gas";
    } else if ( degree >= 0) {
        return "liquid";
    } else {
        return "solid";
    }

}
```

Notes : if degree is 101, the "if" and the "else if" will be true, but the program will stop at the first true condition and will return gas.

<h2> Return switch </h2>

```java 
public String getDigitString (int digit) {
    return switch (digit) {
        case 1 -> "one";
        case 2 -> "two";
        case 3 -> "three";
            default -> "N/A";
    };
}

```

<h2> For </h2>

```java
String[] str = "Hello World!".split(" ");

// For object in array loop

for (String string : str) {
    // Will print each index of the array.
    System.out.println(string);
}

// Forward loop - Similar of the "For object in array"
for (int i = 0; i < str.length; i++) {
    System.out.println(str[i]);
}

// Reverse for loop - Will start will the higher index.
for (int i = str.length - 1 ; i >= 0; i--) {
    System.out.println(str[i]);
}
```

<h2> While loop </h2>

```java 

Scanner scan = new Scanner(System.in);

// It will loop until the user enter "exit" in the terminal.
while (scan.nextLine() != "exit") {
    System.out.print("Type a word : ");
}

```