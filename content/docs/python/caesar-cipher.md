---
title: "シーザー暗号の実装"
date: 2023-04-25T20:10:59+09:00
draft: false
---

#### シーザー暗号

[シーザー暗号- Wikipedia](https://ja.wikipedia.org/wiki/%E3%82%B7%E3%83%BC%E3%82%B6%E3%83%BC%E6%9A%97%E5%8F%B7)

##### エンコーダー実装例

```python
def caesar_encrypt(plaintext, shift):
    ciphertext = ""
    for char in plaintext:
        if char.isalpha():
            if char.isupper():
                ciphertext += chr((ord(char) - 65 + shift) % 26 + 65)
            else:
                ciphertext += chr((ord(char) - 97 + shift) % 26 + 97)
        else:
            ciphertext += char
    return ciphertext
```

##### デコーダー実装例

```python
def caesar_decrypt(ciphertext, shift):
    plaintext = ""
    for char in ciphertext:
        if char.isalpha():
            if char.isupper():
                plaintext += chr((ord(char) - 65 - shift) % 26 + 65)
            else:
                plaintext += chr((ord(char) - 97 - shift) % 26 + 97)
        else:
            plaintext += char
    return plaintext
```

##### 解説

- isalpha()はPythonの文字列メソッドの一つで、与えられた文字列がアルファベットのみで構成されているかどうかを判定するために使用されます。
    ```python
    >>> 'A'.isalpha()
    True
    >>> '1'.isalpha()
    False
    ```

- isupper()はPythonの文字列メソッドの一つで、与えられた文字列がすべて大文字で構成されているかどうかを判定するために使用されます。
    ```python
    >>> 'A'.isupper()
    True
    >>> 'a'.isupper()
    False
    ```

- chr()はPythonの組み込み関数の一つで、Unicodeコードポイントに対応する文字を返すために使用されます。
    ```python
    >>> chr(65)
    'A'
    >>> chr(97)
    'a'
    ```

- ord()はPythonの組み込み関数の一つで、文字のUnicodeコードポイントを返すために使用されます。
    ```python
    >>> ord('A')
    65
    >>> ord('a')
    97
    ```

