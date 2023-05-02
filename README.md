Download Link: https://assignmentchef.com/product/solved-comp201-assignment-3
<br>
<span class="kksr-muted">Rate this product</span>

In this asignment, you are expected to find the shortest path between two cities in a given road network using the Floyd-Warshall algorithm.

Each road in this road network connects exactly two cities, and the roads in the network have various lengths. This road network can be considered as an undirected graph since each road can be used in either direction, and has the same length in both directions. Between any two cities, there exist at least one path that connects them, though this path might not be exactly a road that directly connects the two cities.

You can see an example of such a road network.

Wakanda

Mordor

Gondor

London

Tatooine

Narnia

Naboo

Asgard

40

90

60

What is shortest path between Mordor and Narnia, and how long is it?

the answer is:

Mordor – London – Gondor – Narnia Length: 120

1. Program Description

• Your program reads the road network information from a file whose name is provided as a command line argument to your program. The file name is passed to the program

30

70 20

16050

100

Given the road network above, if the question is

1

as follow../your program input file.txt

<ul>

 <li>The input file for your program consists of lines, each of which describes a road that connects any two cities. Each line has three entries, and the entries are separated by blank spaces. The first and second entries are the names of the cities connected by the road, and the third entry shows the length of the road in kilometer.Here is an example of a file that can be an input to your program. This program is based on the figure of road network depicted above.1 2 3 4 5 6 7 8 9</li>

 <li>After reading the input file, the program will prompt its user to enter the names of two cities whose shortest distance and path are to be searched.Program: Enter the cities:User: Mordor NarniaThe names of the cities are separated by a whitespace blank.</li>

 <li>If a shortest path is found between the two cities, the output is printed in two lines. The first line shows the sequence of cities in the path, and the second line displays the length of the path in kilometer. If there are more than one shortest path, any one of them can be a valid output. For the problem in the example, the output is:Mordor London Gondor Narnia 120If it was found that there exists no path, the output is a single line which is as follow. *** NO PATH ***</li>

 <li>To find the shortest path in the problem, you are expected to utilize Floyd-Warshall algorithm. This algorithm finds and calculates the length of the shortest paths be- tween all pairs of vertices in a graph. In your code, this algorithm is executed only once. However, the shortest paths that it finds can be queried repeatedly by a entering city names in the command prompt. The algorithm is used in your code as follow.</li>

</ul>

Mordor London 30 London Tatooine 100 London Gondor 20 London Narnia 160 London Naboo 50 Gondor Narnia 70 Narnia Naboo 90 Naboo Asgard 60 Narnia Wakanda 40

Listing 1: example of input fileThe file will not include the number of lines that it contains.

2

Koc University – COMP201

1

2

3

4

5 6 7 8 9

10 11 12 13 14 15 16 17 18 19 20 21 22 23 24

25 26

27

28 29 30 31 32 33 34 35 36

cities // array of vertices ; each array element contains a city name and its index becomes the city’s numeric id

roads // array of edges; each array element contains the ids of two cities connected directy by a road and the length of the road

city graph // a two−dimensional array that shows the length of the shortest path between any two cities

shortest paths // a two−dimensional array that shows the direction to the shortest path between any two cities

void floydWarshall () {for (int k = 0; k &lt; cities.city count; k++) { for (int i = 0; i &lt; cities.city count; i++) {

for (int j = 0; j &lt; cities.city count; j++) {if ((city graph[i][k] == INF) || (city graph[k][j] == INF)) {

continue ; }

if (city graph[i][j] &gt; (city graph[i][k] + city graph[k][j])) { city graph[i][j] = city graph[i][k] + city graph[k][j]; shortest paths [ i ][ j ] = shortest paths [ i ][k];

}

} }

} }

main(int argc, char *argv[]) {// Allocate memory regions dynamically to cities array and roads array. // Read and parse the input f i l e . Insert the city names and ids to

cities array.// Insert city ids and road lengths to roads array.// Allocate memory regions dynamically to city graph , distance , and

shortest paths arrays .// Initialize the values in city graph array with road lengths , such

that the value in city graph [ i ][ j ] is the road length between cities

i and j if these cities are directly connected by a road. For cities m and n that are not connected directly by a road , the value in

city graph[m][n] will be INF, which is a large value like 10M, that

is assumed to be infinite .

initialise(); floydWarshall () ; while (1) {

// prompt user to enter two city names// print the shortest path between the two cities // print the length of the path

int

}

return 0; }

Listing 2: FloydWarshall Algorithm

• A template code is provided that will help you create your final program. Please read the comments in the template code carefully before working on your code.

3

<ul>

 <li>You are allowed to use ONLY dynamic memory allocation to create any array in the code.</li>

 <li>When a dynamically allocated array is no longer used, the memory regions allocated for it have to be freed.2. Work Instruction</li>

</ul>

<ol>

 <li>Accept the assignment link: https://classroom.github.com/a/g YOXrS3, and open the generated private Github repository.</li>

 <li>Clone the repository locally to your machine or import it to REPL.it.</li>

 <li>Work on the floyd warshall.c template code by modifying the insert to cities, printPath, and main functions to add the missing parts that are necessary to make the code work properly.</li>

 <li>To ensure that your code works correctly, you can use the provided input.txt file as an input to your program, and compare your output with the content of the expected-output.txt file. In the expected-output.txt file, there is a list of in- puts and outputs that your code is supposed to produce when the input file is the input.txt file.</li>

 <li>To ensure that all dynamically allocated memory regions have been freed by the end of your code, you can use Valgrind to check if there is still unfreed allocated memory.</li>

 <li>After you finish working on your code, commit and push your code to your repository.</li>

</ol>

3. Evauation Criteria

You will be graded out of 50 maximal points. The total grade comprises the following criteria.

<ul>

 <li>25 points for code correctnessThis criterion covers correctness of printed output, and the code being free from syntax errors, segmentation faults, stack smashing, infinite loop/recursion, and other logical errors. Please make sure that your code can handle input files that have much higher number of cities and roads than the provided input.txt file.</li>

 <li>10 points for using only dynamic memory allocations for creating arraysYou must not declare arrays statically such as ”int array1[100]”, but, instead, use functions like malloc, calloc, and realloc in allocating memory regions for the arrays in your code.</li>

 <li>10 points for freeing all dynamically allocated memory before the end of your code</li>

 <li>5 points for coding style and comments</li>

</ul>

4

Koc University – COMP201

4. Oral Assessment