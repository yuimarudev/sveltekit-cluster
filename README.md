# sveltekit-cluster
This repository is an example of clustering SvelteKit with `node:cluster`.

## Run
```bash
npm i
npm run build
node server/index.js
```

## Performance
Machine
```
Ubuntu@localhost 
--------------- 
OS: Ubuntu 20.04.5 LTS x86_64 
Host: KVM/QEMU (Standard PC (Q35 + ICH9, 2009) pc 
Kernel: 5.4.0-144-generic 
CPU: Intel (Haswell, no TSX, IBRS) (8) @ 2.399GHz 
Memory: 2599MiB / 16008MiB 
```
Node.js version
```
$ node -v
v18.15.0
```

When using `node:cluster`
```
$ ./wrk -t12 -c400 -d30s http://127.0.0.1:3000/
Running 30s test @ http://127.0.0.1:3000/
  12 threads and 400 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency    24.67ms   17.61ms 470.72ms   89.47%
    Req/Sec     1.41k   258.37     2.94k    75.99%
  503060 requests in 30.10s, 2.26GB read
Requests/sec:  16715.49
Transfer/sec:     76.77MB
```

Vanilla
```
$ ./wrk -t12 -c400 -d30s http://127.0.0.1:3000/
Running 30s test @ http://127.0.0.1:3000/
  12 threads and 400 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency    68.45ms   16.21ms 304.96ms   93.74%
    Req/Sec   491.19    145.47   666.00     34.58%
  175028 requests in 30.06s, 803.89MB read
Requests/sec:   5821.96
Transfer/sec:     26.74MB
```