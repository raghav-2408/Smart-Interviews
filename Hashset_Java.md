# Hashset implementation using Java 
* Insert (put)
* Remove (remove)
* display (get)
```java
public class Main {
    public static void main(String[] args) {
        MyHashMap<String, Integer> hashMap = new MyHashMap<>();

        // Put some key-value pairs
        hashMap.put("one", 1);
        hashMap.put("two", 2);
        hashMap.put("three", 3);

        // Get values by keys
        System.out.println("Value for key 'one': " + hashMap.get("one")); // Output: 1
        System.out.println("Value for key 'four': " + hashMap.get("four")); // Output: null

        // Search for values by keys
        String keyToSearch = "two";
        if (hashMap.containsKey(keyToSearch)) {
            int value = hashMap.get(keyToSearch);
            System.out.println("Value for key '" + keyToSearch + "': " + value);
        } else {
            System.out.println("Key '" + keyToSearch + "' not found");
        }
        // Remove a key-value pair
        hashMap.remove("two");

        // Check if the key was removed
        System.out.println("Value for key 'two' after removal: " + hashMap.get("two")); // Output: null
    }
}
```

# Sum Of Pairs

```java
import java.io.*;
import java.util.*;

public class Main {

    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int t=sc.nextInt();
        for(int p=0;p<t;p++){
        int n=sc.nextInt();
        int key=sc.nextInt();
        int arr[]=new int[n];
        for(int i=0;i<n;i++){
            arr[i]=sc.nextInt();
        }

        HashMap<Integer,Integer> hash=new HashMap<>();
        boolean found=false;
        for(int j=0;j<n;j++){
            int ans=key-arr[j];
            if(hash.containsKey(ans)){
                System.out.println("True");
                found=true;
                break;
            }
            else{
                hash.put(arr[j],j);
            }

        }
        if(!found){
            System.out.println("False");
        }

        
    }
    }
}
```


