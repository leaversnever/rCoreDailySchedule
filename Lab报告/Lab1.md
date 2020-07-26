# Lab1报告
## Preparation
* `context.rs` contains the definition of `Context` which store the information of registers and interrupt information when any program is interrupted.
* `timer.rs` implement a function that a timer interrupts the program every constant machine time. 

## Q1：
sp first reduces the size of a Context (34 registers), and then executes the `handle_interrupt` function, during which the value of sp may change, but after executing `handle_interrupt`, the value of sp will return to the state before the execution, from ` After handle_interrupt` returns, execute `__restore` to restore the original sp stored in the Context.
## Q2：
After `rust_main` returns, the program may be still running. Because `rust_main` is called by `entry.asm`, and no termination condition is written in `entry.asm`, the program will continue to run in some address. This situation will lead to an infinite loop (it seems that some students return an error).
My infinite loop condition
```Hello, rCore-Tutorial!
Breakpoint at 0x80200f30
100 tick
200 tick
300 tick
400 tick
500 tick
600 tick
QEMU: Terminated
```
## Q3:
### Q3.1:
We just add an arm `Trap::Exception(Exception::LoadFault) => panic!()` in the match clause of `handler::handle_interrupt(...)`
### Q3.2:
```
if stvel == 0x0
{
    println!("Success");
}
```
### Q3.3:
We just let `context.spec = 0`, so that the program will jump to `0x0`.