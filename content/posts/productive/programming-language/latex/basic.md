---
title: "basic"
draft: false
---


#latex

# Latex

Latex is used for creating complex Notes for subjects like mathmatics( with lots of formulas), research paper or use can it for simple notes. Once done you can convert `.tex` file to pdf(Portable Document Format). 

### Basic Layout

Creating document with `latex` is simple. In contrast to word, you start off with the plain text file(tex file) which contains latex code and the actual content. LaTeX uses control statement, which specifies how your content should be formatted. After that you can use latex compiler to compile .tex file to .pdf file.   

Example, 

```tex

\documentclass{article}
\begin{document}
Hello world
\end{document}

```
- Once your converted this `.tex` file into .pdf, you can see in .pdf file a blank white page contains the word *Hello world*.

### Adding a title to the page

```tex

\documentclass{article}

\title{My document}
\date{2020-06-25}
\author{John Doe}


\begin{document}
\maketitle
\newpage

Hello World!

\end{document}

```
- The statements `\title`,`\date` and `\author` are not within the documents environment, so they will not directly not show in our document. The area before our main document called *preamble*.   

If we compile again, we will see a nicely formatted title page, but we can spot a page number at bottom of the title page. What if we don't want any page number on the title page.We can remove it by telling latex to remove it from the bottom of the page. This can be done by adding `pagenumbering{gobble}` command then on the next page change it back by using `pagenumbering{arebic}`.

### Sectioning elements

Latex offer us commands to generate section heading and number them automatically. The command for creating sections are straightforward.

```tex

\section{}
\subsection{}
\subsubsection{}

\paragraph{}
\subparagraph{}

```
### Packages

Latex offers us a bunch of functions by default, but in some situation its become handy to use some other *package*. To import packages in Latex you simply add this command `\usepackage` 

* Import the packages in preamble area, otherwise it will through error.


```tex

\documentclass{article}

\usepackage{umsmath}

\begin{document}
Hello World!

\begin{equation}
f(x)=x^2
\end{equation}

\end{document}

```

### Adding a picture  or figure

Sometimes it's necessary to add pictures in your document.So lets see how we can add them.

- Using Latex all pictures will be indexed automatically and tagged with successive number when using the figure environment and the graphicx packages

```tex
\documentclass{article}
\usepackage{graphicx}

\begin{document}
    \includegraphics[width=\linewidth]{figure.png}
    \caption{a figure}
    \label{fig:figure1}
\end{document}

Figure \ref{fig:figure1} show a figure.

\end{document}

```
- This syntax is enough to show a captioned figure in latex.
- The *Figure* environment is enough to handle numbering and positioning of the image within the document.

#### Image positioning 

Sometime you will see the image position within document is not positioned according to your expectation. If your current page contain too much content then try to show image on the same page, this will not work. The image will be viewed on next page and that's probably not what we want.

- To prevent this behaviour,it's necessary to set the *float* value for the figure environment.

`\begin{figure}[h!]`

- Setting the float `[h!]` behind the figure environment `\begin` tag will force document to show the figure on current page.
- Possible values are

- h(here) - same location
- t(top) - top of the page
- b(bottom) - bottom of the page
- p(page) - on the extra page
- !(override) - will force the specified location.

* use `\hfill` to show two image side by side.

```tex
\begin{figure}[htbp]
    \centering
    \begin{subfigure}[b]{0.48\linewidth}
	 \includegraphics[width=\linewidth]{img.png}
	 \caption{risk-return-a}     
    \end{subfigure}
    \hfill
    \begin{subfigure}[b]{0.48\linewidth}
	    \includegraphics[width=\linewidth]{img.png}
	    \caption{risk-return-b}
    \end{subfigure}
    \caption{risk-return}
    \label{fig:risk}
	
\end{figure}
```
