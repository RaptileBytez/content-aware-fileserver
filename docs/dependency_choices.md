# Dependency Choices

This document explains the choices of dependencies over alternatives,
based on practical testing with real-world documents.

## PDF Text Extraction: pdfplumber vs pypdf vs pymupdf

All three libraries were tested against 5 documents:
- 3 sample invoices (digitally created)
- 1 real-world invoice (Amazon)
- 1 real-world invoice (Lohnsteuerhilfe e.V.)

### Findings

For simple, digitally created PDFs all three libraries produced comparable results.

For real-world documents the differences were significant:

**pypdf** struggled with complex layouts — table column headers were merged
or appeared in wrong order, and summary values were separated from their
labels. This makes it unreliable for LLM-based extraction where context
and reading order are critical.

**pymupdf** performed well on the Amazon invoice, correctly preserving column
headers and value assignments. However, it failed on the Lohnsteuerhilfe
document — table columns appeared in reverse order and summary values were
detached from their labels, similar to pypdf. Both libraries also incorrectly
placed page markers (e.g. "Seite 1 von 1") mid-document instead of at the end.

**pdfplumber** consistently preserved table structure and kept values together
with their labels across all tested documents. The reading order was closest
to the visual original, particularly for the Lohnsteuerhilfe invoice where
the other libraries failed noticeably.

### Test Results Summary

| Document | pypdf | pymupdf | pdfplumber |
|---|---|---|---|
| Sample invoices | ✅ | ✅ | ✅ |
| Amazon invoice | ⚠️ | ✅ | ⚠️ |
| Lohnsteuerhilfe invoice | ❌ | ⚠️ | ✅ |

### Conclusion

`pdfplumber` is the preferred default for this project based on its consistent
performance across all tested document types — particularly its correct handling
of table structures in complex real-world documents.

Results varied by document type, suggesting that no single library is universally
superior. A future improvement could implement a fallback strategy that evaluates
multiple libraries per document. This will be revisited in later project phases.