<h1> Java's Enum Guide </h1>

```java 

public enum Word {
    POTATO("Pomme de terre"),
    APPLE("Pomme");
    private String equivalent;

    Word(String equivalent) {
        this.equivalent = equivalent;
    }

    @Override
    public String toString(){
        return equivalent;
    }

    public String getEquivalent(){
        return equivalent;
    }
}

```