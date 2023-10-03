# Create a Trie

![alt text](https://media.geeksforgeeks.org/wp-content/uploads/20220828232752/Triedatastructure1.png)

(cr. geeksforgeeks)

## TrieNode() class

Class Memeber:
* `children`: A list with size 26, to save children node.
* `isEnd`: Boolean value, indicate whether a node represent the end of a word.

## Trie() class
* Member: root
* Function: insert(), search()

```python
class TrieNode:
    def __init__(self):
        self.children = [None] * 26
        self.isEnd = False

class Trie:
    def __init__(self):
        self.root = TrieNode()
    
    def insert(self, word):
        curNode = self.root
        for c in word:
            ind = ord(c) - ord('a')
            # if the current prefix already in Trie
            if curNode.children[ind]:
                curNode = curNode.children[ind]
            # If the current prefix not in Trie
            else:
                curNode.children[ind] = TrieNode()
                curNode = curNode.children[ind]
        curNode.isEnd = True

    def search(self, node, word, pos):
        ind = ord(word[pos]) - ord('a')
        if node.children[ind]:
            if pos == len(word) - 1 and node.isEnd:
                return True
            else:
                return self.search(node.children[ind], word, pos + 1)
        else:
            return True
```
