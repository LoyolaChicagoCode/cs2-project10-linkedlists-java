# COMP 271 002 F17 Lab 4 (Week 6)

# Team project

Work in teams of two but run individual JShell sessions and submit individually (see details below)

# Objectives

An understanding of the following concepts and techniques:

- ADT implementation perspective
- dynamically allocated objects
- linked lists
- navigating through linked lists
- iterators
- Java assertions
  
# Instructions

In this lab, you will have the opportunity to look "under the hood" of linked lists by creating and manipulating nodes.
You will do this interactively using the JShell that comes with Java 9.

1. If using c9, remove Java 8 from your workspace:

        sudo apt remove -y oracle-java8-*
        sudo apt-get autoremove
      
1. Install Java 9:

      - Java 9 installation instructions for Ubuntu (applicable to your c9 workspace): http://www.webupd8.org/2015/02/install-oracle-java-9-in-ubuntu-linux.html
      - For Windows and Mac, download and install from here: http://www.oracle.com/technetwork/java/javase/downloads/jdk9-downloads-3848520.html
  
   This is a fairly big download, so it might take a while.

1. Define this generic node class:

       class Node<E> {
         public E data;
         public Node<E> next;
         public Node(final E data, final Node<E> next) { this.data = data; this.next = next; }
         public Node(final E data) { this(data, null); }
       }

1. *Question:* What is the purpose of `E` in this class definition?

1. *Question:* What is the purpose of `this` in the second constructor definition?

1. Create a linked list of nodes containing the strings `"hello"`, `"world"`, `"what"`, and `"up"`. 
Use as many statements as you want.

   Hint: To create a single node, use `new Node<>("abcd")`. 
   The `<>` notation is a placeholder for the specific `E` the system infers for you, in this case, `String`.
   
   Hint: It is best to define named variables for your various objects instead of relying on the auto-generated `$...` names.

1. Now create the same list using a single statement.

1. *Question:* Which way to create the list more clearly conveys the actual structure of the list?

1. Define a method for printing the items in a linked list, starting with the head (first) node:

       <E> void printNode(Node<E> curr) { ... }
  
   Hint: Iterate through the list until `curr` becomes `null`.
   
   Hint: In case your method invocation (or any other code) goes into an infinite loop, you can interrupt execution by pressing Control-c.
   
1. Remove the node containing `"what"` from your list above. 
Use `printNode` to verify that the node is gone from the list.

1. Add the node containing `"what"` back but at the very end of the list. 
Use `printNode` to verify that the node is now in the correct position.

1. Can you create a circular list by making the successor of the list 



# Deliverables and submission

Please submit the following deliverables:

- Individual Sakai submission under "Lab 4":
  - JShell history showing your work for this lab
  - Brief description of your collaboration style and summary of your 
    individual contributions to this team project

# Grading

- 1 submission via GitHub
- 1 tests passing and completion of items marked TODO
- 1 performance testing for increasing problem sizes
- 2 written part
  - 1.5 responses to the questions above
  - 0.5 grammar, style, formatting
- 0.5 (optional) DRY in performance testing 

*5 points TOTAL*

# References

- [JShell overview](https://docs.oracle.com/javase/9/jshell/introduction-jshell.htm)
- [JShell tutorial](http://cr.openjdk.java.net/~rfield/tutorial/JShellTutorial.html)