# Rust Tutorial Project — Principles of Programming Languages

> **Topic No.:** 06
> **Topic Name:** Conditional Structure
> **Group No.:** 06

---

## 1. Members

| # | Name | Student ID | GitHub Username | Main Responsibility |
|---|---|---|---|---|
| 1 | `นางสาวธนัญญา พรมภักดี` | `670710128` | `@670710128` | Concept + Code |
| 2 | `นายธีทัต สุจริตพาณิช` | `670710130` | `@670710130` | Code + Demo |
| 3 | `นายนทิบดี ช้างทอง` | `670710131` | `@670710131` | Rust vs Other Language + PPL |
| 4 | `นายนนธวัช งามบุญศิริสิงห์` | `670710132` | `@670710132` | Exercises + Common Mistakes |

---

## 2. Learning Objectives

หลังจากศึกษา Topic นี้แล้ว ผู้เรียนสามารถ:

1. `[อธิบายแนวคิดสำคัญได้]`
2. `[เขียนโปรแกรม Rust ที่เกี่ยวข้องได้]`
3. `[วิเคราะห์พฤติกรรม/กฎของภาษาได้]`
4. `[เปรียบเทียบ Rust กับภาษาอื่นได้]`

---

## 3. Introduction

อธิบายว่า Topic นี้คืออะไร มีความสำคัญอย่างไร และใช้แก้ปัญหาอะไรในการเขียนโปรแกรม

`Conditional Structure หรือ คำสั่งเงื่อนไข คือคำสั่งที่ใช้สำหรับการตัดสินใจ โดยการตัดสินใจนั้นจะขึ้นอยู่กับเงื่อนไขที่กำหนดไว้ ทำให้โปรแกรมสามารถตอบสนองต่อ ข้อมูลและสถานการณ์ที่แตกต่างกันได้ ถ้าไม่มี Conditional Structure โปรแกรมจะทำงานตามลำดับคำสั่งที่เขียนไว้เท่านั้น ไม่สามารถเลือกได้ว่า “ถ้าเกิดเหตุการณ์ A ให้ทำแบบนี้ แต่ถ้าเกิดเหตุการณ์ B ให้ทำอีกแบบ”สิ่งหนึ่งที่แตกต่างจากภาษาโปรแกรมหลายภาษา คือ เงื่อนไขเป็นแบบ Boolean ใน Rust ไม่จำเป็นต้องใส่วงเล็บ () ครอบไว้ แต่สามารถใส่วงเล็บได้ และแต่ละเงื่อนไขจะตามด้วย block { } ซึ่งเป็นส่วนของคำสั่งที่จะถูกทำงานเมื่อเงื่อนไขนั้นเป็นจริง สามารถควบคุม flow ของโปรแกรมโดยใช้ร่วมกับ relational comparison operators และ logical operators ได้ ใน Rust Conditional Structure หลัก ๆ ประกอบด้วย if, else if, else, match `

---

## 4. Key Concepts

### 4.1 `Conditional Statements`

**คำอธิบาย**

`คำสั่งเงื่อนไขที่ใช้สำหรับให้โปรแกรมตัดสินใจ โดยพิจารณาจากเงื่อนไขที่กำหนด เงื่อนไขที่โปรแกรมตรวจสอบต้องให้ผลลัพธ์เป็น Boolean คือ true หรือ false ถ้าผลลัพธ์เป็น true จะทำคำสั่งใน block แต่ถ้า false จะไม่ทำ หรือไปตรวจสอบเงื่อนไขถัดไป`

**ตัวอย่าง**

```rust
fn main() {
    let score = 85;

    if score >= 90 {
        println!("Grade A");
    } else if score >= 80 {
        println!("Grade B");
    } else {
        println!("Grade C or below");
    }
}
```
**Explanation**

` สร้างตัวแปรชื่อ score และกำหนดค่าเป็น 85 ตรวจสอบเงื่อนไขแรก 85 >= 90 เป็น true/false ผลลัพธ์เป็น false ดังนั้นไม่ทำคำสั่ง ตรวจสอบ else if ต่อ score >= 80 เป็น true/false ผลลัพธ์เป็น true ดังนั้นทำคำสั่ง println!("Grade B"); ส่วน else จะทำงานก็ต่อเมื่อ เงื่อนไขก่อนหน้าทั้งหมดเป็น false`

---

### 4.2 `if statement`

`เป็นเงื่อนไขพื้นฐานตัวแรกที่ใช้สำหรับตรวจสอบเงื่อนไข ทำงานเฉพาะเมื่อเงื่อนไขเป็นจริง (true)`

```rust
fn main() {
    let age = 20;

    if age >= 18 {
        println!("Adult");
    }
}
```
**Explanation**

` สร้างตัวแปรชื่อ age และกำหนดค่าเป็น 20 ตรวจสอบเงื่อนไข age >= 18 เป็น true/false ผลลัพธ์เป็น true ดังนั้นทำคำสั่ง println!("Adult"); ถ้าเป็น false โปรแกรมจะไม่ทำคำสั่งภายในบล็อก if และจะทำงานต่อจากบล็อก if`

---

### 4.3 `else..if statement`

`ใช้สำหรับตรวจสอบเงื่อนไขอื่นเพิ่มเติมหลังจากเงื่อนไข if ก่อนหน้าไม่เป็นจริงและก่อนที่จะไปถึง else โปรแกรมหนึ่งสามารถมี else if ได้หลายตัวใน Conditional Statement ชุดเดียวกัน `

```rust
fn main() {

    if false {
        println!("Primary if statement");
    } else if false {
        println!("Secondary if statement");
    } else if true {
        println!("Tertiary if statement");
    }

}
```
**Explanation**

`โปรแกรมตรวจสอบเงื่อนไขแรกเป็น false ไม่ทำคำสั่งในบล็อก ตรวจสอบเงื่อนไขต่อไปเป็น false ไม่ทำคำสั่งในบล็อก ตรวจสอบเงื่อนไขต่อไปเป็น true ดังนั้นจึงทำคำสั่ง println!("Tertiary if statement")`

---

### 4.4 `else  statement`

`จะทำงานเมื่อเงื่อนไขของ if หรือเงื่อนไขก่อนหน้าไม่เป็นจริง (true ทำอันแรก / false ทำอันที่สอง)  `

```rust
fn main() {
    let age = 16;

    if age >= 18 {
        println!("You can vote.");
    } else {
        println!("You are too young to vote.");
    }
}
```
**Explanation**

` สร้างตัวแปรชื่อ age และกำหนดค่าเป็น 16 ตรวจสอบเงื่อนไข age >= 18 เป็น true/false ผลลัพธ์เป็น true ดังนั้นทำคำสั่ง println!("You can vote."); ถ้าเป็น false โปรแกรมจะคำสั่งใน else แทน`

---

### 4.5 `Logical Operators`

`เราสามารถตรวจสอบหลายเงื่อนไขภายใน if ได้ โดยใช้ logical operators 2 ตัว คือ && และ ||`

&& หรือ Conditional AND ใช้ตรวจสอบว่าเงื่อนไขหนึ่งและอีกเงื่อนไขหนึ่งเป็นจริงหรือไม่ ทั้งสองเงื่อนไขต้องเป็น true
```rust
fn main() {
    let a = 5;

    if a > 0 && a < 10 {
        println!("Both conditions are true");
    }
}
```

|| หรือ Conditional OR ใช้ตรวจสอบว่าเงื่อนไขหนึ่งหรืออีกเงื่อนไขหนึ่งเป็นจริงหรือไม่ ไม่จำเป็นต้องเป็นจริงทั้งสองเงื่อนไข
```rust
fn main() {
    let a = 5;

    if a > 0 || a < 10 {
        println!("One of the conditions are true");
    }
}
```
---

### 4.6 `Nested Conditional`

`คือการนำคำสั่ง if ไปใส่ไว้ภายในบล็อก if หรือ else อื่นอีกทีหนึ่ง มักใช้เมื่อเราต้องการตรวจสอบเงื่อนไขรองหลังจากที่เงื่อนไขแรกเป็นจริงแล้ว Compiler จะประเมินเงื่อนไขแบบเป็นลำดับชั้น เริ่มจาก if ด้านนอกก่อน แล้วจึงเข้าไปตรวจสอบ if ด้านใน`

```rust
fn main() {
    let number = 5;

    if number < 10 {

        if number > 0 {
            println!("Inner if statement");
        }

    }
}
```
**Explanation**

` สร้างตัวแปรชื่อ number และกำหนดค่าเป็น 5 ตรวจสอบเงื่อนไข number < 10 เป็น true/false ผลลัพธ์เป็น true ดังนั้นโปรแกรมจึงเข้าไปทำคำสั่งภายใน if เจอ if อีกตัวหนึ่งด้านในนี่คือ Nested if ตรวจสอบเงื่อนไข number > 0 ผลลัพธ์เป็น true ดังนั้นจึงทำ println!("Inner if statement");`

---

### 4.7 `match`

`match ใช้สำหรับตรวจสอบค่าหนึ่งค่ากับรายการของค่าที่เป็นไปได้หลายค่า ใช้เมื่อเราต้องการตรวจสอบหลายกรณี ถ้าคุ้นเคยกับภาษาในตระกูล C สามารถมองว่า match มีแนวคิดคล้ายกับ switch statement แต่ syntax แตกต่างกัน`

```rust
fn main() {
    let grade = "X";

    match grade {
        "A" => println!("Excellent"),
        "B" => println!("Good"),
        "C" => println!("Okay"),
        _ => println!("Unknown grade"),
    }
}
```
**Explanation**

` สร้างตัวแปรชื่อ grade กำหนดค่าเป็น "X" ใช้ keyword match ตามด้วยค่าหลักที่เราต้องการตรวจสอบนำค่าของ grade ไป เปรียบเทียบกับรูปแบบ (pattern) ที่กำหนดไว้ทีละตัว ตรวจสอบว่าตรงกับค่าไหนถ้าตรงจะทำงานตามที่กำหนด ถ้าไม่ตรงเลยจะทำ หมายถึง ค่าหรือกรณีอื่น ๆ ที่ไม่ตรงกับ pattern ก่อนหน้า ดังนั้นผลลัพธ์คือ Unknown grade`

---

### 4.8 `Expression`

`Rust สามารถเอาผลลัพธ์จาก if...else ไปเก็บในตัวแปรได้ ไม่ได้ใช้แค่ควบคุมการทำงาน`

```rust
fn main() {
    let time = 20;

    let greeting = if time < 18 {
        "Good day."
    } else {
        "Good evening."
    };

    println!("{}", greeting);
}
```
**Explanation**

` สร้างตัวแปรชื่อ time กำหนดค่าเป็น 20 และสร้างตัวแปรชื่อ greeting เพื่อให้ if-else สามารถนำผลลัพธ์ที่ได้ไปเก็บในตัวแปร greeting โปรแกรมตรวจสอบ time < 18 ได้ผลลัพธ์เป็น false ดังนั้นจะเลือกค่าจาก else นำค่านี้ไปเก็บที่ greeting จะได้ว่า greeting = "Good evening." แล้วนำค่าของ greeting มาแสดงผล`

---

## 5. Important Syntax / Rules

| Syntax / Rule | Meaning | Example |
|---|---|---|
| `if condition {statement}` | `ทำคำสั่งใน statement ในวงเล็บปีกกา {...} ถ้าเงื่อนไข (condition) เป็นจริง` | `if x > 0 {println("Positive");}` |
| `if condition1 {statement1}      else if condition2{statement2}  else {statement3}` | `ถ้า condition1 เป็นจริง ทำ statement1 , ถ้า condition1 เป็นเท็จ และ condition2 เป็นจริง ทำ statement2 , ถ้าทั้งสองเงื่อนไขเป็นเท็จ ทำ statement3 ในส่วน else` | `if x > 0 {println!("Positive");}         else if x < 0 {println!("Negative");}      else {println!("Zero");}                                                            ` |
| `if condition1 {if condition2 {statement}}` | `หาก condition1 ของ if ด้านนอกเป็นจริง จะทำ condition2 ของ if ด้านใน และหาก condition2 เป็นจริงโปรแกรมจะทำงานในส่วนของ statement` | `if x != 0 {if x > 0 {println!("Positive");}}่` |

### Important Rules

1. `เงื่อนไข(condition)ของ if ต้องเป็น Boolean เท่านั้น เพราะ Rust จะไม่แปลงค่าให้อัตโนมัติเหมือนบางภาษา`
2. `ต้องมีเครื่องหมายปีกกา '{...}' ครอบการทำงานของ statement เสมอ`
3. `ไม่จำเป็นต้องใส่เครื่องหมายวงเล็บ '(...)' ครอบส่วนของเงื่อนไข(condition) (complier จะเตือน unnecessary parentheses)`

---

## 6. Runnable Code Examples

> **ข้อกำหนด:** Code ทุกตัวต้อง Compile และ Run ได้จริงก่อนนำมาใส่ในเอกสาร

### Example 1 — `[SimpleGrade]`

**Purpose:** `[แสดงการใช้เงื่อนไข if, else if, else อย่างง่ายที่รวมเข้าด้วยกันเป็น code เดียว]`

```rust
fn main() {
    let score:i32 = 90;
    
    if score >= 80{
        println!("Grade A");
    }
    else if score >= 60{
        println!("Grade B");
    }
    else if score >= 40{
        println!("Grade C");
    }
    else{
        println!("Grade F");
    }
}
```

**Expected Output**

```text
[Grade A]
```

**Explanation**

`- กำหนดคะแนนที่ใช้ในการตรวจเงื่อนไขให้มีค่า 90`

`- เมื่อเข้าเงื่อนไข if score >= 80 หากคะแนน มากกว่าหรือเท่ากับ 80 จะพิมพ์ "Grade A" ออกมา `

`- หากเงื่อนไขแรกเป็นเท็จ จะตรวจเงื่อนไขที่สอง  else if score >= 60 หากคะแนนมีค่า มากกว่าหรือเท่ากับ 60 จะพิมพ์ "Grade B" ออกมา `

`- หากเงื่อนไขที่สองยังคงเป็นเท็จ จะตรวจเงื่อนไขที่สาม  else if score >= 40 หากคะแนนมีค่า มากกว่าหรือเท่ากับ 40 จะพิมพ์ "Grade C" ออกมา`

`- สุดท้ายหากไม่เข้าเงื่อนไขก่อนหน้าอันใดเลย จะทำสิ่งที่อยู่ใน else เป็นการพิมพ์ "Grade F" ออกมา`

`- ในตัวอย่างนี้ score = 90 ซึ่งจะทำเงื่อนไข if เป็นจริง และพิมพ์ "Grade A" ออกมา`




# Example 2 — `[NestedGrade]`

**Purpose:** `[แสดงการใช้ Nested-if ที่เป็นการใช้ if ซ้อนใน if อีกชั้นหนึ่ง ซึ่งเป็นวิธีการทำเงื่อนไขซ้อนเงื่อนไข]`

```rust
fn main() {
    let score:i32 = 39;

    if score >= 60 {
        if score >= 80 {
            println!("Grade A");
        } 
        else {
            println!("Grade B");
        }
    } 
    else {
        if score >= 40 {
            println!("Grade C");
        } 
        else {
            println!("Grade F");
        }
    }
}
```

**Expected Output**

```text
[Grade F]
```

**Explanation**

`- กำหนดคะแนนที่ใช้ในการตรวจให้มีค่า 39`

`- เมื่อเข้าเงื่อนไข if score >= 60 หากคะแนน มากกว่าหรือเท่ากับ 60 จะตรวจสอบ  if score >= 80 เป็นตัวถัดไป หากคะแนน มากกว่าหรือเท่ากับ 80 เป็นจริงจะพิมพ์ "Grade A" ออกมา แต่หากเป็นเท็จจะเข้าไปทำในส่วนของ else คือ พิมพ์ "Grade B" ออกมา
`

`- ในส่วนของ else ด้านนอกจะทำงานเมื่อคะแนนน้อยกว่า 60 (ไม่เข้าเงื่อนไข if) โดยด้านในจะตรวจสอบ if score >= 40 หากคะแนน มากกว่าหรือเท่ากับ 40 เป็นจริงจะพิมพ์ "Grade C" ออกมา แต่หากเป็นเท็จจะเข้าไปทำในส่วนของ else คือ พิมพ์ "Grade F" ออกมา
`

`- ในตัวอย่างนี้ score = 39 ซึ่งจะทำงานจาก else ด้านนอกสุด และตรวจสอบด้านในเริ่มจาก if score >= 40 เป็นเท็จ ทำให้ขั้นตอนสุดท้ายต้องทำงานในส่วนของ else ด้านใน ซึ่งผลลัพธ์ที่ได้ คือการพิมพ์ "Grade F" อกกมา 
`


## 7. Common Mistakes

### Mistake 1 — การใช้ตัวเลขหรือ Type อื่นที่ไม่ใช่ Boolean ในเงื่อนไข if

**Problem**
คนที่มาจากภาษา C, C++ หรือ Python จะชินกับการใช้ตัวเลข (เช่น `0` หรือ `1`) หรือ Pointer มาเป็นเงื่อนไขหลัง `if` โดยตรง

**Incorrect Code**
```rust
fn main() {
    let number = 1;
    // Compile Error! เพราะ number เป็นประเภท i32 ไม่ใช่ bool
    if number {
        println!("Number is not zero");
    }
}
```
**Correct Code**
```rust
fn main() {
    let number = 1;
    if number != 0 { // ต้องเช็คให้ได้ค่า bool (true/false) ชัดเจน
        println!("Number is not zero");
    }
}
```
**Why?**

Rust เข้มเรื่อง Type มาก เงื่อนไขหลัง if ต้องได้ค่าออกมาเป็น bool (true หรือ false) เท่านั้น มันจะไม่แปลงตัวเลขเป็น Boolean ให้อัตโนมัติเหมือนภาษา C เพื่อป้องกันบั๊กที่เราอาจจะเผลอเขียนผิด

---

### Mistake 2 — การคืนค่าคนละ Type ออกมาจาก if Expression

**Problem**

`ใน Rust เอา if ไปกำหนดค่าให้ตัวแปรได้ แต่ดันคืนค่าปนกันคนละประเภทในแต่ละปีกกา`

**Incorrect Code**

```rust
fn main() {
    let condition = true;
    let result = if condition {
        5       // เป็นตัวเลข
    } else {
        "five"  // Compile Error เป็นข้อความ
    };
}
```

**Correct Code**

```rust
fn main() {
    let condition = true;
    let result = if condition {
        5 // เป็นตัวเลขทั้งคู่
    } else {
        6
    };
}
```

**Why?**

`Rust ต้องรู้ Data Type ของตัวแปรตั้งแต่งานยังไม่รันโปรแกรม ไม่ว่าจะเข้าเงื่อนไข if หรือ else ค่าที่ส่งออกมาต้องเป็น Type เดียวกันเสมอ`

---
### Mistake 3 — การลืมใส่ else เวลาเอา if ไปกำหนดค่าตัวแปร

**Problem**

`ใช้ if กำหนดค่าให้ตัวแปร แต่ดันเขียนแค่ if ไม่มี else`

**Incorrect Code**

```rust
fn main() {
    let is_active = true;
    // Compile Error ขาดบล็อก else
    let status_code = if is_active { 200 };
}
```

**Correct Code**

```rust
fn main() {
    let is_active = true;
    let status_code = if is_active { 200 } else { 400 };
}
```

**Why?**

`Rust มีกฎเหล็กว่าตัวแปรห้ามว่างเปล่า (Uninitialized) ถ้าไม่มี else แล้วเงื่อนไขเป็น false ตัวแปรจะไม่มีค่าใส่ ซึ่ง Rust ไม่ยินยอม`

---

## 8. Exercises

### Exercise 1 — ระบบคำนวณส่วนลดตามระดับสมาชิกและยอดซื้อ

**Problem**
จงเขียนโปรแกรมคำนวณราคาสุทธิหลังหักส่วนลดร้านค้า โดยรับค่าตัวแปร 2 ตัวคือ `is_vip: bool` และ `total_amount: f64` โดยมีเงื่อนไขการให้ส่วนลดดังนี้:
- ถ้าเป็นสมาชิก VIP (`is_vip = true`):
  - ยอดซื้อตั้งแต่ 1,000 บาทขึ้นไป ได้ส่วนลด 20%
  - ยอดซื้อน้อยกว่า 1,000 บาท ได้ส่วนลด 10%
- ถ้าไม่ได้เป็นสมาชิก VIP (`is_vip = false`):
  - ยอดซื้อตั้งแต่ 1,000 บาทขึ้นไป ได้ส่วนลด 5%
  - ยอดซื้อน้อยกว่า 1,000 บาท ไม่ได้ส่วนลด (0%)

ให้ใช้ `if - else` ในการคำนวณหาเปอร์เซ็นต์ส่วนลด นำไปหักออกจากยอดซื้อ แล้วพิมพ์ราคาสุทธิออกมาทางหน้าจอ

**Hint**
- ใช้ `if` ซ้อนภายใน `if` (Nested Condition) หรือใช้ Logical Operator `&&` ร่วมด้วย
- คำนวณส่วนลดโดย `total_amount * (1.0 - discount_rate)`

**Solution**
```rust
fn main() {
    let is_vip: bool = true;
    let total_amount: f64 = 1250.0;

    let discount_rate = if is_vip {
        if total_amount >= 1000.0 {
            0.20 // VIP ยอด 1000+ ลด 20%
        } else {
            0.10 // VIP ยอดไม่ถึง 1000 ลด 10%
        }
    } else {
        if total_amount >= 1000.0 {
            0.05 // ไม่ใช่ VIP ยอด 1000+ ลด 5%
        } else {
            0.00 // ไม่ใช่ VIP ไม่ได้ส่วนลด
        }
    };

    let final_price = total_amount * (1.0 - discount_rate);
    println!("Total Amount: {:.2} THB", total_amount);
    println!("Discount Rate: {}%", discount_rate * 100.0);
    println!("Final Price: {:.2} THB", final_price);
}
```
**Explanation**

`ใช้ if เป็น Expression หาค่าอัตราส่วนลดก่อน เริ่มตรวจเช็คจาก is_vip เมื่อเป็น true จะเข้ามาเช็คเงื่อนไขซ้อนด้านในต่อว่า total_amount >= 1000.0 หรือไม่ ซึ่ง 1250.0 >= 1000.0 เป็นจริง บล็อก if ด้านในจึงคืนค่า 0.20 ออกมาเก็บไว้ในตัวแปร discount_rate แล้วนำไปคำนวณราคาสุทธิออกมาได้ 1000.00 THB`

---

### Exercise 2 — การแกะค่า Option ด้วย if let 

**Problem**

ในภาษา Rust เมื่อทำงานกับข้อมูลที่มีโอกาสเป็นค่าว่างได้ จะใช้ Enum ประเภท `Option<T>` (ซึ่งมีค่าเป็น `Some(T)` หรือ `None`)
จงเขียนโปรแกรมรับค่าคะแนนสอบ `score: Option<i32>` แล้วใช้โครงสร้างเงื่อนไข `if let` ในการตรวจสอบว่า:
1. ถ้ามีค่าคะแนนอยู่จริง (`Some(s)`) ให้ตรวจเช็คต่อว่าคะแนน `s >= 50` หรือไม่ ถ้าถึงให้พิมพ์ `"Passed with score: X"` แต่ถ้าไม่ถึงให้พิมพ์ `"Failed with score: X"`
2. ถ้าไม่มีค่าคะแนน `(None)` ให้พิมพ์ `"No score provided"`

**Hint**

- โครงสร้าง `if let Some(s) = score { ... } else { ... }` เป็นการเช็คเงื่อนไขพร้อมแกะค่า (Pattern Matching) ในคำสั่งเดียว

**Solution**

```rust
fn main() {
    let score: Option<i32> = Some(68); 

    if let Some(s) = score {
        if s >= 50 {
            println!("Passed with score: {}", s);
        } else {
            println!("Failed with score: {}", s);
        }
    } else {
        println!("No score provided");
    }
}
```

**Explanation**

`คำสั่ง if let Some(s) = score จะทำการตรวจสอบว่าตัวแปร score มีข้อมูลประเภท Some หรือไม่ ถ้ามี มันจะแกะค่าตัวเลขข้างในออกมาใส่ไว้ในตัวแปร local ชื่อ s ทันที และทำบล็อกเงื่อนไขภายใน (พิมพ์ "Passed with score: 68") แต่ถ้า score เป็น None มันจะข้ามไปทำบล็อก else ด้านนอกสุดแทน `

---

## 9. PPL Perspective

> **ส่วนนี้เป็นหัวใจของรายวิชา Principles of Programming Languages**

วิเคราะห์ Topic นี้ในมุมมองของ Programming Languages

### 9.1 Syntax

`Rust นั้นเป็นภาษาที่ Conditional structures มี syntax ที่ไม่เหมือนภาษาอื่นตรงที่ condition ของข้อนั้นๆ จะไม่จำเป็นต้องใส่วงเล็บแต่ก็ยังคงต้องใส่ {} เพื่อเป็นการทำ block ทุก statement และยังสามรถนำ if ไปใช้เป็น expression ได้โดยตรงและคืนค่าออกมาได้เลย เหมือนเป็นตัวแปรตัวหนึ่งทำให้เราเอาไป assign ใส่ตัวแปรได้เลย และ nested if เขียนซ้อนกันได้โดยวาง if ไว้ใน block ของ if อีกตัว หรือใช้ else if ต่อกันได้`

### 9.2 Semantics

`if/else ตรวจเงื่อนไขเพื่อเลือกรันเพียง branch เดียว branch ที่ไม่ถูกเลือกจะไม่ถูก evaluate และ &&, || เป็น short-circuit เมื่อใช้เป็น expression ค่าที่ได้คือค่าของ branch ที่ถูกเลือก ถ้าไม่มี else จะมี type เป็น () จึงใช้คืนค่าอื่นไม่ได้ ดังนั้น if ที่ต้องคืนค่าจริงต้องมี else เสมอ`

### 9.3 Type System

`condition ของ if ธรรมดาต้องเป็น boolean เท่านั้น เพราะ Rust ไม่มี implicit conversion ส่วนของ if let ใช้ pattern matching แทน แต่ยังตรวจที่ compile time เช่นกัน เมื่อใช้ if เป็น expression ทุก branch ต้องมี type เดียวกัน เพราะ Rust เป็น 
static type และ compiler ต้องหา type ของ expression ให้ได้ตอน compile time`

### 9.4 Memory / Resource Management

`เพราะเนื่องจากตัวแปรที่ประกาศภายใน {} ของแต่ละ if นั้นจะถูกจำกัดแค่ใน block นั้น และจะถูก deallocate จาก memory หลังออกจาก if ทันทีทำให้ไม่ต้องพึ่ง garbage collector ทำให้ไม่มี overhead จาก runtime memory management`

### 9.5 Abstraction / Other PPL Concepts

`เพราะ if ของ Rust สามารถเป็น expression สะท้อนแนวคิดจากภาษาสาย functional ที่ทุกโครงสร้างคุม flow คืนค่าได้ ต่างจาก imperative ดั้งเดิมเช่น C/Java 
 ตัวแปรที่ประกาศใน if/else block จึงมี scope จำกัดแค่ใน block
 Rust ผสม imperative paradigm เข้ากับ functional paradigm หรือเรียกว่าภาษาแบบ multi-paradigm`
 
### 9.6 Why Rust?

`เพราะ condition structure ใน Rust ทำให้เกิด Type safety เพราะทุก if ที่เป็น expression นั้นต้องมี return type เหมือนกันเสมอทำให้ compiler จับ type error ได้ตั้งแต่ compile time 
การทำ condition เป็น boolean ก็ทำให้การ check condition เช่น การเผลอ assign แทน compare (if (x = 5)) ทำให้ condition ที่ต้องเป็น boolean นั้นตรวจจับได้และทำให้เกิด Reliability
การตรวจสอบทั้งหมดเกิดขึ้น ที่ compile time เท่านั้น ไม่มีการเช็คเพิ่มตอน runtime และยังไม่ต้องมี garbage collector คอยตรวจสอบหรือ clean up memory ระหว่างรันโปรแกรม เพราะตัวแปรใน branch ต่างๆ ถูก drop ตาม scope โดยอัตโนมัติ`

---

## 10. Rust vs. Other Language

**Comparison Language:** `Python`

| Aspect | Rust | Other Language |
|---|---|---|
| Syntax | `ไม่ต้องใส่วงเล็บครอบเงื่อนไข แต่บังคับใส่ {} เสมอเพื่อทำ block` | `ไม่ต้องใส่วงเล็บและไม่มี {} เลย ใช้ indentation การเว้นวรรค หรืิ tab แทนการกำหนด block พร้อมโคลอน :` |
| Semantics / Behavior | `Condition ต้องเป็น bool เท่านั้น` | `Condition รับได้แทบทุก type` |
| Type System | `Static strong typing, ตรวจตอน compile time ถ้าใช้ if เป็น expression ทุก branch บังคับ return type เดียวกัน` | `Dynamic typing ตรวจตอน runtime ตัวแปรเปลี่ยน type ได้ตลอด และ conditional expression ไม่บังคับให้สอง branch คืน type เดียวกันเลย` |
| Memory Management | `ตัวแปรใน block ถูก drop อัตโนมัติทันทีที่ออกจาก scope ไม่มี garbage collector` | `ใช้ garbage collector คอยเก็บ memory ที่ไม่ใช้แล้วให้อัตโนมัติ` |
| Safety | `Compiler เช็ค type และ bool ตั้งแต่ compile time ป้องกัน bug ก่อนรันจริง` | `ไม่มีการเช็ค type ตอน compile เพราะไม่มีขั้นตอน compile แบบ static ทำให้เกิด bug บาง class จะไปโผล่ตอน runtime แทน` |

### Rust Example

```rust
fn main() {
    let number = 3;
    if number % 2 == 0 {
        println!("{} is Even", number);
    } else {
        println!("{} is Odd", number);
    }
}
```

### `Python` Example

```python
number = 3
    if number % 2 == 0:
        print(f"{number} is Even")
    else:
        print(f"{number} is Odd")
```

### Analysis

`Rust ต้องมี fn main() ครอบ ใช้ {} กำหนดขอบเขต block, และบรรทัดคำสั่งต้องปิดด้วย ;
Python ไม่ต้องมี function ครอบ, ใช้ indentation แทน {} ในการกำหนดขอบเขต if else, ไม่ต้องมี ; ปิดบรรทัด
ในแง่ type system ตัวแปร number ทั้งสองภาษาไม่ได้ระบุ type ชัดเจน แต่ต่างกันตรงที่ Rust เป็น int32 ตอน compile ในขณะที่ Python ตัวแปรเป็น int แบบ dynamic คือเปลี่ยน type ได้ตลอดเวลาแม้ตอนรันโปรแกรม`

---

## 11. Teach Your Topic

การนำเสนอมีสมาชิก 4 คน คนละประมาณ 5 นาที

| Member | Responsibility | Time |
|---|---|---|
| Member 1 | Concept + Short Code Illustration | 5 min |
| Member 2 | Detailed Code + Live Demo | 5 min |
| Member 3 | Rust vs Other Language + PPL Analysis | 5 min |
| Member 4 | Exercises + Common Mistakes + Challenge | 5 min |

### Individual Contribution

**Member 1:** นางสาวธนัญญา พรมภักดี (670710128)
* **รับผิดชอบ:** Concept + Short Code Illustration
* **รายละเอียด:** อธิบายทฤษฎีพื้นฐาน Conditional Structures ใน Rust พร้อมยกตัวอย่างโค้ดประกอบ
>
> ---
>
**Member 2:** นายธีทัต สุจริตพาณิช (670710130)
* **รับผิดชอบ:** Detailed Code + Live Demo
* **รายละเอียด:** ลงลึกรายละเอียดโค้ดตัวอย่าง และทำ Live Demo รันโปรแกรมระหว่างนำเสนอ
>
> ---
>
**Member 3:** นายทิบดี ช้างทอง (670710131)
* **รับผิดชอบ:** Rust vs Other Language + PPL Analysis
* **รายละเอียด:** เปรียบเทียบ Rust กับภาษาอื่นตามหลัก PPL
>
> ---
>
**Member 4:** นายนนธวัช งามบุญศิริสิงห์ (670710132)
* **รับผิดชอบ:** Exercises + Common Mistakes + Challenge
* **รายละเอียด:** ออกแบบแบบฝึกหัด รวบรวมข้อผิดพลาดที่พบบ่อย และโจทย์ท้าทาย
> **Note:** สมาชิกทุกคนเข้าใจโครงสร้างและสามารถอธิบาย Code ทั้งหมดของกลุ่มได้เป็นอย่างดี
---

## 12. References

1. Klabnik, S., & Nichols, C. (2023). *Control Flow - The Rust Programming Language*. Rust Documentation. https://doc.rust-lang.org/book/ch03-05-control-flow.html
2. Rust Community. (n.d.). *If/else - Rust by Example*. Rust Documentation. https://doc.rust-lang.org/rust-by-example/flow_control/if_else.html
3. Rust Community. (n.d.). *if let - Rust by Example*. Rust Documentation. https://doc.rust-lang.org/rust-by-example/flow_control/if_let.html
4.  Rust Reference Team. (n.d.). *If expressions - The Rust Reference*. Rust Documentation. https://doc.rust-lang.org/reference/expressions/if-expr.html
5. Rust Community. (n.d.). *Rust by Example*. Rust Documentation. https://doc.rust-lang.org/rust-by-example/
6. GeeksforGeeks. (n.d.). *Conditionals in Rust*. https://www.geeksforgeeks.org/rust/conditionals-in-rust/
7. W3Schools. (n.d.). *Rust if .. else Conditions*. https://www.w3schools.com/rust/rust_if_else.php
   
---

## 13. AI Usage Declaration

สามารถใช้ AI เป็นเครื่องมือช่วยเรียนรู้และพัฒนาได้ แต่สมาชิกทุกคนต้องเข้าใจและสามารถอธิบายผลงานของกลุ่มได้

| AI Tool | Purpose | How the Result Was Verified |
| :--- | :--- | :--- |
| **ChatGPT** | • ใช้ช่วยเรียบเรียงภาษาและตรวจทานคำผิดในเอกสาร <br> • ใช้ช่วยค้นหาไอเดียโจทย์แบบฝึกหัดเบื้องต้น | • สมาชิกในกลุ่มอ่านเรียบเรียงเนื้อหาใหม่ด้วยตนเอง <br> • นำโจทย์มาปรับแก้และทดสอบสั่งรันโค้ดจริงด้วย `cargo run` |
| **Gemini** | • ใช้ตรวจสอบโครงสร้างของโปรแกรม <br> | • อ่านทบทวนเนื้อหาภาษาไทยให้ถูกต้องตามคำศัพท์ทางคอมพิวเตอร์ |

### Declaration

- [✓] Code ทุกส่วนที่นำเสนอได้รับการ Compile และทดสอบแล้ว
- [✓] สมาชิกทุกคนสามารถอธิบาย Code ที่นำเสนอได้
- [✓] ตรวจสอบข้อมูลจากแหล่งอ้างอิงที่น่าเชื่อถือแล้ว
- [✓] ระบุการใช้ AI อย่างโปร่งใส

### รายละเอียดการใช้ AI

ใช้ AI เป็นเพียง **"เครื่องมือช่วยค้นหาข้อมูลและตรวจทานเอกสาร"** เพื่อความรวดเร็วในการสืบค้นวิธีแก้ปัญหาการตั้งค่าสภาพแวดล้อมการทำงาน และช่วยเกลาภาษาในเอกสารเท่านั้น 
การวิเคราะห์เนื้อหา การเขียนโค้ดตัวอย่าง การออกแบบแบบฝึกหัด ตลอดจนการทดสอบรันโปรแกรมทั้งหมด สมาชิกทุกคนในกลุ่มเป็นผู้ลงมือทำ เขียนโค้ด และตรวจสอบความถูกต้องกับเอกสารอ้างอิงทางการของ Rust (`doc.rust-lang.org`) ด้วยตนเอง

---

## 14. GitHub Contribution

| Member | Issues | Commits | Pull Requests | Code Reviews | Contribution |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Member 1** <br> (นางสาวธนัญญา พรมภักดี) | 0 | 4 | 3 | 1 | สรุปและเขียนเนื้อหาบทเรียนส่วน Concept + Short Code บน Markdown |
| **Member 2** <br> (นายธีทัต สุจริตพาณิช) | 0 | 3 | 1 | 0 | เรียบเรียงเนื้อหา Detailed Code และอัปโหลดไฟล์โค้ดสำหรับ Live Demo |
| **Member 3** <br> (นายทิบดี ช้างทอง) | 0 | 3 | 0 | 0 | สรุปส่วน Rust vs Other Languages และเขียนวิเคราะห์เชิง PPL |
| **Member 4** <br> (นายนนธวัช งามบุญศิริสิงห์) | 0 | 52 | 0 | 0 | จัดทำโครงสร้าง Repository, เขียนแบบฝึกหัด (Exercises) และทดสอบโค้ด |

---

### Teamwork Reflection

#### How did your team collaborate?
ใช้วิธีแบ่งหัวข้อการทำงานอย่างชัดเจนโดยใช้ GitHub Repository ในการรวบรวมไฟล์เอกสารและไฟล์โค้ด สมาชิกทุกคนมีการอัปเดตไฟล์เนื้อหาผ่านการ Commit มีการพูดคุยสื่อสารช่องทางออนไลน์เพื่อตรวจสอบความถูกต้องของเนื้อหาให้สอดคล้องกันก่อนบันทึกงาน

#### Problems encountered
1. **การจัดโครงสร้างไฟล์บน GitHub:** สมาชิกในกลุ่มช่วงแรกยังไม่ชินกับการสร้างโฟลเดอร์สำหรับเก็บไฟล์โค้ด `.rs` และโครงสร้างโปรเจกต์
2. **การตั้งค่าสภาพแวดล้อมการทำงาน:** พบปัญหาการตั้งค่าและลง Extension ของเครื่องมือพัฒนาโปรแกรมก่อนการสั่งรันโค้ดจริง

#### How did you solve them?
1. ร่วมกันออกแบบโครงสร้างโฟลเดอร์กลาง `code_examples/` ให้ชัดเจน และแนะนำขั้นตอนการกดสร้างไฟล์พร้อมโฟลเดอร์ผ่านหน้าเว็บ GitHub ให้สมาชิกในกลุ่มทำตามได้ง่ายขึ้น
2. ช่วยกันสืบค้นวิธีแก้ไขข้อผิดพลาดใน Terminal จนสามารถสั่งรันและ Compile โค้ดผ่านคำสั่ง `cargo run` ได้อย่างถูกต้องครบถ้วนก่อนส่งงานครับ
---

## 15. Final Checklist

- [✓] Learning Objectives ครบ 3–4 ข้อ
- [✓] Key Concepts ครบถ้วน
- [✓] Syntax / Rules
- [✓] Runnable Code Examples
- [✓] Code Compile และ Run ได้จริง
- [✓] Common Mistakes
- [✓] Exercises 2 ข้อ พร้อม Solutions
- [✓] PPL Perspective
- [✓] Rust vs Other Language
- [✓] References อย่างน้อย 4 แหล่ง
- [✓] AI Usage Declaration
- [✓] GitHub Contribution
- [✓] สมาชิกทั้ง 4 คนมีส่วนร่วม
- [✓] สมาชิกทั้ง 4 คนพร้อมนำเสนอคนละ 5 นาที
- [✓] สมาชิกทุกคนสามารถอธิบาย Code ของกลุ่มได้

---

## Submission Information

**Repository:** `[https://github.com/670710128/rust-tutorial-2569]`

**Chapter Path:** `[06-conditional-structures/]`

**Final PR:** `#[37]`

**Submitted by:** `[Group 06]`

**Date:** `[2026-10-04]`
