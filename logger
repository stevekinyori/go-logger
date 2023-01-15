package logger

import (
	"fmt"
	"log"
	"os"
	"runtime"
	"strings"
)

const (
	debugLogLevel    = "debug"
	infoLogLevel     = "info"
	logPrefixMissing = "missing"
)

var (
	logLevel  = infoLogLevel
	logPrefix = logPrefixMissing
)

func initLogger(logType string) *log.Logger {
	return log.New(os.Stdout, fmt.Sprintf("[%v] %v:", logPrefix, logType), log.LstdFlags|log.Lmicroseconds)
}

func Info(message string) {
	initLogger(infoLogLevel).Println(message)
}

func Debug(message string) {
	if logLevel == debugLogLevel {
		initLogger(debugLogLevel).Println(message)
	}
}

func DebugMethod(depth ...int) {
	if logLevel == debugLogLevel {
		var depthVal int
		if len(depth) == 0 {
			depthVal = 2
		} else {
			depthVal = depth[0]
		}
		function, _, _, _ := runtime.Caller(depthVal)
		initLogger(debugLogLevel).Printf("Calling function: %s", runtime.FuncForPC(function).Name())
	}
}

func SetLogLevelDebug() {
	logLevel = debugLogLevel
}

func SetLogLevelInfo() {
	logLevel = infoLogLevel
}

func GetLogLevel() string {
	return logLevel
}

func SetLogPrefix(prefix string) {
	logPrefix = strings.ToUpper(prefix)
}
