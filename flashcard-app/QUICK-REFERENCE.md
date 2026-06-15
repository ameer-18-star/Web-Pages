# Quick Import Reference Guide

## Minimal Format (Required Fields Only)

```json
[
  {
    "topic": "Topic Name",
    "question": "Question text?",
    "answer": "Answer text"
  }
]
```

## Full Format (All Fields)

```json
[
  {
    "id": 1,
    "topic": "Topic Name",
    "question": "Question with <b>bold</b> and <i>italic</i>?",
    "answer": "Answer with <b>bold</b> and <i>italic</i><br>and line breaks",
    "image": "https://example.com/image.png",
    "marked": false,
    "seen": false,
    "difficulty": null
  }
]
```

## Field Quick Reference

| Field | Type | Required | Default | Values |
|-------|------|----------|---------|--------|
| `id` | Number | No | Auto-generated | Any integer |
| `topic` | String | **YES** | - | Any text |
| `question` | String | **YES** | - | Text with HTML |
| `answer` | String | **YES** | - | Text with HTML |
| `image` | String/null | No | `null` | URL or `null` |
| `marked` | Boolean | No | `false` | `true`/`false` |
| `seen` | Boolean | No | `false` | `true`/`false` |
| `difficulty` | String/null | No | `null` | `"easy"`, `"normal"`, `"hard"`, `"forget"`, `null` |

## HTML Tags Supported

- `<b>text</b>` - Bold
- `<i>text</i>` - Italic  
- `<br>` - Line break

## Quick Examples

### Simple Card
```json
{
  "topic": "Math",
  "question": "What is 2 + 2?",
  "answer": "4"
}
```

### Card with Formatting
```json
{
  "topic": "Science",
  "question": "What is <b>H₂O</b>?",
  "answer": "<b>Water</b><br>Two hydrogen, one oxygen"
}
```

### Card with Image
```json
{
  "topic": "Biology",
  "question": "What is photosynthesis?",
  "answer": "Process converting light to energy",
  "image": "https://example.com/photosynthesis.png"
}
```

### Previously Studied Card
```json
{
  "topic": "History",
  "question": "When did WWII end?",
  "answer": "1945",
  "marked": true,
  "seen": true,
  "difficulty": "easy"
}
```

## Import Steps

1. **Create** a `.json` file
2. **Add** flashcard objects in an array
3. **Include** required fields: `topic`, `question`, `answer`
4. **Validate** JSON syntax (use JSONLint.com)
5. **Import** using the 📥 Import button in app

## Common Mistakes to Avoid

❌ Forgetting commas between objects
❌ Missing quotes around strings
❌ Invalid `difficulty` values
❌ Not wrapping everything in `[ ]` array
❌ Using single quotes instead of double quotes

✅ Use double quotes for all strings
✅ Separate objects with commas
✅ Validate JSON before importing
✅ Start with simple template and expand

## Need More Help?

See the full documentation: `IMPORT-FILE-STRUCTURE.md`