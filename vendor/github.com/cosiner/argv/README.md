# Argv

[![GoDoc](https://img.shields.io/badge/godoc-reference-blue.svg?style=flat)](https://godoc.org/github.com/cosiner/argv) 
[![Build Status](https://travis-ci.org/cosiner/argv.svg?branch=master&style=flat)](https://travis-ci.org/cosiner/argv)
[![Coverage Status](https://coveralls.io/repos/github/cosiner/argv/badge.svg?style=flat)](https://coveralls.io/github/cosiner/argv)
[![Go Report Card](https://goreportcard.com/badge/github.com/cosiner/argv?style=flat)](https://goreportcard.com/report/github.com/cosiner/argv)

Argv is a  library for [Go](https://golang.org) to split command line string into arguments array. 

# Documentation
Documentation can be found at [Godoc](https://godoc.org/github.com/cosiner/argv)

# Example
```Go
func TestArgv(t *testing.T) {
    args, err := Argv(" ls   `echo /`   |  wc  -l ", func(backquoted string) (string, error) {
		return backquoted, nil
	}, nil)
	if err != nil {
		t.Fatal(err)
	}
	expects := [][]string{
		[]string{"ls", "echo /"},
		[]string{"wc", "-l"},
	}
	if !reflect.DeepEqual(args, expects) {
		t.Fatal(args)
	}
}
```

# LICENSE
MIT.
