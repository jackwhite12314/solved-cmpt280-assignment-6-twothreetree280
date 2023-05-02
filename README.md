Download Link: https://assignmentchef.com/product/solved-cmpt280-assignment-6-twothreetree280
<br>



In lib280-asn6 you are provided with a fully functional 2-3 tree class called TwoThreeTree280. Recall that 2-3 trees are keyed dictionaries. As such, the TwoThreeTree280 class implements the KeyedBasicDict280 interface. This interface adds the methods obtain(k), delete(k) and has(k), and set(x) (replace the item whose key matches they key of x with the item x).

Presently, TwoThreeTree280 does not implement KeyedDict280 which adds additional operations including all of the methods in KeyedLinearIterator280 which, in turn, includes all of the public operations on a cursor. Note that KeyedDict280 is the same interface that is implemented by KeyedChainedHashTable280 so you should be somewhat familiar with it from the previous assignment.

The task for this question is to extend the TwoThreeTree280 to a class called IterableTwoThreeTree280 which allows linear iteration over the keyed data items stored in the two-three tree in ascending keyorder. We will achieve this by adding additional references to leaf nodes so that the leaf nodes form a bi-linked list. Note that adding this feature to a 2-3 tree results in exactly a B+ tree of order 3 (see textbook Section 17.1). We aren’t going to call it a B+ tree class though, because we are implementing specifically a B+ tree of order 3, and higher-order B+ trees will not be supported. Our IterableTwoThreeTree280 class will be exactly a B+ tree of order 3.

Figure 1 in the Appendix shows the differences between a 2-3 tree (without iteration) and a B+ tree of order 3 containing the same elements, with the linking of the leaf nodes to support iteration. The algorithms for insertion and deletion are the same in both kinds of tree, except that in the case of the B+ tree, references to/from the predecessor and successor leaf nodes in key-order have to be adjusted to maintain the bi-linked list of leaf nodes.

The full class hierarchy of IterableTwoThreeTree280 is shown in Figure 2 of the Appendix. The hierarchy of tree node classes is shown in Figure 3 of the Appendix.

To implement the IterableTwoThreeTree280, the following tasks must be carried out:

<ol>

 <li>Make an extension of LeafTwoThreeNode280 that adds references to its predecessor and successor leaf nodes. <strong>This has already been done for you in the class </strong></li>

 <li>Override the TwoThreeTree280::createNewLeafNode() method by adding a new protected method in IterableTwoThreeTree280 that it returns a new LinkedLeafTwoThreeNode280 object instead of a TwoThreeNode280 object. <strong>This has already been done for you.</strong></li>

 <li>In IterableTwoThreeTree280, override the insert and delete methods of TwoThreeTree280 with modified versions that correctly maintain the additional predecessor and successor references in the LinkedLeafTwoThreeNode280. Each leaf node should always point to the the leaf node immediately to the left of it (the predecessor) and to the right of it (the successor) even if they are not siblings. Of course, the leaf node with the smallest key has no predecessor and the leaf node with the largest key has no successor.</li>

</ol>

In IterableTwoThreeTree280, the insert and delete methods from TwoThreeTree280 already have been copied, and TODO comments have been inserted indicating where you need to add additional code to maintain the additional leaf node references. The comments also provide a few hints. You should not have to modify any of the existing code for insert or delete, just add new code to deal with the linking and unlinking of leaf nodes from their successors and predecessors. Maintaining these links is very similar to inserting and removing nodes from the middle of a doubly-linked list.

<ol start="4">

 <li>Implement the additional methods required by KeyedDict280 (and, by extension, KeyedLinearIterator280). Some of these have been done for you, others have not. TODO comments in IterableTwoThreeTree280</li>

</ol>

indicate which methods you need to implement and maybe even a hint or two. In this class, the linear iterator allows positioning of the cursor along the leaf-level of the tree.

<ol start="5">

 <li>In the main() function, write a regression test to test the methods required by KeyedDict280 (and, by extension, KeyedLinearIterator280). You to not need to explicitly test the insertion and deletion methods since testing of the methods from KeyedLinearIterator280 will reveal any problems with the new leaf node linkages, but you will need to insert and delete items to create test cases.</li>

</ol>

<strong>You must test all of the methods listed in the interfaces that are coloured blue in Figure 2 of the Appendix.</strong>

Use instances of the local class called Loot, which has been defined in the main method, as the data items to insert into the tree for testing. This class implements the type of item depicted in Figure 1 in the Appendix consisting of the name of a magic item from a fantasy game, and its value in gold pieces. The item keys are the item names (strings).

<em>Hint: The toStringByLevel() method you’ve been given prints not only the 2-3 tree’s structure, but also displays current linear ordering of the nodes that results from following the successor links in the leaf nodes, beginning with the leftmost leaf node. This may be helpful for the debugging of step 2.</em>