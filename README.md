# LeetCode Solution Swift 
[![language badge](https://img.shields.io/badge/language-swift%202.2-orange.svg)](https://github.com/apple/swift)
[![progress](https://img.shields.io/badge/progress-%20%20Updating%2048%2F354-green.svg)](https://github.com/wty21cn/leetcode-solution-swift#bit-manipulation)
[![license badge](https://img.shields.io/badge/license-MIT-blue.svg)](./LICENSE)

## About
This project aims to provide swift version solutions for algorithm problems on [LeetCode Online Judge](https://leetcode.com/problemset/algorithms/).

For current stage, the main target is to provide solutions for all problems, so there will be no well-considered test cases provided, also Xcode unit test is not included. But all the solutions here can pass the related problems on LeetCode OJ.

Some of the algorithm analyses will be provide alongside the solutions, some may not, and will be updated in the future.

To run a specific solution, please change the question number in [main.swift](./leetcode-solution-swift/Shared/main.swift),  e.g. `q371.getSolution()` to run solution for question 371 "Sum Of Two Integers". 

And modify `static func getSolution()` in `struct Q0371` to provide test cases

```swift
struct q371 {
    
    class Solution {
        fun getSum(a: Int, _ b: Int) -> Int {
            
            var sum = a
            var adding = b
            while adding != 0 {
                let t = sum ^ adding
                adding = (sum & adding) << 1
                sum = t
            }
            return sum
            
        }
    }
    
    static fun getSolution() -> Void {
        print(Solution().getSum(-1203940,1230912848102))
    }
}
```

## Notes 
### Helper Class
There are lots of problems on LeetCode OJ using two data structures: Linked List and Binary Tree. LeetCode OJ use following serialized format to describe a binary tree.

> The input `[1,nil,2,3]` represents the serialized format of a binary tree using level order traversal, where nil signifies a path terminator where no node exists below.
> 
> Some examples:
> 
> * `[]`
> 
```
Empty tree. The root is a reference to nil
```
> * `[1,2,3]`
>
```
       1
      / \
     2   3
```
> * `[1,nil,2,3]`
> 
```
       1
        \
         2
        /
       3
```
> * `[5,4,7,3,nil,2,nil,-1,nil,9]`
> 
```
       5
      / \
     4   7
    /   /
   3   2
  /   /
 -1  9
```

The helper class: [LinkedListBuilder/LinkedListPrinter](./leetcode-solution-swift/Shared/LinkedListHelper.swift) and [BinaryTreeBuilder/BinaryTreePrinter](./leetcode-solution-swift/Shared/BinaryTreeHelper.swift) comply to this serialized format and is very useful to deserialize and visualize these two data structures.

They can be used to build linked list and complicated binary tree in just one line:

```swift
let root = BinaryTreeBuilder.buildTreeWithNodes([10,7,12,6,9,11,15,nil,3,8,nil,nil,nil,13,16])

let head = LinkedListBuilder.buildLinkedListWithNodes([1,2,3,4,5,6,7])
```

Print linked list and binary tree visually for easy debugging:

```swift
LinkedListPrinter.print(head!)

1-->2-->3-->4-->5-->6-->7

BinaryTreePrinter.print(root!)

         ┌───── 15
 ┌───── 14
 │       │       ┌───── 13
 │       └───── 12
 │               └───── 11
10
 │       ┌───── 8
 │       │       └───── 7
 └───── 5
         │       ┌───── 4
         │       │       └───── 2
         └───── 1

```

### Utility Script
#### Solution Symlink

The solution source codes in leetcode-solution-swift Xcode project is structured based on the problem difficulty: Easy, Medium and Hard. 

But the utility python script [generate-solution-symlink.py](./util/generate-solution-symlink.py) can be used to generate source code symlinks in centralized(`../solution-links/centralized`) and category based structure(`../solution-links/category`). Simply follow commands below after clone the repo to local disk.

```shell
cd leetcode-solution-swift/util
./generate-solution-symlink.py

```
The category information is stored in each source code file, generally at 5th line after `"//  Category* : "`, one solutions can relate to more than one algorithm categories which separated by white space.

#### README.md

This README.md is auto generated by script [generate-readme.py](./util/generate-solution-symlink.py). Beacause manually update the solution list below is a wast of time. This script use [readme-header.md](./util/readme-header.md) as its datasource, so any change to README.md should be made in [readme-header.md](./util/readme-header.md), and auto generate to README.md

## Solution List
The problems listed here only contain those whose solution is already provided by this project. And the list is auto genarated by [generate-readme.py](./util/generate-solution-symlink.py). 

If you want a full list of questions, please check [leetcode.com](https://leetcode.com/problemset/algorithms/)

|   #   |       Title        |     Solution      |    Difficulty   |       Note       |
| :---: | :----------------: | :---------------: | :-------------: | :--------------: |
| 7 | [Reverse Integer](https://leetcode.com/problems/verse-integer) | [swift](./leetcode-swift/Easy/q7-reverse-integer.swift) | Easy |  |
| 9 | [Palindrome Number](https://leetcode.com/problems/lindrome-number) | [swift](./leetcode-swift/Easy/q9-palindrome-number.swift) | Easy |  |
| 13 | [Roman To Integer](https://leetcode.com/problems/roman-to-integer) | [swift](./leetcode-swift/Easy/q013-roman-to-integer.swift) | Easy |  |
| 21 | [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists) | [swift](./leetcode-swift/Easy/q021-merge-two-sorted-lists.swift) | Easy |  |
| 24 | [Swap Nodes In Pairs](https://leetcode.com/problems/swap-nodes-in-pairs) | [swift](./leetcode-swift/Easy/q024-swap-nodes-in-pairs.swift) | Easy |  |
| 26 | [Remove Duplicates From Sorted Array](https://leetcode.com/problems/emove-duplicates-from-sorted-array) | [swift](./leetcode-swift/Easy/q26-remove-duplicates-from-sorted-array.swift) | Easy |  |
| 27 | [Remove Element](https://leetcode.com/problems/emove-element) | [swift](./leetcode-swift/Easy/q27-remove-element.swift) | Easy |  |
| 66 | [Plus One](https://leetcode.com/problems/lus-one) | [swift](./leetcode-swift/Easy/q66-plus-one.swift) | Easy |  |
| 70 | [Climbing Stairs](https://leetcode.com/problems/climbing-stairs) | [swift](./leetcode-swift/Easy/q070-climbing-stairs.swift) | Easy |  |
| 83 | [Remove Duplicates From Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list) | [swift](./leetcode-swift/Easy/q083-remove-duplicates-from-sorted-list.swift) | Easy |  |
| 100 | [Same Tree](https://leetcode.com/problems/same-tree) | [swift](./leetcode-swift/Easy/q100-same-tree.swift) | Easy |  |
| 101 | [Symmetric Tree](https://leetcode.com/problems/symmetric-tree) | [swift](./leetcode-swift/Easy/q101-symmetric-tree.swift) | Easy |  |
| 102 | [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal) | [swift](./leetcode-swift/Easy/q102-binary-tree-level-order-traversal.swift) | Easy |  |
| 103 | [Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal) | [swift](./leetcode-swift/Medium/q103-binary-tree-zigzag-level-order-traversal.swift) | Medium |  |
| 104 | [Maximum Depth Of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree) | [swift](./leetcode-swift/Easy/q104-maximum-depth-of-binary-tree.swift) | Easy |  |
| 107 | [Binary Tree Level Order Traversal II](https://leetcode.com/problems/binary-tree-level-order-traversal-ii) | [swift](./leetcode-swift/Easy/q107-binary-tree-level-order-traversal-ii.swift) | Easy |  |
| 110 | [Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree) | [swift](./leetcode-swift/Easy/q110-balanced-binary-tree.swift) | Easy |  |
| 111 | [Minimum Depth Of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree) | [swift](./leetcode-swift/Easy/q111-minimum-depth-of-binary-tree.swift) | Easy |  |
| 118 | [Pascals Triangle](https://leetcode.com/problems/pascals-triangle) | [swift](./leetcode-swift/Easy/q118-pascals-triangle.swift) | Easy |  |
| 119 | [Pascals Triangle II](https://leetcode.com/problems/pascals-triangle-ii) | [swift](./leetcode-swift/Easy/q119-pascals-triangle-ii.swift) | Easy |  |
| 121 | [Best Time To Buy And Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock) | [swift](./leetcode-swift/Easy/q121-best-time-to-buy-and-sell-stock.swift) | Easy |  |
| 122 | [Best Time To Buy And Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii) | [swift](./leetcode-swift/Medium/q122-best-time-to-buy-and-sell-stock-ii.swift) | Medium |  |
| 141 | [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle) | [swift](./leetcode-swift/Easy/q141-linked-list-cycle.swift) | Easy |  |
| 160 | [Majority Element](https://leetcode.com/problems/majority-element) | [swift](./leetcode-swift/Easy/q160-majority-element.swift) | Easy |  |
| 171 | [Excel Sheet Column Number](https://leetcode.com/problems/excel-sheet-column-number) | [swift](./leetcode-swift/Easy/q171-excel-sheet-column-number.swift) | Easy |  |
| 172 | [Factorial Trailing Zeroes](https://leetcode.com/problems/factorial-trailing-zeroes) | [swift](./leetcode-swift/Easy/q172-factorial-trailing-zeroes.swift) | Easy |  |
| 191 | [Number Of 1 Bits](https://leetcode.com/problems/number-of-1-bits) | [swift](./leetcode-swift/Easy/q191-number-of-1-bits.swift) | Easy |  |
| 198 | [House Robber](https://leetcode.com/problems/house-robber) | [swift](./leetcode-swift/Easy/q198-house-robber.swift) | Easy |  |
| 202 | [Happy Number](https://leetcode.com/problems/happy-number) | [swift](./leetcode-swift/Easy/q202-happy-number.swift) | Easy |  |
| 206 | [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list) | [swift](./leetcode-swift/Easy/q206-reverse-linked-list.swift) | Easy |  |
| 213 | [House Robber II](https://leetcode.com/problems/house-robber-ii) | [swift](./leetcode-swift/Medium/q213-house-robber-ii.swift) | Medium |  |
| 217 | [Contains Duplicate](https://leetcode.com/problems/contains-duplicate) | [swift](./leetcode-swift/Easy/q217-contains-duplicate.swift) | Easy |  |
| 226 | [Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree) | [swift](./leetcode-swift/Easy/q226-invert-binary-tree.swift) | Easy |  |
| 231 | [Power Of Two](https://leetcode.com/problems/power-of-two) | [swift](./leetcode-swift/Easy/q231-power-of-two.swift) | Easy |  |
| 232 | [Implement Queue Using Stacks](https://leetcode.com/problems/implement-queue-using-stacks) | [swift](./leetcode-swift/Easy/q232-implement-queue-using-stacks.swift) | Easy |  |
| 235 | [Lowest Common Ancestor Of A Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree) | [swift](./leetcode-swift/Easy/q235-lowest-common-ancestor-of-a-binary-search-tree.swift) | Easy |  |
| 237 | [Delete Node In A Linked List](https://leetcode.com/problems/delete-node-in-a-linked-list) | [swift](./leetcode-swift/Easy/q237-delete-node-in-a-linked-list.swift) | Easy |  |
| 242 | [Valid Anagram](https://leetcode.com/problems/valid-anagram) | [swift](./leetcode-swift/Easy/q242-valid-anagram.swift) | Easy |  |
| 258 | [Add Digits](https://leetcode.com/problems/add-digits) | [swift](./leetcode-swift/Easy/q258-add-digits.swift) | Easy |  |
| 263 | [Ugly Number](https://leetcode.com/problems/ugly-number) | [swift](./leetcode-swift/Easy/q263-ugly-number.swift) | Easy |  |
| 283 | [Move Zeroes](https://leetcode.com/problems/move-zeroes) | [swift](./leetcode-swift/Easy/q283-move-zeroes.swift) | Easy |  |
| 292 | [Nim Games](https://leetcode.com/problems/nim-games) | [swift](./leetcode-swift/Easy/q292-nim-games.swift) | Easy |  |
| 326 | [Power Of Three](https://leetcode.com/problems/power-of-three) | [swift](./leetcode-swift/Easy/q326-power-of-three.swift) | Easy |  |
| 334 | [Everse String](https://leetcode.com/problems/everse-string) | [swift](./leetcode-swift/Easy/q334-everse-string.swift) | Easy |  |
| 342 | [Power Of Four](https://leetcode.com/problems/power-of-four) | [swift](./leetcode-swift/Easy/q342-power-of-four.swift) | Easy |  |
| 345 | [Reverse Vowels Of A String](https://leetcode.com/problems/reverse-vowels-of-a-string) | [swift](./leetcode-swift/Easy/q345-reverse-vowels-of-a-string.swift) | Easy |  |
| 349 | [Intersection Of Two Arrays](https://leetcode.com/problems/Intersection-of-two-arrays) | [swift](./leetcode-swift/Easy/q349-Intersection-of-two-arrays.swift) | Easy |  |
| 350 | [Intersection Of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii) | [swift](./leetcode-swift/Easy/q350-intersection-of-two-arrays-ii.swift) | Easy |  |
| 371 | [Sum Of Two Integers](https://leetcode.com/problems/sum-of-two-integers) | [swift](./leetcode-swift/Easy/q371-sum-of-two-integers.swift) | Easy |  |
