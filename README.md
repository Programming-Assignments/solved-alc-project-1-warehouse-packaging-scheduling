Download Link: https://assignmentchef.com/product/solved-alc-project-1-warehouse-packaging-scheduling
<br>
The 1st ALC project is to develop a software tool for solving the Warehouse Packaging Scheduling problem. In order to solve this problem, students must use solvers for Satisfiability (SAT), Maximum Satisfiability (MaxSAT), Pseudo-Boolean Satisfiability (PBS) or PseudoBoolean Optimization (PBO).

<h1>Problem Specification</h1>

In many online shopping companies, products are stored in warehouses and there is a separate area for packaging of products according to the client’s orders.

Consider the case of a warehouse where they have several people that are <em>runners</em>. The mission of a runner is to pick up products from shelves and put them into conveyor belts. The conveyor belts take the products to the packaging area of the warehouse.

Runners in warehouses are always on the move. Hence, they are not allowed to take breaks (pauses). The timespan of a runner is the time spent from the start until the runner puts the last product in the conveyor belt. In order to be have a sense of justice between runners, a runner cannot spend less than 50% of the maximum timespan of the other runners.

Let <em>P </em>define a set of <em>m </em>products located inside the warehouse in a given shelf. The warehouse operations needs to satisfy a set of <em>n </em>orders {<em>O</em><sub>1</sub><em>,O</em><sub>2</sub><em>…O<sub>n</sub></em>}. Each order <em>O<sub>j </sub></em>is composed

<em>j </em>of <em>k<sub>j </sub></em>products, i.e. <em>O<sub>j</sub></em>such that each product <em>p<sub>i </sub></em>∈ <em>P</em>, 1 ≤ <em>i </em>≤ <em>k<sub>j</sub></em>. In order to satisfy each order, a runner needs to go to the shelf where the product is located and put it into the conveyor belt. This must be done for all products in the order, not necessarily by the same

runner.

Let <em>t<sub>ij </sub></em>be the time a runner takes to go from the location of product <em>p<sub>i </sub></em>to the location of product <em>p<sub>j </sub></em>and put product <em>p<sub>j </sub></em>in the conveyor belt. <a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>

Let <em>c<sub>i </sub></em>be the time product <em>p<sub>i </sub></em>takes in the conveyor belt from its location in the warehouse to the packaging area. Observe that two products cannot arrive at the same time to the packaging

<table width="162">

 <tbody>

  <tr>

   <td width="34"><em>t</em><em>ij</em></td>

   <td width="43"><em>p</em>1</td>

   <td width="32"><em>p</em>2</td>

   <td width="32"><em>p</em>3</td>

   <td width="23"><em>p</em>4</td>

  </tr>

  <tr>

   <td width="34"><em>p</em>1</td>

   <td width="43">1</td>

   <td width="32">5</td>

   <td width="32">3</td>

   <td width="23">3</td>

  </tr>

  <tr>

   <td width="34"><em>p</em>2</td>

   <td width="43">–</td>

   <td width="32">1</td>

   <td width="32">3</td>

   <td width="23">2</td>

  </tr>

  <tr>

   <td width="34"><em>p</em>3</td>

   <td width="43">–</td>

   <td width="32">–</td>

   <td width="32">1</td>

   <td width="23">2</td>

  </tr>

  <tr>

   <td width="34"><em>p</em>4</td>

   <td width="43">–</td>

   <td width="32">–</td>

   <td width="32">–</td>

   <td width="23">1</td>

  </tr>

 </tbody>

</table>

Table 1: Runner’s time between product shelves.

<table width="158">

 <tbody>

  <tr>

   <td width="29"> </td>

   <td width="43"><em>p</em>1</td>

   <td width="32"><em>p</em>2</td>

   <td width="32"><em>p</em>3</td>

   <td width="23"><em>p</em>4</td>

  </tr>

  <tr>

   <td width="29"><em>c<sub>i</sub></em></td>

   <td width="43">3</td>

   <td width="32">1</td>

   <td width="32">3</td>

   <td width="23">2</td>

  </tr>

 </tbody>

</table>

Table 2: Time in conveyor belt for each product.

area. At each time step, you can only have one product arriving to the packaging area in order to allow a proper processing of the product and avoid blockages.

Considering a fixed number of runners, the goal is to determine the sequence of products each runner should put in the conveyor belt such that you minimize the overall timespan of the operations, i.e. the timespan from the initial timestep until the last product arrives at the packaging area.

Consider a problem instance with two runners in the warehouse and that two orders <em>O</em><sub>1 </sub>and <em>O</em><sub>2 </sub>such that <em>O</em><sub>1</sub>={<em>p</em><sub>1</sub><em>,p</em><sub>2</sub><em>,p</em><sub>3</sub>} and <em>O</em><sub>2</sub>={<em>p</em><sub>1</sub><em>,p</em><sub>4</sub>} are to be satisfied. Furthermore, table 1 defines the time a runner takes between product locations in the warehouse and table 2 defines the time a product takes from its location to the packaging area.

Suppose the two runners are initially both located in <em>p</em><sub>1</sub>. In this case, the optimal solution would be as shown in Figure 1. For this example, the optimal solution has a cost of 8 since this is the timestamp that the last product arrives at the packaging area.

Note that all products arrive at the packaging area at different timestamps. No two products can arrive at the same time. Moreover, runners are always on the move with no pauses. Finally, the maximum timespan of the runners is 7 (Runner 1) and all runners have a timespan of at least 50% of the maximum.

<h1>Project Goals</h1>

You are to implement a tool, or optionally a set of tools, invoked with command proj1. This set of tools should use a SAT/MaxSAT/PB solver to compute the warehouse packaging scheduling problem.

Your tool does not take any command-line arguments. The problem instance is to be read from the standard input.

Consider an instance file named job.wps. The tool is expected to be executed as follows:

<table width="265">

 <tbody>

  <tr>

   <td width="38"><em>p</em>1</td>

   <td width="38"><em>p</em>1</td>

   <td width="189"><em>p</em>1 → <em>p</em>2</td>

  </tr>

 </tbody>

</table>

Runner 1

<table width="189">

 <tbody>

  <tr>

   <td width="113"><em>p</em>1 → <em>p</em>3</td>

   <td width="76"><em>p</em>3 → <em>p</em>4</td>

  </tr>

 </tbody>

</table>

Runner 2

<table width="151">

 <tbody>

  <tr>

   <td colspan="2" width="72"><em>p</em>1<sub>1</sub></td>

   <td width="42"> </td>

   <td width="38"> </td>

  </tr>

  <tr>

   <td width="38"> </td>

   <td width="34"> </td>

   <td colspan="2" width="80"><em>p</em>2<sub>1</sub></td>

  </tr>

  <tr>

   <td width="38"></td>

   <td width="34"></td>

   <td width="42"></td>

   <td width="38"></td>

  </tr>

 </tbody>

</table>

Product 1

Product 2                                                                         <em>p</em>1<sub>2</sub>

Product 3                                            <em>p</em>1<sub>3</sub>

Product 4                                                           <em>p</em>2<sub>4</sub>

Time

0        1       2       3        4       5       6        7       8       9

Figure 1: Warehouse Packaging Scheduling Solution

proj1 &lt; job.wps &gt; solution.txt

The tool must write the solution to the standard output, which can then be redirected to a file (e.g., solution.txt).

The programming languages to be used are only C/C++, Java or Python. The formats of the files used by the tool are described below.

<h1>File Formats</h1>

You can assume that all input files follow the description provided in this document. There is no need to check if the input file is correct. Additionally, all lines (input or output) must terminate with the end-of-line character.

<h2>Input Format</h2>

The input file representing a problem instance is a text file that follows the following format:

<ul>

 <li>One line with an integer <em>n</em>(<em>n </em><em>&gt; </em>1) defining the number of runners</li>

 <li>One line with an integer <em>m</em>(<em>m </em>≥ <em>n</em>) defining the number of products</li>

 <li>One line with <em>n </em>integers defining the initial position of each runner</li>

 <li>A sequence of <em>m </em>lines where the <em>i<sup>th </sup></em>line contains <em>m </em>integers describing the times <em>t<sub>ij </sub></em>to go from the location of product <em>i </em>to the location of product <em>j</em>.</li>

 <li>One line with <em>m </em>integers where the <em>i<sup>th </sup></em>integer defines the time product <em>i </em>takes in the conveyor belt to arrive to the packaging area.</li>

 <li>One line with an integer <em>o</em>(<em>o </em><em>&gt; </em>1) defining the number of orders</li>

 <li>A sequence of <em>o </em>lines where the <em>i<sup>th </sup></em>line describes the products of order <em>i</em>. Each line contains the following:

  <ul>

   <li>An integer <em>k<sub>i</sub></em>(<em>k<sub>i </sub></em><em>&gt; </em>0) defining the number of products in order <em>i</em></li>

   <li>A sequence of <em>k<sub>i </sub></em>integers denoting the products in order <em>i</em></li>

  </ul></li>

</ul>

Finally, observe that products are always numbered from 1 to <em>m </em>and that integers in the same line are always separated by a white space.

<h2>Output Format</h2>

Considering the several constraints a solution must satisfy, it is possible that some problem instances do not have a solution. If the problem instance is not satisfiable, then the output of the program is a single line with the word UNSAT. Otherwise, the output representing an optimal solution to the problem instance must comply with the following format:

<ul>

 <li>One line with an integer <em>T </em>defining the optimal timespan for the warehouse scheduling problem</li>

 <li>A sequence of <em>n </em>lines where the <em>i<sup>th </sup></em>line defines the sequence of products handled by runner <em>i </em>as follows:

  <ul>

   <li>An integer <em>k<sub>i </sub></em>denoting the number of products of runner <em>i</em></li>

   <li>A sequence of <em>k<sub>i </sub></em>integers denoting the sequence of products handled by the runner</li>

  </ul></li>

 <li>A sequence of <em>o </em>lines where the <em>j<sup>th </sup></em>line defines the timestamp that each product of order <em>O<sub>j </sub></em>is put on the conveyor belt. Each line is defined as follows:

  <ul>

   <li>An integer <em>k<sub>j </sub></em>denoting the number of products of order <em>O<sub>j</sub></em></li>

   <li>A sequence of pairs of <em>k<sub>j </sub></em>integers where each pair contains the product identifier and the respective timestamp that the product is put on the conveyor belt. The product identifier and the timestamp are separated by the character :.</li>

  </ul></li>

</ul>

Important: The final version to be submitted for evaluation must comply with the described output. Project submissions that do not comply will be severely penalized, since each incorrect output will be considered as a wrong answer. An application that verifies if the output complies with the description will be available on the course’s website.

<h1>Example 1</h1>

The file describing the problem in Table 1 is as follows:

2

4

1 1

1 5 3 3

5 1 3 2

3 3 1 2

3 2 2 1

3 1 3 2

2

3 1 2 3

<ul>

 <li>4 1</li>

</ul>

The optimal solution corresponding to Figure 1 would be:

8

<ul>

 <li>1 1 2</li>

 <li>3 4</li>

 <li>1:1 2:7 3:3</li>

</ul>

2 1:2 4:5

<h1>Example 2</h1>

Consider the following problem instance with 2 runners starting in position of product 1, 2

products and 2 orders as follows:

2

2

1 1

1 10

10 1

2 3

2

2 1 2

1 1

In this case, it is not possible to satisfy the constraint that the timespan of each runner is at least 50% of any other runner. Hence, the output would be:

UNSAT

<h1>Additional Information</h1>

The project is to be implemented in groups of one or two students.

The project is to be submitted through the course website. Jointly with your code, you should submit a short text file describing the main features of your project.

The evaluation will be made taking into account correctness given a reasonable amount of CPU time (80%) and efficiency (20%).

The input and output formats described in this document must be strictly followed.


