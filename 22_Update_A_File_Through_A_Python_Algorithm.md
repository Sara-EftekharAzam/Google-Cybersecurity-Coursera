# **Algorithm for File Updates in Python**

## **Project description**

In this project, I developed a Python algorithm to manage and update a file containing a list of IP addresses authorized to access restricted healthcare systems. The goal was to automate the process of removing IP addresses from the allow list when they appear in a separate remove list. This task simulates a real-world scenario in which security professionals must frequently update network access permissions to ensure only authorized personnel have access to sensitive patient information. Using Python’s file-handling capabilities and list manipulation methods, the algorithm reads, modifies, and writes data efficiently and securely.

---

## **Open the file that contains the allow list**

To begin, I defined a variable called `import_file` that stores the name of the file containing the allow list. Then, I used a `with` statement combined with the built-in `open()` function to safely open the file. The `with` statement ensures that the file is automatically closed after the block of code inside it is executed.

**Code:**

```python
import_file = "allow_list.txt"

with open(import_file, "r") as file:
```

**Explanation:**

* `open()` is a Python function used to access files.
* The first argument (`import_file`) specifies the file name, and the second argument (`"r"`) indicates read mode.
* The `with` keyword is used for better file handling—it automatically closes the file after the block finishes executing, preventing potential file corruption or resource leaks.
* The variable `file` temporarily holds the opened file for use within the block.

---

## **Read the file contents**

Inside the `with` block, I used the `.read()` method to read the entire contents of the file and stored it in a variable named `ip_addresses`. This method converts the file content into a single string that can be processed later.

**Code:**

```python
    ip_addresses = file.read()
```

**Explanation:**

* The `.read()` method reads the entire file content as a string.
* The resulting string (`ip_addresses`) contains all the IP addresses from the allow list, which can later be split and manipulated as needed.

---

## **Convert the string into a list**

After reading the data as a string, I converted it into a list format so each IP address could be processed individually. The `.split()` method separates the string by line breaks (`"\n"`), creating a list where each element is an individual IP address.

**Code:**

```python
ip_addresses = ip_addresses.split("\n")
```

**Explanation:**

* The `.split("\n")` method divides the string wherever there is a newline character, effectively creating a list of IP addresses.
* This step makes it easier to search for and remove specific IPs later in the algorithm.

---

## **Iterate through the remove list**

Next, I created a `for` loop to iterate through a second list called `remove_list`, which contains all the IP addresses that need to be deleted from the allow list. The loop variable `element` is used to represent each IP address in the `remove_list` one at a time.

**Code:**

```python
for element in remove_list:
```

**Explanation:**

* The `for` keyword initializes a loop that executes its body once for each element in `remove_list`.
* The variable `element` temporarily holds the current IP address during each iteration.
* This structure makes it possible to compare and remove matching entries from the allow list.

---

## **Remove IP addresses that are on the remove list**

Inside the loop, I added a conditional statement that checks if the current IP address (`element`) from the `remove_list` is present in the `ip_addresses` list. If the condition evaluates to `True`, the `.remove()` method is called to delete it.

**Code:**

```python
    if element in ip_addresses:
        ip_addresses.remove(element)
```

**Explanation:**

* The `if` statement tests for membership using the `in` keyword.
* If the IP address exists in the allow list, `.remove()` deletes it.
* The `.remove()` method is safe to use in this case because the allow list does not contain duplicate IP addresses.
* This ensures that each unwanted IP is removed exactly once.

---

## **Update the file with the revised list of IP addresses**

Finally, I converted the updated list back into a string format and rewrote it to the same file. The `.join()` method was used to combine the elements of `ip_addresses` into a single string, separated by newline characters (`"\n"`). Then, a second `with` statement and the `.write()` method were used to overwrite the existing file with the updated data.

**Code:**

```python
updated_ip_addresses = "\n".join(ip_addresses)

with open(import_file, "w") as file:
    file.write(updated_ip_addresses)
```

**Explanation:**

* The `.join()` method converts a list into a string, using newline characters to preserve the original formatting.
* Opening the file in `"w"` mode allows overwriting the file with new content.
* The `.write()` method writes the string to the file.
* Using `with` again ensures the file is properly closed after writing.

---

## **Summary**

This algorithm demonstrates how to use Python for secure and efficient file manipulation—a key skill in cybersecurity and systems administration. It performs the following tasks:

1. Opens a text file containing an allow list of IP addresses.
2. Reads and converts its contents into a manipulable list.
3. Iterates through a remove list to identify unwanted IPs.
4. Removes any matching IPs from the allow list.
5. Converts the revised list back into a string and writes it to the file.

By applying key Python concepts such as file handling (`open`, `with`), string methods (`.read()`, `.split()`, `.join()`), conditional logic (`if` statements), and list operations (`.remove()`), this algorithm automates the process of maintaining secure access control for a networked environment.
