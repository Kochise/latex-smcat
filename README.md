# latex-smcat
LaTeX package to interface with state-machine-cat (npm)

Source : https://github.com/Kochise/latex-smcat

## installation

Get 'nvm' for Windows : https://github.com/coreybutler/nvm-windows/releases<br>
Uncompress/install it where you need.<br>

```batch
\>cd nvm
\nvm>nvm install 12.17.0
\nvm>nvm use 12.17.0
\nvm>node -v
v12.17.0
\nvm>npm install --global state-machine-cat

xcopy /c /h /e /r /q /y latex-smcat <miktex>\texmfs\install\tex\latex\smcat
start "" "<miktex>\miktex-portable.cmd"
```

Install version 7.3.0 at minimum because it brings EPS support that is currently superior to SVG.

Refresh the filename database.<br>
Update the package database.<br>
You should be ready to go.<br>

Alternatively, you can use https://github.com/Kochise/win_portable

## usage

See https://github.com/sverweij/state-machine-cat<br>

In your preamble :

```latex
\def\imagepath{./images}
\graphicspath{{\imagepath/}}
\usepackage[imagepath=\imagepath]{smcat}
```

In your document :

```latex
%\begin{smcat}[width]{caption}{refname}
\begin{smcat}[8cm]{smcat caption example}{smcatexample}
initial,
doing: entry/ write unit test
       do/ write code
       exit/ ...,
# smcat recognizes initial
# and final states by name
# and renders them appropriately
final;

initial      => "on backlog" : item adds most value;
"on backlog" => doing        : working on it;
doing        => testing      : built & unit tested;
testing      => "on backlog" : test not ok;
testing      => final        : test ok;
\end{smcat}
```

![smcat](https://raw.githubusercontent.com/Kochise/latex-smcat/master/smcat.png)

## options

What is available through 'smcat' :

```
% Output the version number
-V, --version

% Output type (svg|eps|ps|ps2|dot|smcat|json|ast|scxml|oldsvg|scjson, default: "svg")
-T, --output-type [type]

% Input type (smcat|json|scxml, default: "smcat")
-I, --input-type [type]

% Rendering engine (dot|circo|fdp|neato|osage|twopi, default: "dot")
-E, --engine [type]

% Rendering direction (top-down|bottom-top|left-right|right-left, default: "top-down")
-d, --direction [dir]

% File to write to. use - for stdout
-o, --output-to [file]

% Graph attributes to pass to the dot render engine
--dot-graph-attrs [string]

% Node attributes to pass to the dot render engine
--dot-node-attrs [string]

% Edge attributes to pass to the dot render engine
--dot-edge-attrs [string]

% Transform forks and joins into transitions (!experimental!)
--desugar

% Display license and exit
-l, --license

% Output usage information
-h, --help
```

Cannot be specified on a group basis, only in the preamble.<br>
Just add the requested parameters without the leading/separator dash(es).<br>

```latex
\usepackage[E={osage}]{smcat}
```

or :

```latex
\usepackage[dotnodeattrs={string}]{smcat}
```

Avoid :

```
o, outputto	: because using the refname
l, license	: because useless
h, help		: because useless
V, version	: because useless, unless debug log
```

## limitations

Your imagination.

## greetings

Based on https://github.com/dakusui/latex-ditaa<br>
Also interested into https://github.com/sile-typesetter/sile<br>
