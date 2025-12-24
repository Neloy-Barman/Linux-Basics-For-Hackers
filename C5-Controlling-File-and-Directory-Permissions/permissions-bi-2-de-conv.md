# Permission Binary to Decimal Conversion

## The Connection

Each permission bit corresponds to a **binary place value**:

```
Position:     1st    2nd    3rd
              ↓      ↓      ↓
Permission:   r      w      x
Binary:       1      1      1
Place Value:  2²     2¹     2⁰
Decimal:      4      2      1
```

---

## How It Works

| Binary | Calculation | Decimal | Permission |
| :----: | ----------- | :-----: | :--------: |
| `000`  | 0 + 0 + 0   |  **0**  |   `---`    |
| `001`  | 0 + 0 + 1   |  **1**  |   `--x`    |
| `010`  | 0 + 2 + 0   |  **2**  |   `-w-`    |
| `011`  | 0 + 2 + 1   |  **3**  |   `-wx`    |
| `100`  | 4 + 0 + 0   |  **4**  |   `r--`    |
| `101`  | 4 + 0 + 1   |  **5**  |   `r-x`    |
| `110`  | 4 + 2 + 0   |  **6**  |   `rw-`    |
| `111`  | 4 + 2 + 1   |  **7**  |   `rwx`    |

---

## Visual Breakdown

```
Binary:    1     1     1
           ↓     ↓     ↓
         ┌───┐ ┌───┐ ┌───┐
         │ r │ │ w │ │ x │
         └───┘ └───┘ └───┘
           ↓     ↓     ↓
Weight:    4     2     1    →  4 + 2 + 1 = 7 (rwx)
          2²    2¹    2⁰
```

---

## Examples

> **Set `wx` (write + execute)**
> ```
> r   w   x
> 0   1   1   →  0 + 2 + 1 = 3
> ```

> **Set `r-x` (read + execute)**
> ```
> r   w   x
> 1   0   1   →  4 + 0 + 1 = 5
> ```

> **Full permission `rwxr-xr--`**
> ```
> User:   rwx = 4+2+1 = 7
> Group:  r-x = 4+0+1 = 5
> Others: r-- = 4+0+0 = 4
> 
> chmod 754 filename
> ```

---

## Key Point

> **It's simply binary-to-decimal conversion!**
> 
> The values `4, 2, 1` are just **powers of 2** representing each bit position in a 3-bit binary number.
> 
> ```
> 2² = 4  →  r
> 2¹ = 2  →  w
> 2⁰ = 1  →  x
> ```