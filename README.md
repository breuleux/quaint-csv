
quaint-csv
==========

CSV support for the `data` macro in
[Quaint](http://breuleux.github.io/quaint).


## Install

    quaint --setup csv



## Usage

```quaint
format table ::
  data csv ::
    Name,Job
    Alice,accountant
    Bob,baker
```

Importing from a file:

```quaint
rows => data :: jobs.csv

each {rows} row ::
  * {row.Name}'s job is {row.Job}

;; output:
;; * Alice's job is accountant
;; * Bob's job is baker
```


## Sample configuration

This configuration entry must be added in the `plugins` section of
`quaint.json`:

```json
"csv": {
  "lineSeparator": "\n",
  "separator": ",",
  "quote": "\"",
  "trim": false,
  "useHeader": true
}
```


## Options


### lineSeparator

The separator character for lines/records (default: `\n`)


### separator

The separator character (default: `,`)


### quote

The character used for quoting (default: `"`)


### trim (boolean)

Whether to trim field values. (default: false)


### useHeader (boolean)

Whether to use the first line as field names or not. (default: true)

If this is true, then the result is an array of records with the names
taken from the first line of the file, otherwise it will be an array
of arrays.

