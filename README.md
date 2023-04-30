Download Link: https://assignmentchef.com/product/solved-cs235-project-2-roster-is-a-bag-of-students
<br>
In Project2 we will work with the ArrayBag class discussed in lecture 4. This project consists of two parts:

<ol>

 <li>Modify the ArrayBag class</li>

 <li>Implement a class Roster which <u>inherits from </u><u>ArrayBag</u> and stores Student</li>

</ol>

The ArrayBag class (as discussed in lecture) will be distributed via GitHub Classroom.

<strong>First</strong> you <strong>must read the </strong><strong>ArrayBag</strong><strong> interface</strong> and understand how it works. You will need to know how to use ArrayBag objects by understanding its interface.

<u>Note: </u>Reading interfaces will be the way you learn to use language libraries, so this is great practice for that!

<strong>Implementation – 2 parts: </strong>

<strong>Work incrementally!</strong> Start from Part 1 (implement and test), when that runs correctly then move on to Part2.

<strong>Part1- ArrayBag modifications: </strong>

<ol>

 <li>Modify the add method so that it<u> will not allow duplicate items</u> to be added to the ArrayBag (conceptually the Bag becomes a Set). <strong>Hint: </strong>you can use other ArrayBag operations to implement this.</li>

 <li>Implement <u>public</u> method display() to display the contents of the bag to standard output in the form “item1, item2, … , itemN
”</li>

</ol>




/**<strong>@post</strong> prints the contents of items_ to the standard output             separated by commas and followed by a new line.**/      <strong>void</strong><strong> display() </strong><strong>const</strong><strong>;</strong>

<ol start="3">

 <li>Overload <u>public</u> operator+= to implement Set Union. <strong>Hint: </strong>you can use other ArrayBag operations to implement this.</li>

</ol>




/** implements Set Union

The union of two sets A and B is the set of elements which are in A,      in B, or in both A and B.

<strong>@param</strong> a_bag to be combined with the contents of this (the calling) bag

<strong>@post</strong> adds as many items from a_bag as space allows

*/     <strong>void</strong> <strong>operator</strong><strong>+=(</strong><strong>const</strong><strong> ArrayBag&lt;T&gt;&amp; a_bag);</strong>

<strong>Note: </strong>Because ArrayBag is of <u>fixed size</u>, += will only copy as many items from a_bag as there is space available without deleting its original contents. NOTICE HOW FIXED SIZE CAN BE AN ISSUE AND FORCE UNINTUITIVE IMPLEMENTATIONS! We will address the fixed-size problem soon.

<ol start="4">

 <li>Overload <u>public</u> operator-= to implement Set Difference. <strong>Hint: </strong>you can use other ArrayBag operations to implement this.</li>

</ol>




/** implements Set Difference

The (set) difference between two sets A and B is the set that      consists of the elements of A which are not elements of  B      <strong>@param</strong> a_bag to be subtracted from this (the calling) bag

<strong>@post</strong> removes all data from items_ that is also found in a_bag

*/     <strong>void</strong> <strong>operator</strong><strong>-=(</strong><strong>const</strong><strong> ArrayBag&lt;T&gt;&amp; a_bag);</strong>

<strong>IMPORTANT: </strong>Please remember that you DO NOT compile (or include in your project if using an IDE) the implementation (.cpp) of a Template class. Please look at slides 57-59 from Lecture 3 and make sure you understand separate compilation with templates (it will probably help if, as suggested on slide 61, you first run a dummy test and make sure you can compile a simple/trivial template class)

<strong>Part2 –</strong> <strong>Roster class:</strong><strong> </strong>

<strong> </strong>

Write a class, Roster, that <strong>inherits from </strong><strong>ArrayBag</strong> <u>but it is not a template, instead it</u> <u>stores </u><u>Student</u><u> objects</u>. The roster class should have <u>at least</u> the following <u>public</u> <u>methods</u>:

<ol>

 <li><strong>Roster();</strong> //default constructor for empty roster</li>

 <li>/**parameterized constructor</li>

</ol>

<strong>@pre</strong> the input file is expected to be in CSV         (comma separated value) where each line has format:

“id,first_,name_,last_name<strong>
</strong>”

<strong>@param</strong> input_file_name the name of  the input csv file

<strong>@post</strong> Student objects are added to roster as per the data

in the input file      **/

<strong>Roster(</strong><strong>std</strong><strong>::</strong><strong>string</strong><strong> input_file_name);</strong>

<ol start="3">

 <li>/**<strong>@post</strong> displays all students in roster, one per line in the form “first_name_ last_name_<strong>
</strong>“</li>

</ol>

**/     <strong>void</strong><strong> display(); </strong>

In the starter files you will also find the Person class with <strong>overloaded operator== . </strong>This is necessary otherwise you will have a problem when the modified add() methods tries to compare two Student objects to add them to the Roster. <em><u>This</u> <u>statement is not trivial, if you don’t understand please ask!</u></em>




<strong>Testing: </strong>

<strong>Testing your modification to ArrayBag: </strong>

Before you move to part2, YOU MUST  make sure that your modifications to ArrayBag work correctly. To do so write your own main function (not for submission) that does the following:

<ul>

 <li>Instantiate two ArrayBag objects that stores integers</li>

 <li>Add integers to the two bags (some integers should be common to the two bags)</li>

 <li>Call += on one of the bags, display its contents and make sure the operation worked correctly (i.e. bag1∪bag2) and that your modification to add worked s.t. there are no duplicates.</li>

 <li>Call —= on one of the bags, display its contents and make sure the operation worked correctly (i.e. bag1 — bag2).</li>

</ul>

<strong>Testing the Roster class: </strong>

Again in a main function (not for submission) do the following

<ul>

 <li>Instantiate a Roster object with the name of an input file</li>

 <li>Display the roster and make sure that all students in the input file were added to the Roster.</li>

</ul>

<strong>The data: </strong>The input file will be in <strong>csv</strong> (comma separated value) format, and each line corresponds to the information necessary to create a Student object. Each line in the input csv has the following format:

id,fist_name,last_name

A sample input file named roster.csv is available in the distribution repo for GitHub Classroom. <strong>Review — reading the input: </strong>

In C++ to read input from a file you need a file stream

#include &lt;fstream&gt;

Since we are only reading input you can use an ifstream object.

Since we are reading from a csv file, every student is on a line. On each line, each data item is separated by a comma.

You may use string::getline() to read lines from the ifstream. To use getline() you must

#include &lt;string&gt;

You may find it useful to use a stringstream to then read each piece of data (id, first_name and last_name) from each line you read from the input file.

#include &lt;sstream&gt;

You may use getline() to read data from the sstream as well. Remember that getline() may take a delimiter. The default delimiter is ‘
’, but if you are reading comma-separated values you can use ‘,’ as the delimiter. getline(stream, variable, delimiter); Don’t forget to:

<ul>

 <li>Open the stream before reading.</li>

 <li>Check that opening the stream did not fail before reading, and output an error message if it does fail.</li>

 <li>Close the stream after reading.</li>

</ul>

<strong>Note: </strong>Reading from input file should be familiar from CSci 135. If you need to review, lookup ifstream, sstream and string::getline()

References for each of these are easily found online: <a href="http://www.cplusplus.com/reference/fstream/ifstream/">http://www.cplusplus.com/reference/fstream/ifstream/</a><u> </u><a href="http://www.cplusplus.com/reference/sstream/stringstream/">http://www.cplusplus.com/reference/sstream/stringstream/</a><u> </u><a href="http://www.cplusplus.com/reference/string/string/getline/">http://www.cplusplus.com/reference/string/string/getline/</a>

If you need help with this even after having reviewed the documentation, please don’t hesitate to ask for help. After this project you will be expected to be able to read from csv files.