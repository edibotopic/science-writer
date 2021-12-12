# Science Writer

[Science Writer](https://github.com/edibotopic/science-writer) is an extension for [Visual Studio Code](https://code.visualstudio.com/) that aims to reduce time spent on repetitive aspects of **scientific writing**. It aims to achieve this using snippets and boilerplate that can be triggered when editing [markdown](https://help.github.com/articles/markdown-basics/) files within VSCode.

The extension might be especially useful for scientific novices who are unfamiliar with the conventions of scientific writing.

When combined with powerful tools like [LaTeX](https://www.latex-project.org/get/), [Pandoc](https://pandoc.org/) and [Markdown Preview Enhanced](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced#:~:text=Markdown%20Preview%20Enhanced%20is%20an,or%20%E5%BE%AE%E4%BF%A1%E6%94%AF%E4%BB%98%20Wechat%20Pay.), Science Writer allows the efficient drafting of scientific documents that can be exported in a variety of formats (`.docx`, `.pdf`).

## Features

The extension is written to ensure the sensible formatting of both Word files and LaTeX pdfs exported *via* [Markdown Preview Enhanced](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced#:~:text=Markdown%20Preview%20Enhanced%20is%20an,or%20%E5%BE%AE%E4%BF%A1%E6%94%AF%E4%BB%98%20Wechat%20Pay.) or [Pandoc](https://pandoc.org/).

For example, the `write manuscript` snippet generates `YAML` at the top of the document for defining *title*, *authors*, *affiliations* in addition to an *abstract*. Users can <kbd>tab</kbd> through these, modifying as needed. Dropdown menus for common completion options are also provided for certain snippets (e.g., specifying export doc, figure name, SI unit choice).

**Note:** to trigger snippet suggestions when editing markdown files in VSCode press <kbd>ctrl</kbd>+<kbd>space</kbd>. Pressing <kbd>ctrl</kbd>+<kbd>space</kbd> again while a snippet is highlighted will show a description of the snippet. Pressing <kbd>enter</kbd> will insert the snippet.

Science Writer contains snippets for the following categories:

### Boilerplate templates
    
- *submit paper*: template for letter to journal editor accompanying paper submission

- *response to reviewers*: template for letter to journal outlining responses to reviewer comments

- *write manuscript*: template for journal article with front-matter (title, authors, affiliations, contact, abstract) and article skeleton (introduction, materials & methods, etc.)

- *acknowledge*: template for completing acknowledgements section

### Math and statistics

- *p-value S*: appends a significant P-value with dropdown menu for level of significance

- *p-value NS*: appends a non-significant P-value

- *mean value*: inserts an average ± standard deviation

- *math inline*: places cursor between `$<here>$` to facilitate typing of equations on same line

- *math ownline*: places cursor between `$$<here>$$` to facilitate typing of equations on next line

### Scientific units

**Note**: these snippets must be inserted within a math block - `$<here>$` or `$$<here>$$` to be rendered in markdown, LaTeX or Word as an equation.

- *Units base*: base SI units in dropdown menu

- *Units special*: special SI units in dropdown menu

- *Units derived common*: common derived SI units in dropdown menu

- *Constants*: common constants uses in scientific equations in dropdown menu

### Citations

Includes a range of options for adding citations.

Snippet invoked with `cite` followed by `number of authors (one,two,three,many)` and whether the citation is at `END` of sentence or `PART` of sentence. For example, `cite many END` yields:

(`surname` *et al.,* `year`)

User can <kbd>tab</kbd> to `year` after editing `surname`.

### References

- *Ref paper*: reference a journal article

- *Ref book authored*: reference a book authored by a person or people

- *Ref book chapter*: reference a book chapter in an edited volume

### Tables and figures

- *Figure*: adds an image from a folder in the current working directory and includes a figure legend. **Note:** by default it is assumed images are found in a `figures` folder in the project directory

- *Table*: adds a basic markdown table and table caption

## Requirements

The following are recommended for the effective use of this extension:

- [VSCode](https://code.visualstudio.com/) to edit text and install extensions
- [Markdown Preview Enhanced](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced#:~:text=Markdown%20Preview%20Enhanced%20is%20an,or%20%E5%BE%AE%E4%BF%A1%E6%94%AF%E4%BB%98%20Wechat%20Pay.) (VSCode extension) for rendering markdown and GUI-based export functionality
- [Markdown Table](https://marketplace.visualstudio.com/items?itemName=TakumiI.markdowntable) (VScode extension) for easier manipulation of markdown tables
- [Pandoc](https://pandoc.org/) to convert markdown to various filetypes. [Installation instructions here](https://pandoc.org/installing.html)
- [LaTeX](https://www.latex-project.org/get/) for typesetting of pdf documents in LaTeX style. [TeX Live is often recommended](https://www.tug.org/texlive/)
- [Microsoft Word](https://www.microsoft.com/en-ie/microsoft-365/word) to view .doc files generated by Pandoc

Markdown is a very simple and quick way to write documents, and it has most of the basic formatting one needs for a scientific document (italics, bold, headers, math); however, the `.md` file typically needs to be converted to a suitable filetype. When circulating among colleagues it is common to send either a `.docx` (Word) or a `.pdf` (from Word or LaTeX). Some journals expect raw `.doc` (Word) or `.tex` (LaTeX) files that are then "built" into a `.pdf` by the publisher. Others accept `.pdf` files directly.

*Pandoc* allows all of the necessary file conversions. *Markdown Preview Enhanced* has a GUI interface for making several of them by pointing-and-clicking. If you want to convert markdown to a raw `.tex` file you need to [customise](https://github.com/shd101wyy/markdown-preview-enhanced/issues/647) the `YAML` that is parsed when using the GUI export options; however, it might be easier in this case to simply use the relevant command in the terminal after you change directory (cd) to your project folder:

```bash
cd myProject
pandoc -s myDoc.md -o myDoc.tex
```

This will create a `.tex` file in the same directory as the `.md` file. Other relevant commands for terminal user are:

```bash

pandoc -s myDoc.md -o myDoc.docx
pandoc -s myDoc.docx -o myDoc.pdf
pandoc -s myDoc.tex -o myDoc.pdf
pandoc -s myDoc.md -o myDoc.pdf
```

LaTeX has far more powerful formatting and typesetting capabilities than markdown but writing LaTeX documents can be cumbersome. One approach is to rapidly draft a manuscript in markdown before typesetting in LaTeX to render a more polished document. You can edit, build and preview LaTeX files from within VSCode using the excellent [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) extension (still requires LaTeX to be installed on your device).

## Limitations

The extension is intended to improve the ease and efficiency with which scientists can write, not to generate documents that can be submitted to all scentific journals unmodified.

Its design is based on the author's *particular* experience writing for journals in an applied life science (food science and technology). There are no agreed-upon universal principles for science writing that apply to all journals, so modifications might be needed for your specific use-case. Practices and norms will vary across disciplines (sections, citation/referencing style, formatting, etc.).

Many scientific publishers have style guides and templates for their manuscripts that might deviate from those generated using this extension. A LaTeX template for converting `.md` files into `.pdf` files formatted as per the requirements of Elsevier (one of the largest publishers) is [available here](https://github.com/j-jith/pandoc-elsevier-template).

## Release Notes

See [CHANGELOG](CHANGELOG.md)

## To-do

- [ ] Add gifs to README
- [ ] Make snippet names shorter and more consistent
- [ ] Food-specific units (e.g., BMI, calories) for reasons of professional bias
- [ ] Common material/substance names *via* dropdown menus (e.g., elements, amino acids, vitamins)
- [ ] More boilerplate (e.g., hypotheses, replication, legends with statistics)
- [ ] Check if useful to provide snippets for different referencing styles

## For more information

* [Visual Studio Code's Markdown Support](http://code.visualstudio.com/docs/languages/markdown)
* [Markdown Syntax Reference](https://help.github.com/articles/markdown-basics/)

**If you use the extension or have any ideas for improving it then please email me or post an issue**
