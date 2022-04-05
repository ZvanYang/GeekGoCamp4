通过执行```go build -race``` 可以看到```data race``` 的情况

````
➜ zvan@zvandembp  ~/go/src/GeekGoCamp4/week3 git:(main) ✗ ./dataRace
==================
WARNING: DATA RACE
Write at 0x00000114a900 by goroutine 7:
main.Routine()
/Users/zvan/go/src/GeekGoCamp4/week3/dataRace.go:19 +0x32
main.main.func1()
/Users/zvan/go/src/GeekGoCamp4/week3/dataRace.go:11 +0x39

Previous write at 0x00000114a900 by goroutine 6:
main.Routine()
/Users/zvan/go/src/GeekGoCamp4/week3/dataRace.go:19 +0x32
main.main.func1()
/Users/zvan/go/src/GeekGoCamp4/week3/dataRace.go:11 +0x39

Goroutine 7 (running) created at:
main.main()
/Users/zvan/go/src/GeekGoCamp4/week3/dataRace.go:11 +0x85

Goroutine 6 (finished) created at:
main.main()
/Users/zvan/go/src/GeekGoCamp4/week3/dataRace.go:11 +0x85
==================
Found 1 data race(s)
````

输出结果
````
➜ zvan@zvandembp  ~/go/src/GeekGoCamp4/week3 git:(main) ✗ ./dataRace
final Counter:4
➜ zvan@zvandembp  ~/go/src/GeekGoCamp4/week3 git:(main) ✗ ./dataRace
final Counter:4
➜ zvan@zvandembp  ~/go/src/GeekGoCamp4/week3 git:(main) ✗ 
➜ zvan@zvandembp  ~/go/src/GeekGoCamp4/week3 git:(main) ✗ ./dataRace
final Counter:4
➜ zvan@zvandembp  ~/go/src/GeekGoCamp4/week3 git:(main) ✗ ./dataRace
final Counter:4
➜ zvan@zvandembp  ~/go/src/GeekGoCamp4/week3 git:(main) ✗ ./dataRace
final Counter:4
➜ zvan@zvandembp  ~/go/src/GeekGoCamp4/week3 git:(main) ✗ 
➜ zvan@zvandembp  ~/go/src/GeekGoCamp4/week3 git:(main) ✗ ./dataRace
final Counter:4
➜ zvan@zvandembp  ~/go/src/GeekGoCamp4/week3 git:(main) ✗ ./dataRace

````
基本结果是4

