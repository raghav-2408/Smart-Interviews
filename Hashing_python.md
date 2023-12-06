# Hash Table Implementation in Python

```python
class HashTable:
    def __init__(self):
        self.size = 10
        self.table = [[] for _ in range(self.size)]

    def _hash(self, x):
        return x % self.size

    def insert(self, x):
        index = self._hash(x)
        self.table[index].append(x)
        print(f"Inserted {x} at index {index}")

    def search(self, x):
        index = self._hash(x)
        if x in self.table[index]:
            print(f"{x} found at index {index}")
            return True
        else:
            print(f"{x} not found in the hash table")
            return False

    def delete(self, x):
        index = self._hash(x)
        bucket = self.table[index]
        if x in bucket:
            bucket.remove(x)
            print(f"Deleted {x} from index {index}")
        else:
            print(f"{x} not found in the hash table")

# Example usage
if __name__ == "__main__":
    hash_table = HashTable()

    hash_table.insert(5)
    hash_table.insert(15)
    hash_table.insert(25)

    hash_table.search(15)
    hash_table.search(10)

    hash_table.delete(15)
    hash_table.search(15)
```

# Explanation

```python
class HashTable:
    def __init__(self):
        self.size = 10
        self.table = [[] for _ in range(self.size)]
```

* xclass HashTable:: Defines a class named HashTable to implement a basic hash table.

* xdef __init__(self):: Constructor method that initializes the hash table with a size of 10 and creates an empty list for each index.

```python
 def _hash(self, x):
        return x % self.size
```
   

* xdef _hash(self, x):: Private helper method _hash for calculating the hash index of a value x.

* xreturn x % self.size: Uses the modulo operator to calculate the hash index.

```python
    def insert(self, x):
        index = self._hash(x)
        self.table[index].append(x)
        print(f"Inserted {x} at index {index}")
```


* def insert(self, x):: Method to insert a value x into the hash table.

* index = self._hash(x): Calculates the hash index using the _hash method.

* self.table[index].append(x): Appends the value x to the list at the calculated index.

* print(f"Inserted {x} at index {index}"): Prints a message indicating the successful insertion.

```python
    def search(self, x):
        index = self._hash(x)
        if x in self.table[index]:
            print(f"{x} found at index {index}")
            return True
        else:
            print(f"{x} not found in the hash table")
            return False
```


* def search(self, x):: Method to search for a value x in the hash table.

* index = self._hash(x): Calculates the hash index using the _hash method.

* if x in self.table[index]:: Checks if the value x is in the list at the calculated index.

* print(f"{x} found at index {index}"): Prints a message if the value is found.

* return True: Returns True to indicate a successful search.

* else:: Executes this block if the value is not found.

* print(f"{x} not found in the hash table"): Prints a message indicating that the value was not found.

* return False: Returns False to indicate an unsuccessful search.

```python
    def delete(self, x):
        index = self._hash(x)
        bucket = self.table[index]
        if x in bucket:
            bucket.remove(x)
            print(f"Deleted {x} from index {index}")
        else:
            print(f"{x} not found in the hash tabl* e")
```


* def delete(self, x):: Method to delete a value x from the hash table.

* index = self._hash(x): Calculates the hash index using the _hash method.

* bucket = self.table[index]: Retrieves the list (bucket) at the calculated index.

* if x in bucket:: Checks if the value x is in the bucket.

* bucket.remove(x): Removes the value from the bucket if found.

* print(f"Deleted {x} from index {index}"): Prints a message indicating the successful deletion.

* else:: Executes this block if the value is not found.

* print(f"{x} not found in the hash table"): Prints a message indicating that the value was not found.


# Example usage
```python
if __name__ == "__main__":
    hash_table = HashTable()

    hash_table.insert(5)
    hash_table.insert(15)
    hash_table.insert(25)

    hash_table.search(15)
    hash_table.search(10)

    hash_table.delete(15)
    hash_table.search(15)
```


* * hash_table = HashTable(): Creates an instance of the HashTable class.

* * hash_table.insert(5): Inserts the value 5 into the hash table.

* * hash_table.insert(15): Inserts the value 15 into the hash table.

* * hash_table.insert(25): Inserts the value 25 into the hash table.

* * hash_table.search(15): Searches for the value 15 in the hash table.

* * hash_table.search(10): Searches for the value 10 in the hash table.

* * hash_table.delete(15): Deletes the value 15 from the hash table.

* * hash_table.search(15): Searches for the value 15 after deletion to show it's not present.

# Hashing (Handling the collision using Linear Probing)
```python
class HashTable:
    def __init__(self):
        self.size = 10
        self.table = [None] * self.size

    def _hash(self, x):
        return x % self.size

    def insert(self, x):
        index = self._hash(x)

        # Linear probing
        while self.table[index] is not None:
            if self.table[index] == x:
                print(f"{x} already exists in the hash table at index {index}")
                return
            index = (index + 1) % self.size

        # If no collision, insert the element
        self.table[index] = x
        print(f"Inserted {x} at index {index}")

    def search(self, x):
        index = self._hash(x)

        # Linear probing for search
        while self.table[index] is not None:
            if self.table[index] == x:
                print(f"{x} found at index {index}")
                return True
            index = (index + 1) % self.size

        print(f"{x} not found in the hash table")
        return False

    def delete(self, x):
        index = self._hash(x)

        # Linear probing for deletion
        while self.table[index] is not None:
            if self.table[index] == x:
                self.table[index] = None
                print(f"Deleted {x} from index {index}")
                return
            index = (index + 1) % self.size

        print(f"{x} not found in the hash table")

```

