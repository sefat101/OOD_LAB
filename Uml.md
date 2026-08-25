// Abstract base class focusing only on essential features
abstract class GarbageBin {
    protected String location;
    protected int capacity;
    protected int currentLevel;

    // Abstract methods: The "what", hiding the "how"
    abstract void collectGarbage();
    abstract boolean isFull();
}

// Child class inheriting from GarbageBin
class SmartGarbageBin extends GarbageBin {
    
    @Override
    void collectGarbage() {
        currentLevel = 0; // Reset after collection
        System.out.println("Garbage collected at " + location);
    }

    @Override
    boolean isFull() {
        return currentLevel >= capacity;
    }
}
