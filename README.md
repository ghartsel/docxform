# RapidMarkup

RapidMarkup is a Python3 technical documentation authoring tool that converts ODF content to popular markup formats. This lets you use LibreOffice as a WYSIWYG editor to create content suitable for docs-as-code content management.

## Features

- WYSIWYG authoring
- One-click semantic highlighting
- Supports the docs-as-code content management paradigm

## Motivation

- The belief that ASCII-based editors and markup are inadequate for serious technical documentation (documentation is *not* email) and that content cannot be entirely decoupled from presentation (form *does* follow function).
- This mechanism permits semantic highlighting independent of the rendered format, which a strength ReStructuredText already holds over Markdown.
- Single-source documentation is supported at a high level. LibreOffice documents can be formatted for high usability and are easily published in native or PDF offline formats for document review or publishing. Markup processors combined with CSS give you the online presentation format from the same source document.
- WYSIWYG authoring tools, when simply configured and not burdened with excessive features, provide a more productive authoring environment than simple ASCII text editors. The time saved and enhanced quality of using LibreOffice far outweighs the convenience of "never having to leave the keyboard."
- Under-the-hood LibreOffice is XML, which is a natural representation for the hierarchical structure of technical documentation.

## Prerequisites

- Python 3
- `pip3 install -r requirements.txt`
- Free and open source LibreOffice (https://www.libreoffice.org/). Also, distributed with Ubuntu.

## Usage

``` python
    python3 rapidmu.py [-h] -fn FILENAME [-m {md,MD,rst,RST}]
```

RapidMarkup currently generates ReStructuredText and Markdown (GitHub flavor) document formats. You can run the program on the sample.fodt file to convert a sample LibreOffice file and see the generated formats and supported semantic styles.

Options:

``` bash
    -h [HELP] This Usage.


    -fn [FILENAME] Source file name.

    -m [MARKUP] Output markup format; md/MD = Markdown, rst/RST = ReStructuredText
```

Output is to STDIO.

Docxform currently generates ReStructuredText and Markdown (GitHub flavor) document formats. You can run the program on the sample.fodt file to convert a sample LibreOffice file and see the generated formats and supported semantic styles.

### Convert Libreoffice to Markdown

1. Create source file using LibreOffice.
2. Convert .fodt source to .md format:

    Example:

``` python
    python3 rapidmu.py -fn sample.fodt -m MD > sample.md
```

### Convert Libreoffice to reStructuredText

1. Create source file using LibreOffice.
2. Convert .fodt source to .rst format:

    Example:

``` python
    python3 rapidmu.py -fn sample.fodt -m RST > sample.rst
```

## Notes

If you are using a docs-as-code documentation methodology where your documentation source is version controlled like the software source, you can store, access and manage the LibreOffice .fodt-formatted files directly in the repository in the same way as any other ASCII source.

The current version of RapidMarkup supports styles defined as LibreOffice **Custom Styles**. These styles support technical software documentation semantic elements.

## TODO:

- Define additional semantic styles to support typical hardware and software documentation requirements, which might be called *specialization* in the DITA world. This involves:
    - Define a new Custom Style in LibreOffice.
    - Add the XSLT support for the new styles in the .xsl files.
- Handle unmatched elements.
- Add support for character style mapping (ex: T3).
- Add XSLT support for other markup formats, such as AsciiDoc, other Markdown flavors, and the various wiki formats.
- Support default Google Docs styles.
