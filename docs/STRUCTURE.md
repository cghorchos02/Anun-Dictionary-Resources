# Anun Dictionary Structure Guide

This document explains the overall structure and how all components fit together.

## Directory Organization

### `/data` - All Language Data

#### `/data/vocabulary/` - Lexicon organized by part of speech
- **nouns.json** - Nouns, organized with related inflection patterns
- **verbs.json** - Verbs with conjugation information
- **adjectives.json** - Adjectives with agreement patterns
- **adverbs.json** - Adverbs and adverbial expressions
- **prepositions.json** - Prepositions with case government
- **particles.json** - Function words, grammatical particles

Each file follows the same metadata + entries structure for consistency.

#### `/data/index.json` - Master Index
Quick lookup table mapping:
- English → Anun
- Anun → English  
- All vocabulary across all part-of-speech files

**Updated automatically** when vocabulary files change (or manually updated as needed).

#### `/data/grammar/` - Grammatical Information (Future)
- **phonology.json** - Sound system, phonotactics
- **inflections.json** - Detailed inflection tables and patterns
- **syntax.json** - Word order, clause structure, coordination
- **cases.json** - Case system (if applicable)

#### `/data/texts/` - Authentic and Practice Content
- **sample_texts.json** - Full texts with translations and interlinear glosses
- **practice_sentences.json** - Graded sentences for learning

### `/docs` - Documentation
- **CONVENTIONS.md** - Formatting standards (what you're following)
- **STRUCTURE.md** - This file (how everything relates)

### `/tools` - Scripts and Utilities (Future)
For processing, exporting, and generating:
- JSON validators
- Export to CSV/markdown for websites
- Frequency analysis
- Dependency checking

## Data Flow

```
User edits vocabulary files
    ↓
Follows CONVENTIONS.md format
    ↓
Commits to GitHub
    ↓
index.json updated (maintains master lookup)
    ↓
Tools can export to website/other formats
    ↓
Grammar files build on vocabulary foundation
    ↓
Sample texts and practice sentences use vocabulary + grammar
```

## Vocabulary Entry Lifecycle

### Phase 1: Entry Creation
1. Add entry to appropriate POS file (nouns.json, verbs.json, etc.)
2. Include required fields (id, anun, english, definition, examples)
3. Fill optional fields as you develop the language (etymology, related_words)

### Phase 2: Enrichment
- Add example sentences
- Link to related vocabulary
- Document etymology
- Add cultural/usage notes

### Phase 3: Integration
- Entry appears in index.json for cross-referencing
- Used in practice sentences
- Referenced in grammar documentation

### Phase 4: Grammar Integration
- Verb entries expanded with conjugation patterns
- Noun entries linked to inflection information
- Adjective entries show agreement patterns

## Frequency Levels

Vocabulary is tagged with frequency to support progressive learning:

- **high** (★★★) - Everyday vocabulary, teach first
- **medium** (★★) - Intermediate level
- **low** (★) - Specialized, technical, archaic

This supports building curricula and learner materials at different difficulty levels.

## Related Words Field

The `related_words` array creates a vocabulary web:
- Root word → derived words
- Synonyms
- Antonyms
- Semantic families

Example:
```json
{
  "anun": "anun",
  "related_words": ["anune", "anunis", "anun-mir"]
}
```

This allows tools to generate word families and help learners see connections.

## Example Fields

Each entry has at minimum ONE example, but can have more to show:
- Different grammatical patterns
- Different meanings of polysemous words
- Formal vs. informal usage
- Different contexts

## Future Expansion

Once vocabulary reaches a critical mass:

1. **Grammar Documentation** will reference vocabulary by ID
2. **Practice Sentences** will mix new vocabulary with previously learned words
3. **Sample Texts** will use graded vocabulary for difficulty levels
4. **Tools** will generate learning materials automatically

## Working with the Data

### For Manual Editing
- Use GitHub's web editor for quick edits
- Use a local editor for bulk additions
- Follow CONVENTIONS.md exactly
- Validate JSON before committing

### For Automated Processing (Future)
- Query by POS (part_of_speech)
- Filter by frequency level
- Group by etymology
- Generate related word networks
- Export for website/flashcards/etc.

---

**Key Principle**: Structure now, scale later. The system is designed to handle growth from 1 word to 10,000+ words without major redesigns.
