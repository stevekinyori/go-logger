# Logger
A simple and lightweight logging package for Go.

#Features
* Support for four log levels: debug, info, warning, error.
* Ability to set a prefix for log messages.
* Option to log the name of the calling function at the debug level.
* The log messages include timestamp and the log level.
# Installation
To install the package, simply run:

``` go get github.com/yourusername/logger ```

# Usage
To start using the package, import it in your Go file:

```import "github.com/yourusername/logger" ```

# Logging messages
There are four main functions for logging messages:

* `logger.Info(message string)` - logs a message at the info level.
* `logger.Warning(message string)` - logs a message at the warning level.
* `logger.Error(message string)` - logs a message at the error level.
* `logger.Debug(message string)` - logs a message at the debug level. Only logs if the current log level is set to debug.
* `logger.DebugMethod(depth ...int)` - logs the name of the calling function at the debug level. Only logs if the current log level is set to debug. An optional depth parameter can be passed to specify how many levels to go back in the call stack to find the calling function.

# Setting log level
You can set the current log level using the following functions:

* `logger.SetLogLevelDebug()` - sets the current log level to debug.
* `logger.SetLogLevelInfo()` - sets the current log level to info.
* `logger.SetLogLevelWarning()` - sets the current log level to warning.
* `logger.SetLogLevelError()` - sets the current log level to error.

You can check the current log level using the following function:

`logger.GetLogLevel()` - returns the current log level as a string.
# Setting log prefix
You can set a prefix for log messages using the following function:
 `logger.SetLogPrefix(prefix string)` - sets the prefix for log messages. The prefix will be converted to uppercase.
 
# Example
```
package main

import "github.com/yourusername/logger"

func main() {
	logger.SetLogLevelDebug()
	logger.SetLogPrefix("example")
	logger.Info("Application started")
	logger.Warning("This is a warning message")
	logger.Error("This is an error message")
	logger.Debug("This is a debug message")
	logger.DebugMethod()
}


```

This will output:

```
[EXAMPLE] info: Application started
[EXAMPLE] warning: This is a warning message
[EXAMPLE] error: This is an error message
[EXAMPLE] debug: Calling function: main.main


```
