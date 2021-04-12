# Loyola COMP 271 Lab 9: linked lists

## Individual activity

Collaborate with your classmates on a conceptual level but do not share code.
Submit individually.

# Objectives

An understanding of the following concepts and techniques:

- ADT implementation perspective
- dynamically allocated objects
- linked lists
- navigating through linked lists
- iterators
  
# Instructions

In this lab, you will have the opportunity to look "under the hood" of linked lists by creating and manipulating nodes.
You will do this interactively using the JShell that comes with Java 9 and later.

1. Install JShell if you haven't done so per the earlier instructions.

   - On Ubuntu Linux, including Codenvy, go into a terminal window and enter these commands:
   
         sudo apt update
         sudo apt install openjdk-11-jdk

   - On Windows and Mac, download and install the [appropriate Java 11 JDK for your system](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
     This is a fairly big download, so it might take a while.

1. Start the JShell like so:

       jshell -R-ea

   If this does not work, double-check your Java installation.

1. Define this generic node class:

       class Node<E> {
         public E data;
         public Node<E> next;
         public Node(final E data, final Node<E> next) { 
           if (data == null) throw new IllegalArgumentException("data is null");
           this.data = data; 
           this.next = next; 
         }
         public Node(final E data) { this(data, null); }
         public String toString() { 
           return "Node@" + hashCode() + "(" + data + 
             (next != null ? ", Node@" + next.hashCode() + ")" : ")"); 
         }
       }
       
   Hint: If you make a mistake in a class or method definition, don't worry. 
   You can just reenter it to replace the erroneous or incomplete definition.

1. *Question:* What is the purpose of `E` in this class definition?

1. *Question:* What is the purpose of `this` in the second constructor definition?

1. *Question:* What is the purpose of `toString` in this class definition?

1. Create a linked list of nodes containing the strings `"hello"`, `"<YOUR NAME>"`, `"what"`, and `"up"`. 
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

1. Now create a circular list by making the successor of the list refer back to the head of the list.

1. *Question:* What happens if you use the `printNode` method on this circular list?

1. Define an enhanced `printNodeCycle` that works like `printNode` but stops the iteration when it detects a cycle in the list.

1. Invoke `printNodeCycle` on your circular list.

1. *Question:* How would you describe the shape of any noncyclical structure you can build using the `Node` class? 
Furthermore, can you build structures with branches that look like trees, where a node can have more than one successor or neighbor?

1. Write the equivalent of `printNode` using an `Iterator` over a `java.util.LinkedList`?

       final List<String> myList = new LinkedList<>(Arrays.asList("hello", "<YOUR NAME>", "what", "up"));
       final Iterator i = myList.iterator();
       // TODO while loop using i.hasNext() and i.next()

1. *Question:* Would the same code work for an `ArrayList`?

# Deliverables and submission

Please submit the following deliverables:

- Individual Sakai submission under "Lab 9":
  - single gist with JShell history and written part as two separate files (see below for details)
  - brief description of your collaboration style and summary of your 
    individual contributions to this team project

# Grading

- 2.5 JShell history (`jshell> /save -history myhistory.jsh`) showing the steps described above (it's OK if errors are included)
- 1.5 written part
  - 0.2 for each of the six questions
  - 0.3 grammar and style
- 1 submission of both deliverables as part of a single secret [gist](https://gist.github.com/)
  - go to http://gist.github.com and create a new gist by clicking the corresponding button in the top right corner
  - upload your JShell history by dragging it from your desktop into the gist editor
  - choose add file to open another editor and enter your answers there
  - *finally, submit this gist's URL through Sakai*
  - [GitHub gist documentation](https://help.github.com/articles/creating-gists/)

*5 points TOTAL*

# References

- [JShell overview](https://docs.oracle.com/en/java/javase/11/jshell/)
- [JShell tutorial](http://cr.openjdk.java.net/~rfield/tutorial/JShellTutorial.html)