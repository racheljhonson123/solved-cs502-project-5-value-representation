Download Link: https://assignmentchef.com/product/solved-cs502-project-5-value-representation
<br>



Your task in this assignment is to implement a compiler phase for the CPS value representation transformation, including closure conversion. In the skeleton code, you will nd a template for this compiler phase in class <sub>miniscala.CPSValueRepresenter</sub>. You can (and are encouraged to) use the helper methods in class CPSValueRepresenter, CPSTreeModule.Tree, and object BitTwiddling. Please note that the the following aspects will be taken into consideration while grading:

Correctness of the implementation.

The time and memory ef ciency of the implementation.

For instance, transforming a primitive operation <em>x op y</em> by naively decoding the arguments <em>(x,y)</em> and encoding the result back will fetch you fewer points if there exists a better translation that avoids, either completely or partially, some encodings/decodings. Note: To that end, make sure to use left shift (<sub> &lt;&lt; </sub>) and right shift ( &gt;&gt; ) operations to implement multiplication and division by 2 as described in the lectures.

For the closure conversion part, you can choose to implement either the “simple” or the optimized version. Correctly implementing the simpli ed one will give you 90% of the grade for this assignment, whereas a correct implementation of the optimized transformation will give you 110% of the grade. An optimized version that works without supporting recursive/mutually recursive calls will give you 100% (you can still have function calls if they are not recursive). The extra 10% will be given if recursive and mutually recursive function calls can be handled properly.

Notice, however, that by submitting an incorrect version of the optimized transformation you may lose a lot of points depending on the mistakes. Therefore, we recommend that you start by implementing the basic closure conversion procedure and, if you are successful and still have time, to extend it to the optimized procedure.

NOTE: many functions have an implicit argument <strong>worker</strong>. This argument should not be useful in the nonoptimized version, therefore you are free to pass the value <strong>Map.empty</strong> to a function call.

<h2>CPS Low Level</h2>

The value representation phase of the MiniScala compiler takes as input a CPS program where all values and primitives are “high-level,” in that they have the semantics which the MiniScala language gives them. It produces a “low-level” version of that program as output, in which all values are either integers or pointers and primitives correspond directly to instructions of a typical microprocessor.

This means that the primitive operations used in the CPSLow code (de ned in <sub>CPSPrimitives</sub>) are only executing operations on integers (or pointers for block operations). All primitives are performing the operation that you could be expecting based on the name. Note that the CPSByteWrite primitive returns the value 0. You can checkout the <sub>CPSLowInterpreter</sub> in the <strong>CPSInterpreter.scala</strong> le and make sure you understand the CPSLow semantics.

<h2>Testing</h2>

From this assignment on, you will choose the shapes for the trees you generate. You should inspect them visually and decide whether or not they are correct and optimal. The application in the given skeleton code will not have whitebox tests, but it will still have an extensive blackbox test suite to ensure the correctness of the programs you generate.

Although we will not test tree shapes, we still encourage you to do so for every transformation rule you write. You have the necessary infrastructure in miniscala.test.CPSValueRepresentation_Whitebox so it’s a matter of just writing the source code and the resulting tree. It is usually an effort that pays off.

<h2>Road Map</h2>

Spend the time to understand the task that has to be accomplished. This means reading the material and the lectures carefully. A good idea to make sure you understand is to manually transform some piece of code. While doing that, write this as a test case! Two birds, one stone.

Implement the actual value transformation function, keep the closure conversion for last. Test every cases! Of course the best way is to write at least one test case for it, but if you are not willing to write tests then verify that you can generate code that produces a correct result for simple programs. <strong>Do not use</strong> sbt test everytime you add a case to see if you pass more tests! Many of the Blackbox tests will fail unless the closure conversion has been implemented.

Tips:

The implementation can be very technical in some cases, so make sure that you are making good use of the helping function to avoid clustered code!

When creating fresh variable names, you can try to add some information that will help you to debug. For example, when creating a name for the worker of the function “test” you may prefer to use Symbol.fresh(“test_worker”) rather than Symbol.fresh(“w”).

The skeleton code for the assignment is available <a href="https://www.cs.purdue.edu/homes/wang603/cs502/proj5.tar.gz">here.</a>

This assignment relies on the correct implementation of the previous one (the <sub>CMScalaToCPSTranslator </sub>class). If you are con dent that your implementation of <sub>CMScalaToCPSTranslator</sub> is correct, feel free to use your implementation. You are also free to use the reference implementation that is part of the skeleton for Project 5.