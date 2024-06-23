#  Question 1
    def foo(n):
    sum = 0 # time cost of assignment = c1
    # assume initialization of i to 0 at the start of loop has 0 cost
    for i in range(n): # cost for each (increment i and check if in range) = c2 
        sum = sum + i * i # cost of addition = c3, 
        # cost of multiplication = c4 and 
        # cost of assignment = c1
    return sum # cost of return = c5

(Consider the python function below (read the comments carefully)
What is the overall time cost of calling the "foo" function, in terms of n,c1,c2,c3,c4n,c1,c2,c3,c4 and c5c5?
1 / 1 point

c1+c2+c3+c4+c5c1+c2+c3+c4+c5

**(n+1)∗c1+n∗(c2+c3+c4)+c5(n+1)∗c1+n∗(c2+c3+c4)+c5**

n∗n∗(c2+c3+c4+c1)+c1+c5n∗n∗(c2+c3+c4+c1)+c1+c5

c1+n∗(c2+c3+c4)+c5c1+n∗(c2+c3+c4)+c5

#  Consider this array of size nn sorted in descending order: [n,n−1,…,1][n,n−1,…,1].

Suppose we ran insertion sort to sort this array in ascending order.

Select all the correct options from the list below.

1. After ii steps, suppose the sorted portion is [n−i+1,…,n][n−i+1,…,n] and the element to be inserted is (n−i)(n−i).  We will need to perform ii swaps to ensure that n−in−i is inserted in the correct place.
2. The total number of swaps is given by:
    1+2+⋯+(n−1)=n(n−1)21+2+⋯+(n−1)=2n(n−1) ->correct
3. Consider a different array  a: [a1, a2, ..., an]  that satisfies the property that a[i] < a[i+1] for all but one place a[j] wherein a[j] > a[j+1]. Insertion sort as presented in lecture will run in Θ(n)Θ(n) time for such an "almost" ascending sorted array.
You didn’t select all the correct answers 
