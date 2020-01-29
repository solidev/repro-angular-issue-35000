# Repro for angular issue #35000

Added a simple console.log to lockfile guarded function

Steps to reproduce :

- npm install
- npm run build

```
Locked [Function (anonymous)]
Compiling @angular/animations : fesm5 as esm5
Compiling @angular/animations : esm2015 as esm2015
Compiling @angular/animations : esm5 as esm5
Compiling @angular/animations : main as umd
Compiling @angular/animations : fesm2015 as esm2015
Compiling @angular/compiler/testing : fesm2015 as esm2015
Compiling @angular/compiler/testing : fesm5 
```

```
 npm run build                                                                                                                                                          1.4m  Thu Jan 30 00:27:58 2020

> parallel-test@0.0.0 build /Users/jmbarbier/devel/sandbox/parallel-test
> npm-run-all --parallel build:*


> parallel-test@0.0.0 build:app1 /Users/jmbarbier/devel/sandbox/parallel-test
> ng build --prod app1


> parallel-test@0.0.0 build:app4 /Users/jmbarbier/devel/sandbox/parallel-test
> ng build --prod app4


> parallel-test@0.0.0 build:app2 /Users/jmbarbier/devel/sandbox/parallel-test
> ng build --prod app2


> parallel-test@0.0.0 build:app3 /Users/jmbarbier/devel/sandbox/parallel-test
> ng build --prod app3


> parallel-test@0.0.0 build:app5 /Users/jmbarbier/devel/sandbox/parallel-test
> ng build --prod app5

0% compilingLocked [Function (anonymous)]
Locked [Function (anonymous)]
0% compilingLocked [Function (anonymous)]
40% building 15/16 modules 1 active ...-
```

shows that something uses a lockfile event with ngcc precompilation => parallel build failure
