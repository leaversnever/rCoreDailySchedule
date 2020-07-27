# Lab3报告
## Preparation

- `address.rs`: most implementations of physical and virtual address and pages.
-  `page_table_entry.rs`: which implements PTE, which is a `struct` bind with `usize`.
-  `page_table.rs`: this file defines structure  page table, which can be made up with 512(which is PAGE_SIZE/8) PTEs. Method `zero_init()` is implemented. A smaller pointer `PageTableTracker` is also implemented.
-  `memory_set.rs` and `mapping.rs` is detailed implementation of mapping.

## Q1：
As you can see from lines 3 to 6, we can see that t0 is allocated by the address of the boot page table, and then subtracted by the linear mapping offset 0xffffffff00000000, and then shifted to the right by 12, which is a 4KB offset, Therefore t0 can represent the physical page number..
## Q2：
page_tables means all page tables, `mapped_pairs` is the table we use (maybe we can simply describe them by their name.).
## Q3:
No, we don't have to, 