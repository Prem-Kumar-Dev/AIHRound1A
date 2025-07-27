# Input Directory

This directory contains PDF files to be processed by the Adobe India Hackathon Round 1A PDF Outline Extractor.

## Instructions

1. **Place PDF files here**: Copy all PDF files that need to be processed into this directory
2. **Supported formats**: Standard PDF files (.pdf extension)
3. **File naming**: Any valid filename is supported
4. **Multilingual support**: PDFs in English, Japanese, Hindi, and other Unicode scripts are supported

## Current Files

The following sample PDF files are included for testing:
- `babel-japanese-sample.pdf` - Japanese multilingual test file
- `E0CCG5S239.pdf` - English document sample
- `E0CCG5S312.pdf` - Multi-page technical document
- `E0H1CM114.pdf` - Complex document with multiple headings
- `STEMPathwaysFlyer.pdf` - Educational flyer
- `TOPJUMP-PARTY-INVITATION-20161003-V01.pdf` - Event invitation

## Processing

When the Docker container runs, it will:
1. Automatically scan this directory for all `.pdf` files
2. Extract titles and headings from each PDF
3. Generate corresponding JSON output files in the `output/` directory
4. Process files with multilingual support for proper Unicode handling

## Notes

- Files are processed in alphabetical order
- Processing typically takes <0.2 seconds per file
- Large files and complex layouts are supported
- 1-based page numbering is used in the output (page 1, not page 0)
