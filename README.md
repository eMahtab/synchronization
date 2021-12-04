# Synchronization

```java
public class Main{
  static int counter = 0;
  public static void main(String[] args) {
    Thread t1 = new Thread(new Runnable() {
      public void run() {
        for(int i = 1; i <= 200000; i++) {
         counter++;
        }
      }
    });

    Thread t2 = new Thread(new Runnable() {
      public void run() {
       for(int i = 1; i <= 200000; i++) {
        counter++;
       } 
      }
    });

    t1.start();
    t2.start();
    try {
      t1.join();
      t2.join();
    } catch(InterruptedException exception) {
      exception.printStackTrace();
    }

    System.out.println(counter); // counter value may or may not be 400000
  }
}

```
