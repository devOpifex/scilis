# Scilis

Secure cookies for [ambiorix](https://ambiorix.dev).

Signs (and unsigns) cookies to ensure they are not tempered with by clients.

## Installation

Get it from Github.

```r
remotes::install_github("devOpifex/scilis")
```

## Example

```r
library(scilis)
library(ambiorix)

app <- Ambiorix$new()

# use an environment variable
app$use(scilis("secret"))

app$get("/", \(req, res) {
  print(req$cookie)
  res$cookie(
    "MYCOOKIE",
    "This is secure"
  )
  res$send("Added cookie")
})

app$start()
```
