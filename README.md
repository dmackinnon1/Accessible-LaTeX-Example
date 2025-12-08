# Accessible-LaTeX-Example

The LaTeX source code for the manuscript makes use of the latest PDF tagging support available in Tex Live 2025. Please see the LaTeX team's tagging instructions for more information.

## Overleaf requirements

To make use of the tagging support now available in LaTeX, you need to make sure that the [TeX Live version and compiler](https://docs.overleaf.com/getting-started/recompiling-your-project/selecting-a-tex-live-version-and-latex-compiler) of your project are set properly.

- With 2025 TeX Live, \LaTeX{} can now produce tagged PDFs automatically -- a key requirement for accessibility. Additional accessibility features are being added on an ongoing basis to the TeX Live builds. Currently, [new projects created in Overleaf](https://www.overleaf.com/blog/tex-live-2025-is-now-available) use the 2025 TeX Live tested release, and for those who need even more recent releases, a rolling updated version of TeX Live is available through the [Overleaf Labs](https://www.overleaf.com/labs/participate) program. For most requirements, the standard 2025 TeX Live image should be sufficient, but for those who wish to use the most recent features provided by the LaTeX team, the rolling version provided by Overleaf Labs may be required.

- The settings in this document require that the compiler used for this project needs to be explicitly set to **LuaLaTeX** in Overleaf.

## GitHub workflows
This project includes some GitHub workflow definitions that can be used to run an accessibility test against the generated PDF.

| workflow | status | notes |
|--------|--------| ------------|
| Latest PDF of document | ![Dynamic JSON Badge](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fdmackinnon1%2FAccessible-LaTeX-Example%2Fmain%2Fbuild-info%2Fcompile-build-info.json&query=lastBuild&style=flat-square&label=Last%20PDF-Compile&labelColor=blue&color=black)| [View the latest PDF](output/main.pdf) |

The **Compile PDF (latexmk,lualatex)** workflow will compile the source and save the PDF in the project. Overleaf does not save the compiled PDF in the project, but if you are using GitHub Sync, you can run the GitHub workflow on the GitHub side do this. In general, it is not recommended to save a copy of the PDF in the project, but it is done here to simplify the accessibility testing process. The PDF compiled by the GitHub workflow is saved as main.pdf, and the build time for this PDF can be found in the ./build-info/compile-build-info.json file.

| workflow | status | notes |
|--------|--------| ------------|
| PDF accessibility verification |![Dynamic JSON Badge](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fdmackinnon1%2FAccessible-LaTeX-Example%2Fmain%2Fbuild-info%2Fa11y-build-info.json&query=lastBuild&style=flat-square&label=Last%20Generated&labelColor=blue&color=black)<br> ![Dynamic Regex Badge](https://img.shields.io/badge/dynamic/regex?url=https%3A%2F%2Fraw.githubusercontent.com%2Fdmackinnon1%2FAccessible-LaTeX-Example%2Frefs%2Fheads%2Fmain%2Foutput/a11y-statement.txt&search=(.)*ua2&label=Accessibility%20Test)|[See the full report](output/a11y-report.json)|

The **Check PDF Accessibility (veraPDF)** workflow will install and run [veraPDF](https://github.com/veraPDF) to generate an accessibility report. Two reports are generated: a simple a11y-statement.txt report and a more detailed a11y-report.json report. The build time for the report generation can bre found in ./build-info/a11y-build-info.json. This test uses the `ua-2 pdf tagging` profile provided by veraPDF.

