---
layout: post
title:      "Data Structures - Singly Linked Lists"
date:       2019-04-19 22:30:41 -0400
permalink:  data_structures_-_singly_linked_lists
---

 
&nbsp;

A singly linked list consists of many nodes each node contains data and points at the next node. The last node in the list points to null which is how you know you reached the end. The front of the list is the head node.

The following is some Javascript code showing initialization of the LinkedList and Node classes.  

&nbsp; 
 


```

class LinkedList {

  constructor() {
    this.head = null
    this.size = 0
  }


///Other methods here



end



class Node {

  constructor(data, next) {
    this.data = data
    this.next = next
  }

}

``` 

&nbsp;



###### Head Node ---> Node --->  Node ---> Node --->...more nodes... --> null  &nbsp;


&nbsp;


It is a very simple structure. It does not require that nodes are next to each other in memory and because of this is very easy to add and remove from the head of the list. It can be done in constant or O(1) time which is the best possible time complexity.  

&nbsp;

Javascript - add to head and remove from head  

```
  addToHead(data) {
    let node
    if (!!data) {
      node = new Node(data, this.head)
      this.head = node
      this.size += 1
    } else {
      return null
    }
}

  removeFromHead() {
    if (this.size != 0) {
      this.head = this.head.next
      this.size -= 1
    }
}
```
&nbsp;

A downside to this structure is that it is more expensive to search for something in the list or add/remove to the end (instead of th head). Every node has to be iterated through until we accidently run into the node that contains the data we are looking for or until we reach the end or until the next pointer points to null.   

&nbsp;

```
// finds the Node that contains the data. If it doesn't exist returns null
  find(data) {
    let current = this.head
      while (current != null) {
        if (current.data === data) {
          return current
        } else {
          current = current.next
        }
      }
    return null
}



  addToTail(data) {
    let node
    let size = this.size
    let current = this.head

    if (!!data) {

// when list is empty just add to head
      if (current === null) {
        this.addToHead(data)
      } else {

// otherwise find the end of the list and add a Node
        while (size > 0) {

// if size === 1 than it is the last node. Add new Node to end.
          if (size === 1) {
            node = new Node(data, null)
            current.next = node
            this.size += 1
          }
// size is > 1 than decrement size and check the next Node
          current = current.next
          size -= 1
        }
      }
    } else {
      return null
    }
}
```  

&nbsp;

Since we have to traverse the list each time this results in O(n) complexity which is not optimal.  

&nbsp;

Inserting and deleting from the middle of the list is equally as difficult since we have to create our new node and point it to the 'next' node *before* we mode the current node's next to the new node. Else we have no pointer and the list is lost.  

&nbsp;

```
  insertAtIndex(data, index) {
    let node
    let current
    let size = this.size

// check if !!data and if index is within bounds
    if (!!data && index >= size - 1 && index >= 0) {
      current = this.head

// base case if list is empty or if adding to head
      if (current == null && index === 0 || index === size-1) {
        this.addToHead(data)
        return true
      }
// base case when adding to tail
      if (index === 1) {
        this.addToTail(data)
        return true
      }

// find spot before index and insert to next Node
      while (size > index) {
        if (size - 1 === index) {
          node = new Node(data, current.next)
          current.next = node
          this.size += 1
          return true
        }
        current = current.next
        size -= 1
      }

    }
    return false
}
```  

&nbsp;

This is why the structures are often used for Stacks and Queues instead of storing data that needs to be organized in any sort of way. With a Stack we are always manipulating the last thing added because it is a last in first out (LIFO) structure and a Queue is a first in first out (FIFO) data structure. We can talk about those a different day. 

Here's a link to my [JS linked-list code](https://github.com/Rygel-XVI/my-linked-list-js)

