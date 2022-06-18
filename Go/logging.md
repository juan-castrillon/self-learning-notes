---
title:  Logging
parent: Go
---

# Go standard  `log` package

- Sends output by default to `stderr`, but can be easily changed
- Does not support logging levels
- Includes the `log/syslog` package, which allow to write to the machine logs (normally `/var/log/system.log` or similar)

## Writing logs to a file

```go
logFile := filepath.Join(os.TempDir(), "test_go.log")
//Only write mode AND append AND create if not exists
f, err := os.OpenFile(logFile, os.O_WRONLY|os.O_APPEND|os.O_CREATE, 0644)
if err != nil {
    log.Fatal(err)
}
defer f.Close()
log.SetOutput(f)
log.SetFlags(log.LstdFlags | log.Lshortfile)
for i := 0; i < 10; i++ {
    log.Printf("Value: %d", i)
}
log.Println("finished")
```