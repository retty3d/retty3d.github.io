---
title: "標準入力の受け取り方"
date: 2023-05-05T17:36:42+09:00
bookCollapseSection: false
---

## 単一の数値

入力例
> 10

```rust
use std::io;

fn main() {
    let mut buf = String::new();
    io::stdin()
        .read_line(&mut buf)
        .expect("");

    let x: i32 = buf.trim().parse().expect("");
}
```

## 複数の数値

入力例
> 10 20

```rust
use std::io;

fn main() {
    let mut buf = String::new();
    io::stdin()
        .read_line(&mut buf)
        .expect("");

    let numbers: Vec<i32> = buf
        .trim()
        .split_whitespace()
        .map(|x| x.parse().expect(""))
        .collect();

    let a = numbers[0];
    let b = numbers[1];
}
```
