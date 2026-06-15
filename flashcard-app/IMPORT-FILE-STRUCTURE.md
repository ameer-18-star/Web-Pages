# Flashcard Import File Structure Documentation

## Overview
This document explains the complete structure for importing flashcards into the FlashStudy application. The import file must be in **JSON format** with an array of flashcard objects.

---

## File Structure

```json
[
  {
    "id": 1,
    "topic": "Topic Name",
    "question": "Question text with optional <b>bold</b> and <i>italic</i> HTML tags",
    "answer": "Answer text with optional formatting",
    "image": "URL or null",
    "marked": false,
    "seen": false,
    "difficulty": null
  }
]
```

---

## Field Descriptions

### Required Fields

#### 1. `id` (Number or Auto-generated)
- **Type:** Integer
- **Description:** Unique identifier for each flashcard
- **Notes:** If not provided, the app will auto-generate IDs
- **Example:** `1`, `2`, `3`, etc.

#### 2. `topic` (String - Required)
- **Type:** String
- **Description:** Category or subject of the flashcard
- **Usage:** Used for filtering and generating study suggestions
- **Example:** `"JavaScript"`, `"Python"`, `"History"`, `"Mathematics"`

#### 3. `question` (String - Required)
- **Type:** String (HTML supported)
- **Description:** The question or front side of the flashcard
- **Formatting:** Supports HTML tags like `<b>`, `<i>`, `<br>`
- **Examples:**
  ```json
  "What is a <b>closure</b> in JavaScript?"
  "Explain the <i>Pythagorean theorem</i>"
  "What does <b>HTTP</b> stand for?"
  ```

#### 4. `answer` (String - Required)
- **Type:** String (HTML supported)
- **Description:** The answer or back side of the flashcard
- **Formatting:** Supports HTML tags like `<b>`, `<i>`, `<br>`
- **Examples:**
  ```json
  "A closure is a function that retains access to its <i>outer scope</i>."
  "<b>a² + b² = c²</b><br>Where c is the hypotenuse"
  "HyperText Transfer Protocol"
  ```

### Optional Fields

#### 5. `image` (String or null)
- **Type:** String (URL) or null
- **Description:** URL to an image for visual explanation
- **Default:** `null`
- **Supported:** Any publicly accessible image URL
- **Examples:**
  ```json
  "https://example.com/image.png"
  "https://images.unsplash.com/photo-123456789"
  null
  ```

#### 6. `marked` (Boolean)
- **Type:** Boolean
- **Description:** Whether the card is bookmarked/flagged
- **Default:** `false`
- **Usage:** For marking important cards for review
- **Values:** `true` or `false`

#### 7. `seen` (Boolean)
- **Type:** Boolean
- **Description:** Whether the card has been viewed before
- **Default:** `false`
- **Usage:** Used in "Learn New" study mode
- **Values:** `true` or `false`

#### 8. `difficulty` (String or null)
- **Type:** String or null
- **Description:** User's rating of card difficulty
- **Default:** `null`
- **Possible Values:** 
  - `"easy"` - Easy to remember
  - `"normal"` - Moderate difficulty
  - `"hard"` - Difficult to remember
  - `"forget"` - Completely forgotten
  - `null` - Not yet rated
- **Usage:** Used for spaced repetition and "Review Difficult" mode

---

## HTML Formatting Support

The `question` and `answer` fields support the following HTML tags:

### Text Formatting
- `<b>text</b>` - **Bold text**
- `<i>text</i>` - *Italic text*
- `<br>` - Line break

### Example with Multiple Formats
```json
{
  "question": "What is the <b>Pythagorean theorem</b>?",
  "answer": "In a right triangle: <b>a² + b² = c²</b><br>where <i>c</i> is the hypotenuse"
}
```

---

## Complete Examples

### Example 1: Basic Flashcard (Minimal Required Fields)
```json
{
  "topic": "JavaScript",
  "question": "What is a variable?",
  "answer": "A container for storing data values"
}
```
*Note: `id`, `image`, `marked`, `seen`, and `difficulty` will be auto-generated/defaulted*

### Example 2: Fully Populated Flashcard
```json
{
  "id": 42,
  "topic": "Python",
  "question": "What is a <b>list comprehension</b>?",
  "answer": "A concise way to create lists:<br><i>[expression for item in iterable]</i>",
  "image": "https://example.com/python-list.png",
  "marked": true,
  "seen": true,
  "difficulty": "normal"
}
```

### Example 3: Flashcard with Image
```json
{
  "id": 15,
  "topic": "Biology",
  "question": "What is the structure of a <b>cell</b>?",
  "answer": "A cell contains: <b>nucleus</b>, <i>cytoplasm</i>, and <i>cell membrane</i>",
  "image": "https://images.unsplash.com/photo-1234567890/cell-diagram",
  "marked": false,
  "seen": false,
  "difficulty": null
}
```

### Example 4: Previously Studied Flashcard
```json
{
  "id": 7,
  "topic": "History",
  "question": "When did <b>World War II</b> end?",
  "answer": "<b>September 2, 1945</b>",
  "image": null,
  "marked": true,
  "seen": true,
  "difficulty": "easy"
}
```

---

## Import File Templates

### Template 1: Simple Import (5 Cards)
```json
[
  {
    "topic": "Topic 1",
    "question": "Question 1?",
    "answer": "Answer 1"
  },
  {
    "topic": "Topic 1",
    "question": "Question 2?",
    "answer": "Answer 2"
  },
  {
    "topic": "Topic 2",
    "question": "Question 3?",
    "answer": "Answer 3"
  },
  {
    "topic": "Topic 2",
    "question": "Question 4?",
    "answer": "Answer 4"
  },
  {
    "topic": "Topic 3",
    "question": "Question 5?",
    "answer": "Answer 5"
  }
]
```

### Template 2: Advanced Import with All Features
```json
[
  {
    "id": 1,
    "topic": "Programming",
    "question": "What is <b>Object-Oriented Programming</b>?",
    "answer": "A programming paradigm based on <i>objects</i> containing data and code",
    "image": null,
    "marked": false,
    "seen": false,
    "difficulty": null
  },
  {
    "id": 2,
    "topic": "Programming",
    "question": "Name the four pillars of <b>OOP</b>",
    "answer": "<b>1. Encapsulation</b><br><b>2. Abstraction</b><br><b>3. Inheritance</b><br><b>4. Polymorphism</b>",
    "image": "https://example.com/oop-diagram.png",
    "marked": true,
    "seen": true,
    "difficulty": "hard"
  }
]
```

---

## Common Topics Examples

Here are suggested topic names for organizing your flashcards:

### Technology
- `"JavaScript"`
- `"Python"`
- `"React"`
- `"Node.js"`
- `"Data Structures"`
- `"Algorithms"`
- `"Database"`
- `"Networking"`
- `"Security"`
- `"DevOps"`

### Sciences
- `"Physics"`
- `"Chemistry"`
- `"Biology"`
- `"Mathematics"`
- `"Astronomy"`

### Humanities
- `"History"`
- `"Geography"`
- `"Literature"`
- `"Philosophy"`
- `"Languages"`

### Professional
- `"Business"`
- `"Marketing"`
- `"Finance"`
- `"Management"`
- `"Law"`

### Academic
- `"SAT Prep"`
- `"GRE Vocabulary"`
- `"Medical Terms"`
- `"Legal Terms"`

---

## Best Practices

### 1. Organize by Topics
Group related cards under the same topic for better organization and study suggestions.

### 2. Use Clear Questions
Make questions specific and unambiguous.

**Good:** `"What is the time complexity of binary search?"`
**Bad:** `"Binary search?"`

### 3. Concise Answers
Keep answers focused and to the point. Use formatting for clarity.

### 4. Use Images Wisely
Add images for:
- Diagrams and charts
- Visual concepts
- Complex illustrations
- Anatomical structures

### 5. Consistent Formatting
Use consistent HTML formatting across all cards.

### 6. Start Fresh
For new decks, set:
```json
"marked": false,
"seen": false,
"difficulty": null
```

### 7. Pre-mark Important Cards
Flag critical cards for immediate review:
```json
"marked": true
```

---

## Validation Rules

Your JSON file must pass these validation checks:

1. ✅ Valid JSON syntax
2. ✅ Root element is an array `[ ]`
3. ✅ Each card is an object `{ }`
4. ✅ Required fields: `topic`, `question`, `answer`
5. ✅ `difficulty` must be: `"easy"`, `"normal"`, `"hard"`, `"forget"`, or `null`
6. ✅ `marked` and `seen` must be boolean (`true`/`false`)
7. ✅ `image` must be a valid URL string or `null`

---

## Error Handling

### Common Import Errors

**Error:** "Invalid JSON format"
**Solution:** Validate your JSON using a JSON validator online

**Error:** "Expected an array of flashcards"
**Solution:** Ensure your file starts with `[` and ends with `]`

**Error:** Missing required fields
**Solution:** Ensure each card has `topic`, `question`, and `answer`

---

## Tips for Creating Import Files

1. **Start Small:** Test with 5-10 cards first
2. **Use a Text Editor:** Use VS Code, Sublime, or any code editor with JSON syntax highlighting
3. **Validate Online:** Use JSONLint.com to validate your file
4. **Keep Backups:** Save multiple versions of your flashcard decks
5. **Export First:** Export existing cards to see the format
6. **Test Images:** Ensure image URLs are publicly accessible

---

## Sample Complete Import File

See the included `flashcards-import-example.json` file for a complete working example with 20 flashcards covering multiple topics.

---

## Import Process

1. Click **"📥 Import"** button in the app
2. Either:
   - **Paste JSON** directly into the text area, OR
   - **Upload a .json file** using the file selector
3. Click **"Import"** button
4. Success: Cards are loaded and saved to localStorage
5. Error: Check console for specific error messages

---

## Export Your Progress

To save your current progress including difficulty ratings:

1. Click **"📤 Export"** button
2. A JSON file will download with filename: `flashcards_YYYY-MM-DD.json`
3. This file includes all your progress data
4. Can be re-imported later to restore your progress

---

## Need Help?

If you encounter issues:
1. Validate your JSON syntax
2. Check that all required fields are present
3. Ensure image URLs are valid and accessible
4. Start with the simple template and build up
5. Use the export feature to see correct formatting

---

**Version:** 1.0  
**Last Updated:** 2026-01-27  
**Compatible with:** FlashStudy App v1.0