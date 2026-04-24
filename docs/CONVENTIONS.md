# Anun Dictionary Conventions

This document outlines the formatting standards for all data in the Anun Dictionary Resources.

## JSON Structure Standards

### General Rules
- Use UTF-8 encoding
- Maintain consistent indentation (2 spaces)
- All Anun words should preserve their diacritics and orthography exactly
- English translations should be lowercase unless they are proper nouns

### ID Scheme
All entries use a consistent ID format: `{part_of_speech}_{sequential_number}`
- `n_001` for the first noun
- `v_005` for the fifth verb
- `adj_012` for the twelfth adjective

## Vocabulary Entry Format

Each vocabulary entry follows this structure:

```json
{
  "id": "n_001",
  "anun": "anun",
  "english": ["language", "speech"],
  "part_of_speech": "noun",
  "frequency": "high",
  "definition": "A system of communication using words and grammar; the language of the Anun people",
  "examples": [
    {
      "anun": "Anun vel mirat.",
      "english": "I speak Anun.",
      "audio": "optional_future_field"
    }
  ],
  "related_words": ["anune", "anunis"],
  "etymology": "Proto-Anun *anu-",
  "notes": "Optional usage notes or cultural context"
}
```

## Field Definitions

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `id` | string | Yes | Unique identifier for the entry |
| `anun` | string | Yes | The word in Anun orthography |
| `english` | array | Yes | One or more English translations |
| `part_of_speech` | string | Yes | noun, verb, adjective, adverb, preposition, particle, etc. |
| `frequency` | string | No | high, medium, low - indicates how common the word is |
| `definition` | string | Yes | Detailed English definition |
| `examples` | array | Yes | At least one example sentence |
| `related_words` | array | No | IDs or Anun words related to this entry |
| `etymology` | string | No | Origin and historical development |
| `notes` | string | No | Cultural context, usage notes, or grammar tips |

## Example Fields

For the `examples` array:
```json
{
  "anun": "Anun vel mirat.",
  "english": "I speak Anun.",
  "notes": "Present tense, first person singular"
}
```

## Translation Guidelines

- Provide the most common translation first
- Include alternative translations if they're equally valid
- Mark specialized or archaic meanings separately in notes
- Context matters: choose translations that make sense in the example sentences

## Part of Speech Abbreviations

- `n` - noun
- `v` - verb
- `adj` - adjective
- `adv` - adverb
- `prep` - preposition
- `pron` - pronoun
- `conj` - conjunction
- `part` - particle
- `det` - determiner
- `num` - numeral

## Frequency Levels

- **high**: Used in everyday conversation (common)
- **medium**: Intermediate vocabulary
- **low**: Specialized, archaic, or rarely used

---

These conventions ensure consistency and make the data useful for both humans and automated tools.
