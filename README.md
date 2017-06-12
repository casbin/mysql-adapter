MySQL Adapter [![Build Status](https://travis-ci.org/casbin/mysql_adapter.svg?branch=master)](https://travis-ci.org/casbin/mysql_adapter) [![Coverage Status](https://coveralls.io/repos/github/casbin/mysql_adapter/badge.svg?branch=master)](https://coveralls.io/github/casbin/mysql_adapter?branch=master) [![Godoc](https://godoc.org/github.com/casbin/mysql_adapter?status.svg)](https://godoc.org/github.com/casbin/mysql_adapter)
====

MySQL Adapter is the [MySQL DB](https://www.mysql.com/) adapter for [Casbin](https://github.com/casbin/casbin). With this library, Casbin can load policy from MySQL or save policy to it.

## Installation

    go get github.com/casbin/mysql_adapter

## Simple Example

```go
package main

import (
	"github.com/casbin/casbin"
	"github.com/casbin/mysql_adapter"
)

func main() {
	// Initialize a MySQL adapter and use it in a Casbin enforcer:
	a := mysql_adapter.NewDBAdapter("mysql", "root:@tcp(127.0.0.1:3306)/") // Your MySQL driver and data source. 
	e := casbin.NewEnforcer("examples/rbac_model.conf", a)
	
	// Load the policy from DB.
	e.LoadPolicy()
	
	// Check the permission.
	e.Enforce("alice", "data1", "read")
	
	// Modify the policy.
	// e.AddPolicy(...)
	// e.RemovePolicy(...)
	
	// Save the policy back to DB.
	e.SavePolicy()
}
```

## Getting Help

- [Casbin](https://github.com/casbin/casbin)

## License

This project is under Apache 2.0 License. See the [LICENSE](LICENSE) file for the full license text.
