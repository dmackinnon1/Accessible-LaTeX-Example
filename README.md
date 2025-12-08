## GitHub workflows
This project includes some GitHub workflow definitions that can be used to run an accessibility test against the generated PDF.

| workflow | status | notes |
|--------|--------| ------------|
| Latest PDF of slides | ![Dynamic JSON Badge](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fdmackinnon1%2FAccessible-LaTeX-Example%2Fmain%2Fbuild-info%2Fcompile-build-info.json&query=lastBuild&style=flat-square&label=Last%20PDF-Compile&labelColor=blue&color=black)| [View the latest PDF](output/main.pdf) |

The **Compile PDF (latexmk,lualatex)** workflow will compile the source and save the PDF in the project. Overleaf does not save the compiled PDF in the project, but if you are using GitHub Sync, you can run the GitHub workflow on the GitHub side do this. In general, it is not recommended to save a copy of the PDF in the project, but it is done here to simplify the accessibility testing process. The PDF compiled by the GitHub workflow is saved as main.pdf, and the build time for this PDF can be found in the ./build-info/compile-build-info.json file.

| workflow | status | notes |
|--------|--------| ------------|
| PDF accessibility verification |![Dynamic JSON Badge](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fdmackinnon1%2FAccessible-LaTeX-Example%2Fmain%2Fbuild-info%2Fa11y-build-info.json&query=lastBuild&style=flat-square&label=Last%20Generated&labelColor=blue&color=black)<br> ![Dynamic Regex Badge](https://img.shields.io/badge/dynamic/regex?url=https%3A%2F%2Fraw.githubusercontent.com%2Fdmackinnon1%2FAccessible-LaTeX-Example%2Frefs%2Fheads%2Fmain%2Foutput/a11y-statement.txt&search=(.)*ua2&label=Accessibility%20Test)|[See the full report](output/a11y-report.json)|

The **Check PDF Accessibility (veraPDF)** workflow will install and run the VeraPDF accessibility checker. Two reports are generated: a simple a11y-statement.txt report and a more detailed a11y-report.json report. The build time for the report generation can bre found in ./build-info/a11y-build-info.json.

