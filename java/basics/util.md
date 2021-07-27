<h2> Scanner </h2>

```java 

Class main(){

    private static void main(String[] args){

        // To create a scanner
        Scanner scan = new Scanner(System.in)

        // To use the scanner
        String string = scan.nextLine();
        int integer = scan.NextInt();

        // To close a scanner
        scan.close();

        // When closing a scanner, you'll close the "System.in" for good. You won't be able to use Scanner without restarting the programm. 
        // Also, avoid creating several scanner, and prefer using only one and passing it as parameters.
    }

}



```