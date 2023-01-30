# Coachable First Assignment – DMITRY ULASAU
## 1. Runtime Analysis
### *Give the order of growth (as a function of N) of the running times of each of the following code fragments:*

#### # Block ( a ) 
```python
sum = 0
n = N
while n > 0: 
    for i in range(0, n):
        sum += 1
    n = n // 2
```

``start
``

>**n = N = 5**
>
>for loop [0 ... 4] - (inner loop)
>
>1st -> sum = 1 [0]
>
>2nd -> sum = 2 [1]
>
>3rd -> sum = 3 [2] 
>
>4th -> sum = 4 [3]
>
>5th -> sum = 5 [4]

>**n // 2 = 5 // 2 = 2**
>
>for loop [0 ... 1] - (inner loop)
>
>6th -> sum = 6 [0]
>
>7th -> sum = 7 [1]

>**n // 2 = 2 // 2 = 1**
>
>for loop [0 ... 0] - (inner loop)
>
>8th -> sum = 8 [0]

``
end
``
> In this case the iterations of the inner loop depend on the outer loop, it's better to sum over the amount of iterations of the inner loop.
> Value **(n)** for the while loop is fixed, the work done of the inner loop is **(n)**.
>
>Iterations: N, N/2, N/4, N/8, ... N / N
>
>N(1 + 1/2 + 1/4 + 1/8 + ... 1/N) will never be greater 2N
>
>O(N) - LINEAR


#### # Block ( b ) 
```python
sum = 0
i = 1
while i < N:
    for j in range(0, i):
        sum += 1
    i = i * 2
```

``start
``

>**N = 5, i = 1**
>
>for loop [0 ... 0] (inner loop)
>
>1st -> sum = 1 [0]

>**N = 5, i = 2**
>
>for loop [0 ... 1] (inner loop)
>
>2nd -> sum = 2 [0]
>
>3rd -> sum = 3 [1]

>**N = 5, i = 4**
>
>for loop [0 ... 3] (inner loop)
>
>4th -> sum = 4 [0]
>
>5th -> sum = 5 [1]
>
>6th -> sum = 6 [2]
>
>7th -> sum = 7 [3]

``end
``

> While the while loop's value **(i)** is fixed, the inner loop's work is represented by **(i)**
>
>OUTER while loop: i => 1, 2, 4, 8, ...
>
>INNER for loop: j => (0 ... 0), (0 ... 1), (0 ... 3), (0 ... 7), ...
>
>N(1 + 2 + 4 + 8 + ...)
>
>O(N) - LINEAR

#### # Block ( c ) 
```python
sum = 0
i = 1
while i < N:
    for j in range(0, N):
        sum += 1
    i = i * 2
```

``start
``
>**N = 4, i = 1**
>
>for loop 0 ... 3 (inner loop)
>
>1st -> sum = 1 [0] 
>
>2nd -> sum = 2 [1]
>
>3rd -> sum = 3 [2]
>
>4th -> sum = 4 [3]

>**N = 4, i = 2**
>
>for loop 0 ... 3 (inner loop)
>
>5th -> sum = 5 [0]
>
>6th -> sum = 6 [1]
>
>7th -> sum = 7 [2]
>
>8th -> sum = 8 [3]

``end
``

> The work completed by the inner loop is **(N)** regardless of the value of the while loop **(i)**
>
>OUTER while loop: i => 1, 2, 4, 8, ...
>
>INNER for loop: N = 4 i => count(i) = 2
>
>ORDER OF GROWTH O(log(N)) * N = O(N log (N))
>
>O(N log (N)) - logarithmic


&nbsp;
## Selection/Insertion Sort
1. Show in the style of the example trace with selection sort, how selection sort sorts the array

> current - (), minimum - []
>
>**(E)** **[A]** S Y Q U E S T I O N 
>
>A **(E)** S Y Q U **[E]** S T I O N
>
>A E **(S)** Y Q U **[E]** S T I O N
>
>A E E **(Y)** Q U S S T **[I]** O N
>
>A E E I **(Q)** U S S T Y O **[N]**
>
>A E E I N **(U)** S S T Y **[O]** Q
>
>A E E I N O **(S)** S T Y U **[Q]**
>
>A E E I N O Q **(S**) T Y U **[S]**
>
>A E E I N O Q S **(T)** Y U **[S]**
>
>A E E I N O Q S S **(Y)** U **[T]**
>
>A E E I N O Q S S T **(U)** Y

2. What is the maximum number of exchanges involving any particular item during selection sort? E A S Y Q U E S T I O N

> n - 1 = 12 - 1 = 11

3. Show in the style of the example trace with insertion sort, how insertion sort sorts the array E A S Y Q U E S T I O N

>[**E** **A** S Y Q U E S T I O N] - **[0]**
>
>**A < E**
>
>**E <- SWAP -> A**
>
>(**A**) (**E**) S Y Q U E S T I O N

>[A **E** **S** Y Q U E S T I O N] - **[1]**
>
>**S > E**

>[A E **S** **Y** Q U E S T I O N] - **[2]**
>
>**Y > S**

>[A E S **Y** **Q** U E S T I O N] - **[3]**
>
> **Q < Y**
>
>**Y <- SWAP -> Q**
>
>A E S (Q) (Y) U E S T I O N
>
>**S <- SWAP -> Q**
>
>A E (Q) (S) Y U E S T I O N

>[A E Q S **Y** **U** E S T I O N] - **[4]**
>
>**U < Y**
>
>**Y <- SWAP -> U**
>
>A E Q S (U) (Y) E S T I O N

>[A E Q S U **Y** **E** S T I O N] - **[5]**
>
>**E < Y**
>
>**Y <- SWAP -> E**
>
>A E Q S U (E) (Y) S T I O N
>
>**U <- SWAP -> E**
>
>A E Q S (E) (U) Y S T I O N
>
>**S <- SWAP -> E**
>
>A E Q E (S) (U) Y S T I O N
>
>**Q <- SWAP -> E**
>
>A E (E) (Q) S U Y S T I O N

>[A E E Q S U **Y** **S** T I O N] - **[6]**
>
>**S < Y**
>
>**Y <- SWAP -> S**
>
>A E E Q S U (S) (Y) T I O N
>
>**U <- SWAP -> S**
>
>A E E Q S (S) (U) Y T I O N

>[A E E Q S S U **Y** **T** I O N] - **[7]**
>
>**T < Y**
>
>**Y <- SWAP -> T**
>
>A E E Q S S U (T) (Y) I O N
>
>**U <- SWAP -> T**
>
>A E E Q S S (T) (U) Y I O N

>[A E E Q S S T U **Y** **I** O N] - **[8]**
>
>**I < Y**
>
>**Y <- SWAP -> I**
>
>A E E Q S S T U (I) (Y) O N
>
>**U <- SWAP -> I**
>
>A E E Q S S T (I) (U) Y O N
>
>**T <- SWAP -> I**
>
>A E E Q S S (I) (T) U Y O N
>
>**S <- SWAP -> I**
>
>A E E Q S (I) (S) T U Y O N
>
>**S <- SWAP -> I**
>
>A E E Q (I) (S) S T U Y O N
>
>**Q <- SWAP -> I**
>
>A E E (I) (Q) S S T U Y O N

>[A E E I Q S S T U **Y** **O** N] - **[9]**
>
>**O < Y**
>
>**Y <- SWAP -> O**
>
>A E E I Q S S T U (O) (Y) N
>
>**U <- SWAP -> O**
>
>A E E I Q S S T (O) (U) Y N
>
>**T <- SWAP -> O**
>
>A E E I Q S S (O) (T) U Y N
>
>**S <- SWAP -> O**
>
>A E E I Q S (O) (S) T U Y N
>
>**S <- SWAP -> O**
>
>A E E I Q (O) (S) S T U Y N
>
>**Q <- SWAP -> O**
>
>A E E I (O) (Q) S S T U Y N

>[A E E I (O) (Q) S S T U **Y** **N**] - **[10]**
>
>**N < Y**
>
>**Y <- SWAP -> N**
>
>A E E I O Q S S T U (N) (Y)
>
>**U <- SWAP -> N**
>
>A E E I O Q S S T (N) (U) Y
>
>**T <- SWAP -> N**
>
>A E E I O Q S S (N) (T) U Y
>
>**S <- SWAP -> N**
>
>A E E I O Q S (N) (S) T U Y
>
>**S <- SWAP -> N**
>
>A E E I O Q (N) (S) S T U Y
>
>**Q <- SWAP -> N**
>
>A E E I O (N) (Q) S S T U Y
>
>**O <- SWAP -> N**
>
>A E E I (N) (O) Q S S T U Y

>**[A E E I N O Q S S T U Y]**

4. Which method runs fastest for an array with all keys identical, selection sort or insertion sort?

> Insertion sort runs faster for an array with all keys identical (array already sorted)
Insertion sort is linear (checks every element to adjacent one).
Selection sort - quadratic time.

4. **Expensive exchange.** A clerk at a shipping company is charged with the task of rearranging a number of large crates in order of the time they are to be shipped out. Thus, the cost of compares is very low (just look at the labels) relative to the cost of exchanges (move the crates). The warehouse is nearly full: there is extra space sufficient to hold any one of the crates, but not two. Which sorting method should the clerk use?

> Selection sort - because we can compare all crates (the cost of compares is very low) and move needed one.

&nbsp;
## Mergesort
1. Describe in words why mergesort is a stable sort.
> Two objects with equal keys appear in the same order in sorted output as they appear in the input array to be sorted.

2. Give traces, in the style of the trace given in this section, showing how the keys E A S Y Q U E S T I O N  are sorted with top-down mergesort and with bottom-up mergesort.
> The top-down approach: Given an array of size N, the algorithm recursively breaks the array in half and then merges the results together.
>
>E A S Y Q U E S T I O N
>
>[E A S Y Q U] **|** [E S T I O N]
>
>[E A S ] **|**  [Y Q U] **|**  [E S T] **|**  [I O N]
>
>[E A] **|** [S] **|**  [Y Q] **|** [U] **|** [E S] **|** [T] **|**  [I O] **|** [N]
>
>[E] **|**  [A] **|** [S] **|**  [Y] **|**  [Q] **|** [U] **|** [E] **|**  [S] **|** [T] **|** [I] **|** [O] **|** [N]
>
>[A E] **|** [S] **|** [Q Y] **|** [U] **|** [E S] **|** [T] **|** [I O] **|** [N]
>
>[A E S] **|** [Q U Y] **|** [E S T] **|** [I N O]
>
>[A E Q S U Y] **|** [E I N O S T]
>
>[A E E I N O Q S S T U Y]

> Bottom-Up: The iterative part is based on the idea that a one item array is already sorted, so if we have a specific array we can treat each element in it as a sorted array, then apply the merge as usual. Treat each item as a logical array.
>
>E A S Y Q U E S T I O N
>
>[E] **|** [A] **|** [S] **|** [Y] **|** [Q] **|** [U] **|** [E] **|** [S] **|** [T] **|** [I] **|** [O] **|** [N]
>
>[A E] **|** [S Y] **|** [Q U] **|** [E S] **|** [I T] **|** [N O]
>
>[A E S Y] **|** [E Q S U] **|** [I N O T]
>
>[A E E Q S S U Y] **|** [I N O T]
>
>[A E E I N O Q S S T U Y]

&nbsp;
## Quicksort

1. Show, in the style of the trace given with partition(), how that method partitions the array E A S Y Q U E S T I O N.
> () - pivot
>
> [E A S Y Q U E S T I O **(N)**]
>
> [**E** A S Y Q U E S T I O **(N)**] - E < N ? true
>
> [E **A** S Y Q U E S T I O **(N)**] - A < N ? true
>
> [E A **S** Y Q U E S T I O **(N)**] - S < N ? false
>
> [E A S **Y** Q U E S T I O **(N)**] - Y < N ? false
>
> [E A S Y **Q** U E S T I O **(N)**] - Q < N ? false
>
> [E A S Y Q **U** E S T I O **(N)**] - U < N ? false
>
> [E A S Y Q U **E** S T I O **(N)**] - E < N ? true
>
> [E A <**E**> Y Q U <**S**> S T I O **(N)**] - **SWAP**
>
> [E A E Y Q U S **S** T I O **(N)**] - S < N ? false
>
> [E A E Y Q U S S **T** I O **(N)**] - T < N ? false
>
> [E A E Y Q U S S T **I** O **(N)**] - I < N ? true
>
> [E A E <**I**> Q U S S T <**Y**> O **(N)**]  - **SWAP**
>
> [E A E I Q U S S T Y **O** **(N)**] - O < N ? false
>
> [E A E I <**N**> U S S T Y O <**Q**>] - **SWAP**

> [E A E I] | [N] | [U S S T Y O Q]

2. Show, in the style of the quicksort trace, how quicksort sorts the array E A S Y Q U E S T I O N. (For the purposes of this exercise, ignore the initial shuffle.)
> () - pivot
>
> [E A S Y Q U E S T I O **(N)**]
>
> [**E** A S Y Q U E S T I O **(N)**] - E < N ? true
>
> [E **A** S Y Q U E S T I O **(N)**] - A < N ? true
>
> [E A **S** Y Q U E S T I O **(N)**] - S < N ? false
>
> [E A S **Y** Q U E S T I O **(N)**] - Y < N ? false
>
> [E A S Y **Q** U E S T I O **(N)**] - Q < N ? false
>
> [E A S Y Q **U** E S T I O **(N)**] - U < N ? false
>
> [E A S Y Q U **E** S T I O **(N)**] - E < N ? true
>
> [E A <**E**> Y Q U <**S**> S T I O **(N)**] **SWAP**
>
> [E A E Y Q U S **S** T I O **(N)**] - S < N ? false
>
> [E A E Y Q U S S **T** I O **(N)**] - T < N ? false
>
> [E A E Y Q U S S T **I** O **(N)**] - I < N ? true
>
> [E A E <**I**> Q U S S T <**Y**> O **(N)**]  **SWAP**
>
> [E A E I Q U S S T Y **O** **(N)**] - O < N ? false
>
> [E A E I <**N**> U S S T Y O <**Q**>] - **SWAP**

> **[E A E I] | [N] | [U S S T Y O Q]**

> [E A E **(I)**]
>
> [**E** A E **(I)**] E < I true
>
> [E **A** E **(I)**] A < I true
>
> [E A **E** **(I)**] A < I true
>
> [**E** A **(E)**] E < E false
>
> [E **A** **(E)**] A < E true
>
> [<**A**> <**E**> **(E)**] **SWAP**

>**[A E E I N]**

> [U S S T Y O **(Q)**]
>
> [**U** S S T Y O **(Q)**] U < Q false
>
> [U **S** S T Y O **(Q)**] S < Q false
>
> [U S **S** T Y O **(Q)**] S < Q false
>
> [U S S **T** Y O **(Q)**] T < Q false
>
> [U S S T **Y** O **(Q)**] Y < Q false
>
> [U S S T Y **O** **(Q)**] O < Q true
>
> [<**O**> S S T Y <**U**> **(Q)**] **SWAP**
>
> [O <**Q**> S T Y U <**S**>] **SWAP**

> **[A E E I N O Q]**

>[S T Y U **(S)**]
>
>[**S** T Y U **(S)**] - S < S ? false
>
>[S **T** Y U **(S)**] - T < S ? false
>
>[S T **Y** U **(S)**] - Y < S ? false
>
>[S T Y **U** **(S)**] - U < S ? false
>
>[S <**S**> Y U <**T**>] - **SWAP**

>**[ A E E I N O Q S S]**

>[Y U **(T)**]
>
>[**Y** U **(T)**] - Y < T ? false
>
>[Y **U** **(T)**] - U < T ? false
>
>[<**T**> U <**Y**>] - **SWAP**

>**[A E E I N O Q S S T]**

>[U **(Y)**]
>
>[**U** **(Y)**] - U < Y ? true

> **[A E E I N O Q S S T U Y]**

3. About how many compares will Quick.sort() make when sorting an array of N items that are all equal?
> When the input data is already sorted, Quicksort performs at its worst.
>
> Given that every element in the array is the SAME right now, the array is sorted. So, the worst-case scenario for speedy sort is this.
>
> One of the partitions has 1 element (0 comparisons), while the other is recursively sorting a N-1 sub-array.
>
> (𝑁 − 1) + (𝑁 − 2) + ⋯+ 1=  N(N-1)/2 comparisons
>
>**𝑂(𝑁^2)**

4. Show, in the style of the trace given with the code, how the entropy-optimal sort first partitions the array B A B A B A B A C A D A B R A
> Applications commonly use arrays with a lot of duplicate sort keys. It may be possible to go from linearithmic to linear sorting in some cases.
>
>Partitioning the array into three sections, one for each item with a key that is smaller than, equal to, and larger than the partitioning item's key, is a simple solution.

Found answer on the web:
[Solution](https://algs4.cs.princeton.edu/23quicksort/images/partition-3.1.12.png)
![Solution](https://algs4.cs.princeton.edu/23quicksort/images/partition-3.1.12.png "Solution")

5. **Bad partitioning.** How does not stop on equal keys make quicksort go quadratic when all keys are equal? Give an example of this input.
> HHHHHHHH, if we don't stop on equal keys we will get one subarray of 0 and one size of 8.

&nbsp;
## Heapsort

1. Criticize the following idea: to implement find the maximum in constant time, why not keep track of the maximum value inserted so far, then return that value for find the maximum?
> Heap: Ordered binary tree
>
> Because stack and queue don't store their elements in sorted order, it is impossible to determine the maximum indefinitely.
>
> Will need starting again when updating the maximum value following a remove-the-maximum procedure.

2. Is an array that is sorted in decreasing order a max-oriented heap?
> Heap is a tree data structure which is useful for priority queue.
>
> A max heap is a complete binary tree in which the value of a node is greater than or equal to the values of its children.
>
> Yes, it is sorted in decreasing order of a max oriented heap.


2. Suppose that the sequence
P R I O * R * * I * T * Y * * * Q U E * * * U * E
(where a letter means insert and an asterisk means remove the maximum) is inserted to an initially empty max heap. Give the sequence of values returned by del_max operations.

> insert P in queue -> P 
>
> insert R -> R P
>
> insert I -> R P I
>
> insert O  -> R P O I
>
> ^ remove max -> P O I (**-R**)
>
> insert R -> R P O I 
>
> ^ remove max P O I (**-R**)
>
> ^ remove max O I (**-P**)
>
> insert I -> O I I
>
> ^ remove max I I (**-O**)
>
> insert T -> T I I
>
> ^ remove max I I (**-T**)
>
> insert Y -> Y I I
>
> ^ remove max II (**-Y**)
>
> ^ remove max I (**-I**)
>
> ^ remove max [] (**-I**)
>
> insert Q -> Q
>
> insert U -> Q U
>
> insert E -> Q U E
>
> ^ remove max U E (**-Q**)
>
> ^ remove max E (**-U**)
>
> ^ remove max [] (**-E**)
>
> insert U -> U
>
> ^ remove max [] (**-U**)
>
> insert E -> E
>

## LAST
The leftmost column is the original imput of string to be sorted; the rightmost column gives the string in sorted orderl the other columns are the contents at the intermediate step during one of the 8 sorting algorrithms listed below. Match up each algorithm by writing its number under correspodnig colunb. Use each number exactly once.
> 0: Original input: **A**
>

> 1: Sorted: **J**
>

> 2: Selection sort: **H**
>
> All starting letters in the sorted order. [1...11 ("**HISI"**)] - sorted (all minimums), [12...32] - unsorted.
>

> 3: Insertion sort: **F**
>
>Elements in part before "UARE" are sorted, elements below are NOT sorted (as in input).
>

> 4: Shellsort: **C**
>
> Shell's original sequence: N/2 , N/4 , …, 1
>

> 5: Mergesort(top-down): **B**
>
> Split array in half and we can see that top half sortet as in Merge sort.
>

> 6: Mergesort(bottom-up): **D**
>
> In Mergesort (bottom-up) the idea that a one item array is already sorted, so if we have a specific array we can treat each element in it as a sorted array, then apply the merge as usual. 

> 7: Quicksort: **I**
>
>Array partitioned in two parts - PIVOT ("HELP"). All strings less than pivot are above and greater one are below it.
>

> 8: Quicksort (3-way): **E** ???
>

> 9: Heapsort: **G**
> It's heapsort because the elements of the list are in the order which the sub parts follows the principle of max heap.
>
> WATC - Parent node.

![Solution](https://res.cloudinary.com/dulasau/image/upload/v1675105551/ALGOS_ephrlj.bmp "Solution")

## License

If you have any questions please contact me:
dmitrushok@gmail.com

**Dmitry Ulasau**



