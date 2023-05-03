Download Link: https://assignmentchef.com/product/solved-cs32-homework-1-linked-lists
<br>
<strong><em><u>Homework 1:  Linked Lists </u></em></strong>

Here is a C++ class definition for an abstract data type LinkedList of string objects. Implement each member function in the class below. Some of the functions we may have already done in lecture, that’s fine, try to do those first without looking at your notes. You may add whatever private data members or private member functions you want to this class.

typedef string ItemType;

struct Node {    ItemType value;

Node *next;

};

class LinkedList {    private:       Node *head;    public:

// default constructor

LinkedList();




// copy constructor

LinkedList(const LinkedList&amp; rhs);




// Destroys all the dynamically allocated memory

// in the list.

~LinkedList();




// assignment operator       const LinkedList&amp; operator=(const LinkedList&amp; rhs);




// Inserts val at the front of the list       void insertToFront(const ItemType &amp;val);




// Prints the LinkedList       void printList() const;




// Sets item to the value at position i in this

// LinkedList and return true, returns false if

// there is no element i

bool get(int i, ItemType&amp; item) const;




// Reverses the LinkedList

void reverseList();




// Prints the LinkedList in reverse order       void printReverse() const;




// Appends the values of other onto the end of this

// LinkedList.       void append(const LinkedList &amp;other);




// Exchange the contents of this LinkedList with the other

// one.       void swap(LinkedList &amp;other);




// Returns the number of items in the Linked List.

int size() const;

};




When we don’t want a function to change a parameter representing a value of the type stored in the LinkedList, we pass that parameter by constant reference. Passing it by value would have been perfectly fine for this problem, but we chose the const reference alternative because that will be more suitable after we make some generalizations in a later problem.

The get function enables a client to iterate over all elements of a LinkedList. In other words, this code fragment

LinkedList ls; ls.insertToFront(“Hawkeye”); ls.insertToFront(“Thor”); ls.insertToFront(“Hulk”); ls.insertToFront(“Black Widow”); ls.insertToFront(“Iron Man”); ls.insertToFront(“Captain America”);

for (int k = 0; k &lt; ls.size(); k++)

{    string x;    ls.get(k, x);    cout &lt;&lt; x &lt;&lt; endl;

}

must write

Captain America

Iron Man

Black Widow

Hulk

Thor

Hawkeye




The printList and printReverse functions enables a client to print elements of a LinkedList. In other words, this code fragment

LinkedList ls; ls.insertToFront(“The Mandalorian”); ls.insertToFront(“Baby Yoda”); ls.insertToFront(“Cara Dune”); ls.insertToFront(“Greef Karga”);

ls.printList(); ls.printReverse();

must write

Greef Karga Cara Dune Baby Yoda The Mandalorian

The Mandalorian Baby Yoda Cara Dune Greef Karga




You should have one space between after each item printed with an additional newline after the last item.

Here is an example of the append function:

LinkedList e1; e1.insertToFront(“Athos”); e1.insertToFront(“Porthos”); e1.insertToFront(“Aramis”); LinkedList e2; e2.insertToFront(“Robin”); e2.insertToFront(“Batman”); e1.append(e2);  // adds contents of e2 to the end of e1 string s; assert(e1.size() == 5  &amp;&amp;  e1.get(3, s)  &amp;&amp;  s == “Batman”); assert(e2.size() == 2  &amp;&amp;  e2.get(1, s)  &amp;&amp;  s == “Robin”);




Here is an example of the reverseList function:

LinkedList e1; e1.insertToFront(“Jim”); e1.insertToFront(“Oz”); e1.insertToFront(“Paul”); e1.insertToFront(“Kevin”); e1.reverseList();  // reverses the contents of e1 string s; assert(e1.size() == 4  &amp;&amp;  e1.get(0, s)  &amp;&amp;  s == “Jim”);




Here’s an example of the swap function:

LinkedList e1; e1.insertToFront(“A”); e1.insertToFront(“B”); e1.insertToFront(“C”); e1.insertToFront(“D”); LinkedList e2; e2.insertToFront(“X”); e2.insertToFront(“Y”); e2.insertToFront(“Z”); e1.swap(e2);  // exchange contents of e1 and e2 string s; assert(e1.size() == 3  &amp;&amp;  e1.get(0, s)  &amp;&amp;  s == “Z”); assert(e2.size() == 4  &amp;&amp;  e2.get(2, s)  &amp;&amp;  s == “B”);




When comparing items, just use the == or != operators provided for the string type by the library. These do case-sensitive comparisons, and that’s fine.


