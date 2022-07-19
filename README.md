blockchaininfo
==========

[![Build Status](https://travis-ci.org/mshogin/blockchaininfo.svg?branch=master)](https://travis-ci.org/mshogin/blockchaininfo)

Go Client for the Blockchain Data API https://blockchaininfo.info/api/blockchaininfo_api

Documentation: https://godoc.org/github.com/mshogin/blockchaininfo

## Installation

```
go get github.com/mshogin/blockchaininfo
```

## Example

```go
package main

import (
  "github.com/mshogin/blockchaininfo"
  "fmt"
)

func main() {

	c, e := blockchaininfo.New()
	resp, e := c.GetAddress("162FjqU7RYdojnejCDe6zrPDUpaLcv9Hhq")
	if e != nil {
		fmt.Print(e)
	}

	fmt.Println(resp.Hash160)
	fmt.Println(resp.Address)
	fmt.Println(resp.NTx)
	fmt.Println(resp.TotalReceived)
	fmt.Println(resp.TotalSent)
	fmt.Println(resp.FinalBalance)

	for i := range resp.Txs {
		fmt.Println(resp.Txs[i].Result)

		for j := range resp.Txs[i].Inputs {
			fmt.Println(resp.Txs[i].Inputs[j].Sequence)
			fmt.Println(resp.Txs[i].Inputs[j].PrevOut.Spent)
		}
	}

}
```

## License

MIT
