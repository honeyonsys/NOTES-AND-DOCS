# **Huffman Coding (Data Compression Algorithm)**  

---

## **Problem Statement**  
Given a string (or file) containing characters with different frequencies, we need to **compress the data** such that the size of the encoded string is minimized.  

Huffman Coding is a **lossless data compression algorithm** that assigns **variable-length binary codes** to input characters based on their **frequency**.  
- Characters with **higher frequency** get **shorter codes**.  
- Characters with **lower frequency** get **longer codes**.  
- No code is a **prefix** of another (prefix-free property).  

---

## **Real-World Example: File Compression (ZIP, GZIP, JPEG, MP3)**  
- **ZIP & GZIP** use Huffman Coding for text compression.  
- **JPEG & MP3** use Huffman Coding to reduce image and audio sizes.  
- **Morse Code** is similar to Huffman Coding:  
  - Frequent letters (`E`, `T`) have **shorter codes**.  
  - Less frequent letters (`Q`, `Z`) have **longer codes**.  

---

## **Solution Explanation**  

### **Step 1: Frequency Calculation**  
Count how often each character appears in the input text.  

### **Step 2: Build a Min-Heap (Priority Queue)**  
- Insert all characters as nodes into a **min-heap** (priority queue).  
- Nodes are sorted by **frequency** (smallest at the top).  

### **Step 3: Build Huffman Tree**  
- Remove two **smallest frequency nodes**, merge them into a new node.  
- Assign **‘0’** to the left child and **‘1’** to the right child.  
- Repeat until only one node remains (root of the Huffman Tree).  

### **Step 4: Generate Huffman Codes**  
- Traverse the tree to generate binary codes for each character.  

### **Step 5: Encode & Decode**  
- Replace characters in the text with their **Huffman codes** for compression.  
- Use the Huffman Tree to **decode** the compressed data back into the original text.  

---

## **Example**
### **Input String:** `"abacabad"`  
| Character | Frequency | Huffman Code |
|-----------|-----------|--------------|
| `a`       | 4         | `0`          |
| `b`       | 2         | `10`         |
| `c`       | 1         | `110`        |
| `d`       | 1         | `111`        |

### **Encoded Output:**  
`0 10 0 110 0 10 0 111`  

---

## **Java Code Implementation**  

### **1. Huffman Tree & Encoding**
```java
import java.util.*;

class HuffmanNode {
    char ch;
    int freq;
    HuffmanNode left, right;

    HuffmanNode(char ch, int freq) {
        this.ch = ch;
        this.freq = freq;
    }
}

// Comparator for Min-Heap
class HuffmanComparator implements Comparator<HuffmanNode> {
    public int compare(HuffmanNode a, HuffmanNode b) {
        return a.freq - b.freq;
    }
}

public class HuffmanCoding {
    public static void printCodes(HuffmanNode root, String code, Map<Character, String> huffmanMap) {
        if (root == null) return;
        if (root.left == null && root.right == null) {
            huffmanMap.put(root.ch, code);
        }
        printCodes(root.left, code + "0", huffmanMap);
        printCodes(root.right, code + "1", huffmanMap);
    }

    public static Map<Character, String> buildHuffmanTree(String text) {
        // Step 1: Count frequency
        Map<Character, Integer> freqMap = new HashMap<>();
        for (char ch : text.toCharArray()) {
            freqMap.put(ch, freqMap.getOrDefault(ch, 0) + 1);
        }

        // Step 2: Create a priority queue (min-heap)
        PriorityQueue<HuffmanNode> pq = new PriorityQueue<>(new HuffmanComparator());
        for (Map.Entry<Character, Integer> entry : freqMap.entrySet()) {
            pq.add(new HuffmanNode(entry.getKey(), entry.getValue()));
        }

        // Step 3: Build Huffman Tree
        while (pq.size() > 1) {
            HuffmanNode left = pq.poll();
            HuffmanNode right = pq.poll();
            HuffmanNode newNode = new HuffmanNode('-', left.freq + right.freq);
            newNode.left = left;
            newNode.right = right;
            pq.add(newNode);
        }

        // Step 4: Generate Huffman Codes
        HuffmanNode root = pq.poll();
        Map<Character, String> huffmanMap = new HashMap<>();
        printCodes(root, "", huffmanMap);
        return huffmanMap;
    }

    public static void main(String[] args) {
        String text = "abacabad";
        Map<Character, String> huffmanCodes = buildHuffmanTree(text);

        System.out.println("Huffman Codes:");
        for (Map.Entry<Character, String> entry : huffmanCodes.entrySet()) {
            System.out.println(entry.getKey() + ": " + entry.getValue());
        }
    }
}
```

---

## **Complexity Analysis**  
| Step                | Time Complexity |
|----------------------|----------------|
| Build Frequency Map | **\( O(n) \)**   |
| Build Min-Heap      | **\( O(n \log n) \)** |
| Build Huffman Tree  | **\( O(n \log n) \)** |
| Generate Codes      | **\( O(n) \)**   |
| **Total**           | **\( O(n \log n) \)** |

---

## **Why Use Huffman Coding?**  
✅ **Used in file compression (ZIP, GZIP).**  
✅ **Used in multimedia compression (JPEG, MP3).**  
✅ **Used in network data transmission (reduces bandwidth usage).**  
