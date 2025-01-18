# Trie (Prefix Tree) Data Structure in JavaScript 🚀  

A simple implementation of the **Trie (Prefix Tree)** data structure in JavaScript. This repository demonstrates how to create a trie class with essential methods and explains its functionality with practical examples.  

---

## What is a Trie (Prefix Tree)?  
A **Trie**, also known as a **Prefix Tree**, is a tree-like data structure used to store strings in a way that allows for efficient searching, insertion, and deletion of words, especially when dealing with large sets of strings. Each node represents a single character of a word, and words are stored along paths from the root to the leaves. It is particularly useful for tasks like autocomplete, spell checking, and IP routing.  

---

## Features  
- **Insert**: Add a word to the trie.  
- **Search**: Check if a word exists in the trie.  
- **StartsWith**: Check if there is any word in the trie that starts with a given prefix.  
- **Delete**: Remove a word from the trie.  

---

## Code Implementation  

Here’s the JavaScript implementation of the trie:  

```javascript
class TrieNode {
    constructor() {
        this.children = {}; // Stores child nodes
        this.isEndOfWord = false; // Marks if it's the end of a word
    }
}

class Trie {
    constructor() {
        this.root = new TrieNode(); // Root of the trie
    }

    // Insert a word into the trie
    insert(word) {
        let currentNode = this.root;
        for (let char of word) {
            if (!currentNode.children[char]) {
                currentNode.children[char] = new TrieNode();
            }
            currentNode = currentNode.children[char];
        }
        currentNode.isEndOfWord = true;
    }

    // Search for a word in the trie
    search(word) {
        let currentNode = this.root;
        for (let char of word) {
            if (!currentNode.children[char]) {
                return false;
            }
            currentNode = currentNode.children[char];
        }
        return currentNode.isEndOfWord;
    }

    // Check if any word in the trie starts with the given prefix
    startsWith(prefix) {
        let currentNode = this.root;
        for (let char of prefix) {
            if (!currentNode.children[char]) {
                return false;
            }
            currentNode = currentNode.children[char];
        }
        return true;
    }

    // Delete a word from the trie
    delete(word) {
        this.deleteHelper(this.root, word, 0);
    }

    // Helper function to delete a word
    deleteHelper(node, word, index) {
        if (index === word.length) {
            if (!node.isEndOfWord) return false;
            node.isEndOfWord = false;
            return Object.keys(node.children).length === 0;
        }

        const char = word[index];
        if (!node.children[char]) return false;

        const shouldDeleteCurrentNode = this.deleteHelper(node.children[char], word, index + 1);

        if (shouldDeleteCurrentNode) {
            delete node.children[char];
            return Object.keys(node.children).length === 0;
        }

        return false;
    }
}
```

---

## Example Usage  

```javascript
// Initialize the trie
const trie = new Trie();

// Insert words into the trie
trie.insert("apple");
trie.insert("app");

// Search for words
console.log(trie.search("apple")); // Output: true
console.log(trie.search("app")); // Output: true
console.log(trie.search("appl")); // Output: false

// Check if any word starts with a given prefix
console.log(trie.startsWith("app")); // Output: true
console.log(trie.startsWith("appl")); // Output: true
console.log(trie.startsWith("banana")); // Output: false

// Delete a word from the trie
trie.delete("app");
console.log(trie.search("app")); // Output: false
console.log(trie.search("apple")); // Output: true
```

---

## Real-World Applications  
1. **Autocomplete**: Suggesting words based on a prefix.  
2. **Spell Checking**: Finding correct spelling suggestions.  
3. **IP Routing**: Efficient routing for network addresses.  
4. **Dictionary Implementation**: Storing a dictionary for fast word lookups.  

---

## TikTok Tutorial 🎥  
Want to see a quick tutorial on how to build this? Check out this TikTok video:  
[]()  

---

## How to Run the Code  
1. Clone the repository:  
   ```bash
   git clone https://github.com/fix2015/structure_trie
   cd structure_trie
   ```
2. Open the file `index.js` in your favorite code editor.  
3. Run the file using Node.js:  
   ```bash
   node index.js
   ```

---

## Contributing  
Contributions are welcome! If you have suggestions or want to add new features, feel free to create a pull request.  

---

## License  
This project is licensed under the MIT License.  

---

## Connect with Me:
- [LinkedIn - Vitalii Semianchuk](https://www.linkedin.com/in/vitalii-semianchuk-9812a786/)
- [Telegram - @jsmentorfree](https://t.me/jsmentorfree) - We do a lot of free teaching on this channel! Join us to learn and grow in web development.
- [Tiktok - @jsmentoring](https://www.tiktok.com/@jsmentoring) Everyday new videos
- [Youtube - @jsmentor-uk](https://www.youtube.com/@jsmentor-uk) Mentor live streams
- [Dev.to - fix2015](https://dev.to/fix2015) Javascript featured, live, experience but about Trie (Prefix Tree)
