# Huffman-Coding

## Aim

To implement Huffman coding to compress the data using Python.

## Software Required

1. Anaconda - Python 3.7

## Algorithm

### Step 1:
Get the input string from the user.

### Step 2:
Calculate the frequency of each character in the string.

### Step 3:
Create tree nodes and sort them in ascending order of frequency.

### Step 4:
Combine the two nodes with the lowest frequencies repeatedly
to construct the Huffman tree. Assign 0 to the left branch
and 1 to the right branch.

### Step 5:
Traverse the tree and print the Huffman code for each character.

## NAME : SARAN RAJ M

## REGISTER NUMBER : 212225240138

## Program

```python
# Get the input String
string = input("Enter a string: ")

# Create tree nodes
class Node:
    def __init__(self, freq, symbol, left=None, right=None):
        self.freq = freq
        self.symbol = symbol
        self.left = left
        self.right = right
        self.code = ''

# Main function to implement Huffman coding
def printNodes(node, val=''):
    newVal = val + node.code

    if node.left:
        printNodes(node.left, newVal)

    if node.right:
        printNodes(node.right, newVal)

    if not node.left and not node.right:
        print(node.symbol, ":", newVal or '0')

# Calculate frequency of occurrence
freq = {}

for ch in string:
    freq[ch] = freq.get(ch, 0) + 1

nodes = []

for ch in freq:
    nodes.append(Node(freq[ch], ch))

while len(nodes) > 1:
    nodes = sorted(nodes, key=lambda x: x.freq)

    left = nodes[0]
    right = nodes[1]

    left.code = '0'
    right.code = '1'

    newNode = Node(left.freq + right.freq,
                   left.symbol + right.symbol,
                   left, right)

    nodes = nodes[2:]
    nodes.append(newNode)

# Print the characters and its Huffman code
print("Huffman Codes:")

if nodes:
    printNodes(nodes[0])
```

## Output
<img width="628" height="138" alt="image" src="https://github.com/user-attachments/assets/93c1ca38-2894-4c94-a357-ed880c0ddb1b" />


## Result

Thus the Huffman coding was successfully implemented to
compress the data using Python programming.
