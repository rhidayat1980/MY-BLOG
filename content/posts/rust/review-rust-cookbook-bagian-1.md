---
title: "Review Rust Cookbook bagian 1"
date: 2018-07-27T23:38:52+07:00
draft: false
---

Jadi ceritanya malam ini karena dede inara ga bisa tidur, akhirnya saya kebagian temenin anak ini sampai dia ngantuk lagi.

Sambil temenin dede inara saya putuskan untuk baca buku rust, `Rust Cookbook by Vigneshwer Dhinakaran`, lumayan pikir saya.

Oke sesuai judulnya review buku, maka saya akan coba untuk mereview buku ini. Buku `rust cookbook` ini terdiri dari beberapa bab, di bagi menjadi dua bagian, bagian pertama berisi tentang basic thing in rust seperti:

### settting up Rust in Windows, Linux dan Mac

Bagian ini sesuai judulnya si `Vigneshwer Dhinakaran` ngasi tau soal cara instalasi rust di beberapa platform system operasi. ga ada yg istimewa sih di bab ini, karena gw bisa liat langsung di webnya rust [https://www.rust-lang.org/en-US/install.html]

perintahnya juga simple sih

```bash
curl https://sh.rustup.rs -sSf | sh
```

kalo lo udah berhasil nginstall rust bisa langsung cek pake command

```bash
rustc --version
rustc 1.27.2 (58cc626de 2018-07-18)
```

By default ketika lo nginstall rust dia akan ngasih lu compiler(rustc), cargo atau tool yg lo pake untuk manage semua code rust lo, mulai dari scafolding, manage dependency,testing dan compile. jadi si rustc jarang lo pake juga sih, kecuali kalo lo ga mau pake cargo misalnya untuk prototype yg sederhana kaya contoh dibawah. yg lo dapat juga selain compiler dan cargo adalah rustup.

Si `rustup` ini keren sih menerut gw, nih contohnya

```bash
rustup update
rustup doc
```

Fungsi ke dua perintah diatas adalah yg pertama ngapdate rust version, dan yg kedua lo bisa dapat dokumentasi rust di komputer lo, lumayan buat ngurangin ketergantungan sama internet, kaya pas lagi di perjalan dalam pesawat atau kereta api, cobain deh!


### creating your first program in rust

Bagian ini si penulis nasih contoh gimana cara bikin program sederhana di rust.

```bash
mkdir rust_cookbook
cd rust_cookbook
touch sample.rs
```

Lalu open sesuai editor kesukaanmu, content nya seperti dibawah ini

```rust
fn main(){
  println!("Welcome to Rust Cookbook");
}
```

Save lalu jalanin perintah ini

```bash
rustc sample.rs
```

Proses compiling diatas ngasilin sebuah binary code dengan nama sample, kalo di windows ya sample.exe , udah lama banget gw ga liat .exe :)

Cara jalaninnya kalo di linux atau mac ya

```bash
./sample
```

akan ngasillin `Welcome to Rust Cookbook`

### defining a variable assignment

dibagian ini layaknya buku-buku programming lainnya, biasanya dimulai dengan variable assignment.

contoh yang ada dibuku ini kira-kira seperti ini
bikin file `assignment.rs` lalu paste content dibawah ini.

```rust
// Primitive libraries in rust
use std::{i8,i16,i32,i64,u8,u16,u32,u64,f32,f64,isize,usize};
use std::io::stdin;

fn main() {
    println!("Understanding assignment");
    // Compiler will automatically figure out the data type if not mentioned
    // Cannot change the value
    let num =10;
    println!("Num is {}", num);

    let age: i32 =40;
    println!("Age is {}", age);
    // Prints the max and min value of 32bit integer
    println!("Max i32 {}",i32::MAX);
    println!("Max i32 {}",i32::MIN);

    // Another way of variable assigning
    let(f_name,l_name)=("viki","d");
    println!("First name {0} and last name {1}",f_name,l_name);
}
```

save lalu kamu bisa compile pake rustc assignment.rs
jalanin pake `./assignment` outputnya kamu coba sendiri yah :P

pelajaran yg bisa gw dapat adalah, `use` untuk import bahkan standard lib, beda bgt sama elixir :), lalu setiap program pasti dimulai dengan `fn main()`, lalu ada `let` yang bisa di pakai dengan cara yg unik `let(f_name,l_name)=("viki","d");` which is ini pattern matching cuy! dan `println!`, dan terakhir interpolation dengan `{}`.

gw ga akan detilin jelasinnya yah, lo beli aja bukunya cuy hehehe.

### setting up boolean and character types

Bagian ini ngasitau salah dua data types yang ada di rust, boolean dan character.
boolean ada `false` dan `true` sedangkan char membernya ada banyak dan dia ga jelasin apa aja yg masuk character di rust hehehe, not good.

cotoh program yg di pakai di bab ini adalah `boolean-char.rs`

```rust
fn main(){

    //Setting boolean and character types
    let bool_val: bool = true;
    let x_char: char = 'a';

    // Printing the character
    println!("x char is {}", x_char);
    println!("Bool value is {}", bool_val);
}
```

save dan compile pake `rustc boolean-char.rs` lalu jalanin pake ./boolean-char dan lihat hasilnya.

### Controlling decimal points, number formats, and named arguments

```rust
fn main(){
    // Prints the first 2 numbers after the decimal points
    println!("{:.2}",1.2345 );
    println!("================");

    // print the binary hex and octal format
    println!("B: {:b} H: {:x} O: {:o}",10,10,10 );
    println!("================");

    // Shifts
    println!("{ten:>ws$}",ten=10, ws=5 );
    println!("{ten:>0ws$}",ten=10, ws=5 );
}
```

lo harus mulai kuat liat karakter2 aneh cuy. kaya `{:.2}, 1.2345`, ini maksudnya lo hanya mau ngeprint 2 desimal dibelakang koma. lainnya lo cari tau sendiri yah soal converting decimal ke biner, hexa dan octal, yg terakhir itu shifting aja sih sebanyak 5 white spaces, `ws` disini white spaces, ekspresi terakhir itu ganti whitespace nya dengan angka 0.

### Performing arithmetic operations

bab ini ngasih contoh operasi matematika, dengan operator-operator standar. bikin file `arithmetic.rs` lalu isi kaya gini

```rust
fn main(){
    // Arithmetic Operations
    println!("5 + 4 = {}", 5+4 );
    println!("5 - 4 = {}", 5-4 );
    println!("5 * 4 = {}", 5*4 );
    println!("5 / 4 = {}", 5/4 );
    println!("5 % 4 = {}", 5%4 );

    // Assigning data types and mathematical Operations
    let neg_4 = -4i32;
    println!("abs(-4) = {}", neg_4.abs() );
    println!("abs(-4) = {}", neg_4.pow(2) );
    println!("round(1.2345) = {}", 1.2354f64.round() );
    println!("ceil(1.2345) = {}", 1.2345f64.ceil() );
    print!("sin 3.14 = {}", 3.14f64.sin() );
}
```

Oia gw lupa ngasih tau kalo rust termasuk static type, nah biasanya bahasa-bahasa kaya rust ini sifatnya strict gt. misalnya melibatkan dua type yg berbeda kaya `100 / 3` dia ngasilin 33 aja cuy bukan 33.33333, lu harus kasih tau dia exactly `100 / 3.0` untuk dapat nilai yg benernya.

patternnya di rust adalah object.methods misalnya `"ini string".slice`, mirip2 ruby ya :)

### defining mutable variable

Di Rust semuanya by default immutable, kecuali lo ngasih tau saat define variable pake keyword `mut`.

contohnya

```rust
fn main(){
    let mut sample_var = 10;
    println!(“Value of the sample variable is {}”,sample_var);
    let sample_var = 20;
    println!(“New Value of the sample variable is {}”,sample_var);
}
```

kalo lo ga ngasih `mut` maka ekspresi println! yg kedua akan gagal, rust compiler akan ngasih tau lo sih kenapa-kenapanya, ini salah satu enaknya compiler rust, cerdas gt dia. lo coba deh hilangin `mut` dalam contoh diatas dan liat sendiri apa yg gw maksud denga rust compiler yg cerdas.

bagian selanjutnya adalah operasi pada string

### Declaring and performing string operations

oia karena dede inara nya gw lirik udah mulai nguap-nguap, jadi gw bagi aja review buku rust cookbook ini jadi beberapa bagian ya. lagi pula lo bakalan muntah kali baca tulisan gw yg ga bermutu ini wkwkwkwk.
