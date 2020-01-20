# Data-Streams
 An approach to approximate the frequency of occurrences of different items in a data stream.

 Assume 𝑆 = < 𝑎1, 𝑎2, . . . , 𝑎𝑡 > is a data stream of items from the set {1,2,...,n}. Assume for any 1 ≤ i ≤ n, F[i] is the number of times i has appeared in S. We would like to have good approximations of the values F[i] (1 ≤ i ≤ n) at all times.
 
A simple way to do this is to just keep the counts for each item 1 ≤ i ≤ n separately. However, this will require O(n) space, and in many applications (e.g., think online advertising and counts of user’s clicks on ads) this can be prohibitively large. We see in this problem that it is possible to approximate these counts using a much smaller amount of space. To do so, we consider the algorithm explained below.

Strategy
The algorithm has two parameters 𝛿, 𝜖 > 0. It picks 𝑙𝑜𝑔 1/𝛿 independent hash functions: ∀𝑗 ∈ ⟦1;⌈𝑙𝑜𝑔 1/𝛿⌉⟧ , ℎ𝑗:{1,2, ⋯ , 𝑛} → {1,2, ⋯ ,⌈𝑒/𝜖⌉}, where log denotes natural logarithm. Also, it associates a count cj,x to any 1 ≤ 𝑗 ≤ 𝑙𝑜𝑔 1/𝛿
and 1 ≤ 𝑥 ≤ ⌈𝑒/𝜖⌉ . In the beginning of the stream, all these counts are initialized to 0. Then, upon arrival of each 𝑎𝑘 (1 ≤ 𝑘 ≤ 𝑡), each of the counts 𝐶𝑗,ℎ𝑗(𝑎𝑘) (1 ≤ 𝑗 ≤ ⌈𝑙𝑜𝑔 1/𝛿⌉) is incremented by 1.

For any 1 ≤ 𝑖 ≤ 𝑛, we define 𝐹̃[𝑖] = minj{𝑐𝑗,ℎ𝑗(𝑖)}. We will show that 𝐹̃[𝑖] provides a good approximation to F[i]. Note that this algorithm only uses 𝑂(1/𝜖log 1/𝛿) space.

Note: for any 1 ≤ i ≤ n: 𝐹̃[i] ≥ F[i], in the above algorithm.

Datasets
* words_stream.txt: each line of this file is a number corresponding to the ID of a word in the stream.
* counts.txt: each line is a pair of numbers separated by a tab. The first number is an ID of a word and the second number is its associated exact frequency count in the stream.
* hash_params.txt: each line is a pair of numbers separated by a tab, corresponding to parameters a and for the hash functions.
