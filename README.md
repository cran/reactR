# reactR

A set of convenience function with local dependencies for using [`React`](https://facebook.github.io/react) in `R`.  This is modeled after the `html_dependency_*` functions from RStudio's [`rmarkdown`](https://github.com/rstudio/rmarkdown) package.

## Installation

You can install reactR from github with:

```R
# install.packages("devtools")
devtools::install_github("timelyportfolio/reactR")
```

## Example

```R
library(reactR)
library(htmltools)

browsable(attachDependencies(
  tags$script(
  "
    ReactDOM.render(
      React.createElement(
        'h1',
        null,
        'Powered by React'
      ),
      document.body
    )
  "
  ),
  html_dependency_react()
))
```

`reactR` also uses `V8` if available to transform `JSX` and `ES2015` code.

```R
library(reactR)
library(htmltools)

browsable(
  attachDependencies(
    tags$script(
      babel_transform('ReactDOM.render(<h1>Powered By React/JSX</h1>,document.body)')
    ),
    html_dependency_react()
  )
)
```

## Contributing and Code of Conduct

I welcome contributors.  Help make this package great.  Please note that this project is released with a [Contributor Code of Conduct](CONDUCT.md). By participating in this project you agree to abide by its terms.
