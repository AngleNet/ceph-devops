Crush implementation
=====

The source code lies in src/crush, tests lies in src/test/crush. 

1. Core Datastructures
```c++
struct crush_map
struct crush_rule
struct crush_rule_step
```

2. Core methods
```c++
crush_do_rule()
crush_rule(){
    for(step = 0; step < rule->len; step++){
        int firstn = 0;
        const struct crush_rule_step *curstep = 
            &rule->steps[step];
        switch(curstep->op){
            execute the rule and write result to work_space if have some results.
        }
    }
}
```