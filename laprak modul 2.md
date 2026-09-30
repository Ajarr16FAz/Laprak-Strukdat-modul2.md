# <h1 align="center">Laporan Praktikum Modul 1 - Codeblocks IDE & Pengenalan Bahas C++ (Bagian Pertama)</h1>
<p align="center">Muhammad Azhar nur Hafizh - 109082500049</p>

## Dasar Teori
Bahasa C++ diciptakan oleh Bjarne Stroustrup di AT&T Bell Laboratories pada awal tahun 1980-an. Bahasa ini berawal dari bahasa C yang ditambahi fasilitas kelas, sehingga pada mulanya disebut "C with class", lalu disempurnakan dengan penambahan pembebanlebihan operator dan fungsi hingga menjadi C++ [3]. Pada praktikum ini, C++ dipakai sebagai bahasa untuk mempelajari dasar-dasar pemrograman sebelum masuk ke materi struktur data.

### A. Struktur Program dan Identifier<br/>
Secara umum, program C++ tersusun dari beberapa bagian, yaitu pemanggilan *library* (`#include`), pendefinisian konstanta, pendefinisian tipe data bentukan, deklarasi variabel, deklarasi fungsi/prosedur, dan program utama `main()` [3]. Setiap pernyataan (*statement*) dalam C++ diakhiri dengan tanda titik koma (;).
#### 1. Library
Fungsi `cout` dan `cin` berada di *header file* `<iostream>`, sehingga harus dipanggil dengan `#include <iostream>` agar bisa dipakai [3].
#### 2. Identifier
*Identifier* adalah nama yang dipakai untuk variabel, konstanta, fungsi, atau objek lain. Aturannya: harus diawali huruf atau garis bawah (_), tidak boleh mengandung spasi, tidak boleh memakai operator aritmatika, dan bersifat *case sensitive* sehingga `panjang` berbeda dengan `Panjang` [3].
#### 3. Fungsi main()
`main()` adalah fungsi utama tempat program mulai dijalankan. Blok program ditulis di dalam kurung kurawal `{ }` dan biasanya diakhiri dengan `return 0;` [3].

### B. Tipe Data, Variabel, dan Konstanta<br/>
Data dapat dinyatakan dalam bentuk variabel atau konstanta. Tipe data dasar yang dibahas pada modul adalah `char`, `int`, `long`, `float`, dan `double` [3].
#### 1. Tipe Data Dasar
`int` dipakai untuk bilangan bulat, `float` dan `double` untuk bilangan pecahan (real) dengan presisi tunggal dan ganda, sedangkan `char` untuk karakter [3].
#### 2. Variabel
Variabel dipakai untuk menyimpan nilai yang bisa berubah selama program berjalan. Bentuk deklarasinya adalah `tipe_data nama_variabel;` dan variabel juga bisa langsung diberi nilai awal, misalnya `int x = 20;` [3].
#### 3. Konstanta
Konstanta menyimpan nilai yang selalu tetap. Untuk mendeklarasikannya cukup menambahkan kata `const` di depan tipe data, misalnya `const float phi = 3.14;` [3].

### C. Input dan Output<br/>
Operasi masukan dan keluaran pada C++ memakai `cin` dan `cout` dari *library* `iostream` [3].
#### 1. Output dengan cout
`cout` digunakan untuk mencetak data, baik teks maupun angka, dengan operator `<<`. Perintah `endl` atau `\n` dipakai untuk pindah ke baris baru [3].
#### 2. Input dengan cin
`cin` digunakan untuk membaca masukan dari *keyboard* dengan operator `>>`, dan nilainya langsung disimpan ke variabel yang dituju tanpa perlu penentu format seperti pada `printf()` [3].
#### 3. Escape Sequence
*Escape sequence* adalah karakter khusus yang diawali tanda `\`, contohnya `\n` untuk baris baru dan `\t` untuk tabulasi [3].

### D. Operator<br/>
Operator adalah simbol yang dipakai untuk melakukan suatu operasi atau manipulasi [3].
#### 1. Operator Aritmatika
Terdiri dari penjumlahan (+), pengurangan (-), perkalian (*), pembagian (/), dan sisa bagi (%). Untuk mengubah urutan pengerjaan dapat dipakai tanda kurung [3]. Pada pembagian dua bilangan bulat, hasilnya juga bilangan bulat sehingga bagian desimalnya dibuang.
#### 2. Operator Relasi dan Logika
Operator relasi (`==`, `!=`, `<`, `<=`, `>`, `>=`) dipakai untuk membandingkan dua nilai, sedangkan operator logika (`&&`, `||`, `!`) dipakai untuk menggabungkan atau membalik kondisi [3].
#### 3. Operator Increment dan Decrement
Operator `++` menambah nilai variabel sebanyak 1, sedangkan `--` menguranginya sebanyak 1 [3].

### E. Kondisional dan Perulangan<br/>
Untuk mengambil keputusan, C++ menyediakan pernyataan `if`, `if-else`, dan `switch` [3]. Untuk mengulang suatu proses, C++ menyediakan `for`, `while`, dan `do...while`, dan setiap perulangan harus punya kondisi berhenti [3].
#### 1. if dan if-else
Pernyataan `if` menjalankan perintah hanya jika kondisinya benar, dan `else` menjalankan perintah lain jika kondisinya salah [3].
#### 2. switch
`switch` dirancang khusus untuk pengambilan keputusan dengan banyak alternatif. Setiap `case` biasanya diakhiri `break`, dan `default` dijalankan bila tidak ada `case` yang cocok [3].
#### 3. for, while, dan do...while
Perulangan `for` cocok saat jumlah pengulangan sudah diketahui, `while` memeriksa kondisi di awal, sedangkan `do...while` memeriksa kondisi di akhir sehingga pasti berjalan minimal satu kali [3].

## Unguided 

### 1. Buatlah program yang dapat melakukan operasi penjumlahan, pengurangan, dan perkalian matriks 3x3.

```C++
#include <iostream>
using namespace std;

void tampilkanMatriks(int mat[3][3]) {
    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            cout << mat[i][j] << "\t";
        }
        cout << endl;
    }
}

int main() {
    int A[3][3] = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
    int B[3][3] = {{9, 8, 7}, {6, 5, 4}, {3, 2, 1}};
    int hasil[3][3];

    cout << "Penjumlahan Matriks (A + B):\n";
    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            hasil[i][j] = A[i][j] + B[i][j];
        }
    }
    tampilkanMatriks(hasil);

    cout << "\nPengurangan Matriks (A - B):\n";
    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            hasil[i][j] = A[i][j] - B[i][j];
        }
    }
    tampilkanMatriks(hasil);

    cout << "\nPerkalian Matriks (A * B):\n";
    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            hasil[i][j] = 0;
            for(int k = 0; k < 3; k++) {
                hasil[i][j] += A[i][k] * B[k][j];
            }
        }
    }
    tampilkanMatriks(hasil);

    return 0;
}
```
### Output Unguided 1 : 
<img width="1103" height="345" alt="Screenshot 2026-09-30 231137.png" src="(https://github.com/Ajarr16FAz/Laprak-Strukdat-modul2.md/blob/main/Screenshot%202026-09-30%20231137.png)" />


Program ini menggunakan array 2 dimensi berukuran 3x3. Penjumlahan dan pengurangan dilakukan dengan mengoperasikan elemen pada indeks yang sama ($[i][j]$). Sementara itu, perkalian matriks menggunakan tiga perulangan (nested loop) untuk menghitung hasil kali baris dan kolom.

### 2. Berdasarkan guided pointer dan reference sebelumnya, buatlah keduanya dapat menukar nilai dari 3 variabel.

```C++
#include <iostream>
using namespace std;

void tukarPointer(int *a, int *b, int *c) {
    int temp = *a;
    *a = *b;
    *b = *c;
    *c = temp;
}

void tukarReference(int &a, int &b, int &c) {
    int temp = a;
    a = b;
    b = c;
    c = temp;
}

int main() {
    int x = 1, y = 2, z = 3;
    cout << "Nilai awal: x = " << x << ", y = " << y << ", z = " << z << endl;

    tukarPointer(&x, &y, &z);
    cout << "Setelah tukar pointer: x = " << x << ", y = " << y << ", z = " << z << endl;

    tukarReference(x, y, z);
    cout << "Setelah tukar reference: x = " << x << ", y = " << y << ", z = " << z << endl;

    return 0;
}
```
### Output Unguided 2 :


Program ini mendemonstrasikan dua cara melewatkan parameter, yaitu pointer (menggunakan tanda * dan mengirim alamat memori dengan &) serta reference (menggunakan tanda & pada parameter fungsi). Logika penukarannya menggeser nilai secara siklikal: nilai a disimpan ke temp, a diubah menjadi b, b menjadi c, dan c menjadi nilai temp.

### 3. Diketahui sebuah array 1 dimensi sebagai berikut:
arrA = {11, 8, 5, 7, 12, 26, 3, 54, 33, 55}
Buatlah program yang dapat mencari nilai minimum, maksimum, dan rata-rata dari array tersebut! Gunakan function cariMinimum() untuk mencari nilai minimum dan function cariMaksimum() untuk mencari nilai maksimum, serta gunakan prosedur hitungRataRata() untuk menghitung nilai rata-rata! Buat program menggunakan menu switch-case

```C++
#include <iostream>
using namespace std;

int cariMinimum(int arr[], int n) {
    int minVal = arr[0];
    for(int i = 1; i < n; i++) {
        if(arr[i] < minVal) {
            minVal = arr[i];
        }
    }
    return minVal;
}

int cariMaksimum(int arr[], int n) {
    int maxVal = arr[0];
    for(int i = 1; i < n; i++) {
        if(arr[i] > maxVal) {
            maxVal = arr[i];
        }
    }
    return maxVal;
}

void hitungRataRata(int arr[], int n) {
    float jumlah = 0;
    for(int i = 0; i < n; i++) {
        jumlah += arr[i];
    }
    float rataRata = jumlah / n;
    cout << "Nilai rata-rata: " << rataRata << endl;
}

int main() {
    int arrA[] = {11, 8, 5, 7, 12, 26, 3, 54, 33, 55};
    int n = sizeof(arrA) / sizeof(arrA[0]);
    int pilihan;

    do {
        cout << "\nMenu Program Array\n";
        cout << "1. Tampilkan isi array\n";
        cout << "2. Cari nilai maksimum\n";
        cout << "3. Cari nilai minimum\n";
        cout << "4. Hitung nilai rata-rata\n";
        cout << "5. Keluar\n";
        cout << "Pilihan Anda: ";
        cin >> pilihan;

        switch(pilihan) {
            case 1:
                cout << "Isi array: ";
                for(int i = 0; i < n; i++) {
                    cout << arrA[i] << " ";
                }
                cout << endl;
                break;
            case 2:
                cout << "Nilai maksimum: " << cariMaksimum(arrA, n) << endl;
                break;
            case 3:
                cout << "Nilai minimum: " << cariMinimum(arrA, n) << endl;
                break;
            case 4:
                hitungRataRata(arrA, n);
                break;
            case 5:
                cout << "Keluar dari program.\n";
                break;
            default:
                cout << "Pilihan tidak valid!\n";
        }
    } while(pilihan != 5);

    return 0;
}
```
### Output Unguided 3 :



Program ini menggunakan array satu dimensi arrA. Terdapat fungsi cariMinimum dan cariMaksimum yang mengembalikan nilai bertipe int, serta prosedur hitungRataRata (menggunakan tipe void) untuk menampilkan hasil perhitungan rata-rata. Seluruh fungsionalitas diakses secara interaktif menggunakan kontrol menu switch-case di dalam perulangan do-while.

## Kesimpulan
Secara keseluruhan, ketiga program C++ ini mengimplementasikan konsep struktur data yang esensial: program pertama menggunakan array dua dimensi untuk melakukan operasi dasar matriks 3x3 meliputi penjumlahan, pengurangan, dan perkalian; program kedua mendemonstrasikan teknik manipulasi memori melalui pointer dan reference untuk menukar nilai tiga variabel sekaligus; serta program ketiga berhasil mengintegrasikan penggunaan fungsi (cariMinimum, cariMaksimum), prosedur (hitungRataRata), dan menu interaktif switch-case untuk mengelola serta menganalisis elemen-elemen di dalam array satu dimensi secara modular.

## Referensi
[2] Modul 2 Struktur Data: Code Blocks IDE & Pengenalan Bahasa C++ (Bagian kedua). Fakultas Informatika, Telkom University.
