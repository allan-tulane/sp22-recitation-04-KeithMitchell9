# CMPS 2200  Recitation 01

**Name (Team Member 1):** Keith J Mitchell

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`.


## Setup
- Make sure you have a Github account.
- Login to Github.
- Login to repl.it, using "sign in with github"
- Click on the assignment link sent through canvas and accept the assignment. 
- Click on your personal github repository for the assignment.
- Login in Repls https://replit.com/repls and then create a new replit by importing from github repository.
- You'll work with a partner to complete this recitation. To do so, we'll break you into Zoom rooms. You will be able to code together in the same `repl.it` instance. You can choose whose repl.it instance you will share. This person will click the "Share" button in their repl.it instance and email the lab partner.
- Make sure the dependencies are installed. Please use 'pip install -r requirements.txt'.

## Running and testing your code
- In the command-line window, run `./ipy` to launch an interactive IPython shell. This is an interactive shell to help run and debug your code. Any code you change in `main.py` will be reflected from this shell. So, you can modify a function in `main.py`, then test it here.
  + If it seems things don't refresh, try running `from main import *`
- You can exit the IPython prompt by either typing `exit` or pressing `ctrl-d`
- To run tests, from the command-line shell, you can run
  + `pytest main.py` will run all tests
  + `pytest main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Version Control" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [ ] 2. Test that your function is correct by calling from the command-line `pytest main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 

The worst case input value of 'key' for linear_search would be a key that does not exist in the list as the linear_search function will then have to check the entire list for the key which could take a lot of time.

The worst case input value of 'key' for binary_search would also be a key that does not exist in the list as the binary_search function will take log base 2 of the length of the list in order to find, or not find in this case, the key. This number would be rounded down to nearest integer.

- [ ] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 

The best case input value of 'key' in linear_search would be a key equal to the first item in the list. The linear_search function would find the key immediately as it begins searching at the front of the list.

The best case input value of 'key' for binary_search would be a key equal to the value found directly in the middle of the array as binary_search looks in the middle of the array in order to halve it if it does not find the key in the middle, making the middle value the ideal value for a key to be.

- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:

**TODO: add your timing results here**

n	| linear | binary

10 | 0.00357628 | 0.00357628

100 | 0.01716614 | 0.00476837

1000 | 0.30612946 | 0.00810623

10000 | 1.89733505 | 0.01168251

100000 | 23.18477631 | 0.02121925

1000000 | 400.09832382 | 0.02455711

10000000 | 3922.14965820 | 0.03099442


- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

**TODO: your answer goes here**

    The theoretical runtimes do match our empirical results because the linear worst-case run time increases drastically in contrast to the binary worst-case run time. Additionally, the linear runtime follows an O(n) runtime when graphed; whereas the binary also follows its own respective runtime when graphed.

- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times.


  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? 
  
        O(k * n) would be the worst case when looking through k times as this is the worst case linear search scenario multiplied by the amount of times looked through
  + For binary search? 
  
        O((n + k) * log base 2 (n)) would be the worst case for binary search
  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? 
  
        If one is searching either one time or another low integer such as 2 or possibly 3 times, linear search tends to yield a quicker outcome, whereas when searching multiple times, sorting and binary will be the time sensible method.