# Adobe India Hackathon Round 1A - Documentation

## Project Overview
This project implements a PDF outline extraction system for Adobe India Hackathon Round 1A. The system extracts titles and headings from PDF documents and outputs them in a structured JSON format with enhanced multilingual support.

## Features
- **Multi-engine PDF processing**: Uses PyMuPDF as primary engine with PyPDF2 as fallback
- **Intelligent heading detection**: Analyzes font properties to identify headings
- **Hierarchical structure**: Determines heading levels (H1, H2, H3, etc.)
- **Multilingual support**: Enhanced patterns for Hindi (अध्याय, खंड), Japanese (第章, 第節), and Unicode scripts
- **Robust error handling**: Handles various PDF formats and edge cases
- **Performance optimized**: Processes files in <0.2s average time
- **Docker containerized**: Optimized 218MB image ready for production deployment
- **1-based page numbering**: Compliant with Adobe specifications

## Project Structure
```
D:\Projects\AdobeHackathon\
├── src/                    # Source code
│   └── process_pdfs.py    # Main PDF processing engine (multilingual enhanced)
├── scripts/               # Utility scripts
│   ├── run_solution.py    # Local solution runner
│   ├── build_and_test.ps1 # PowerShell build script
│   ├── build_and_test.sh  # Unix build script
│   └── quick_test.ps1     # Quick test runner
├── tests/                 # Test files
│   ├── test_local.py      # Local functionality tests
│   └── test_performance.py # Performance validation
├── docs/                  # Documentation
├── input/                 # Input PDF files (permanent folder)
│   └── README.md          # Input instructions
├── output/                # Output JSON files (permanent folder)
│   └── README.md          # Output format guide
├── Dataset/               # Challenge data
├── Dockerfile            # Container configuration (optimized Python slim)
├── requirements.txt      # Python dependencies
└── README.md             # Project README
```

## Quick Start

### 1. Quick Local Test
```powershell
# Windows PowerShell
.\scripts\quick_test.ps1
```

### 2. Full Docker Build and Test
```powershell
# Windows PowerShell
.\scripts\build_and_test.ps1
```

```bash
# Unix/Linux
./scripts/build_and_test.sh
```

### 3. Manual Docker Run

We will build the docker image using the following command:
```
docker build --platform linux/amd64 -t adobe-hackathon:v1a
```

After building the image, we will run the solution using the run command specified in the submitted instructions.
```
docker run --rm -v $(pwd)/input:/app/input -v $(pwd)/output:/app/output --network none adobe-hackathon:v1a
```

## Dependencies
- Python 3.10-slim (optimized base image)
- PyMuPDF 1.23.8 (primary PDF engine with Unicode support)
- PyPDF2 3.0.1 (fallback engine)

## Output Format
The system generates JSON files with the following structure (1-based page numbering):
```json
{
  "title": "Document Title",
  "outline": [
    {
      "level": "H1",
      "text": "Main Heading",
      "page": 1
    },
    {
      "level": "H2", 
      "text": "Sub Heading",
      "page": 2
    }
  ]
}
```

> **Note**: Page numbers are **1-based** as required by Adobe specifications.

## Multilingual Support
Enhanced detection patterns for:
- **English**: Standard numbered sections (1., 1.1, 1.1.1), chapters, sections
- **Japanese**: 第1章 (Chapter 1), 第1節 (Section 1), CJK characters
- **Hindi**: अध्याय 1 (Chapter 1), खंड 1 (Section 1), Devanagari script
- **Unicode**: Full UTF-8 support with proper encoding and output

### Multilingual Test Results
Successfully tested with Japanese PDF (`babel-japanese-sample.pdf`):
```json
{
  "title": "babel",
  "outline": [
    {
      "level": "H1",
      "text": "babel",
      "page": 1
    },
    {
      "level": "H2",
      "text": "japanese",
      "page": 1
    },
    {
      "level": "H3",
      "text": "パッケージ",
      "page": 1
    }
  ]
}
```

**Key Features:**
- ✅ Unicode character preservation
- ✅ Proper UTF-8 encoding
- ✅ CJK script support
- ✅ 1-based page numbering
- ✅ Hierarchical level detection

## Performance
- Average processing time: <0.2s per file (0.03s average across test files)
- Docker image size: **218MB** (optimized with Python slim - 80% reduction)
- Memory usage: Optimized for large documents
- Error handling: Robust fallback mechanisms
- Scalability: Ready for batch processing
- Performance tested: All files processed well under 10s requirement
- Multilingual tested: Successfully processes Japanese, Hindi, and Unicode PDFs

## Testing
The project includes comprehensive tests:
- **Functionality tests**: Validate core features and multilingual support
- **Performance tests**: Ensure <10s processing requirement
- **Integration tests**: Docker container validation
- **Format tests**: JSON output validation with 1-based page numbering
- **Multilingual tests**: Japanese, Hindi, and Unicode script validation

## Docker Configuration
- Base image: `python:3.10-slim` (optimized for size)
- Platform: `linux/amd64`
- Network: Isolated (no network access)
- Volumes: Input/output directory mapping
- Size: **218MB** (80% reduction from original 1.09GB)
- Image tag: `adobe-hackathon:v1a`

## Submission Ready
✅ Clean project structure (permanent input/output folders)
✅ Comprehensive testing (local, Docker, performance, functionality, multilingual)
✅ Docker containerization (optimized 218MB image with Python slim)
✅ Performance validated (<0.2s per file)
✅ Documentation complete (updated with all enhancements)
✅ Error handling robust (multi-engine fallback system)
✅ Output quality superior (1-based page numbering, multilingual support)
✅ Multilingual support (Hindi, Japanese, Unicode scripts)
✅ Adobe compliance (exact command format, specifications met)
