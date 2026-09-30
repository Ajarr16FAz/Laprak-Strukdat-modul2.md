# <h1 align="center">Laporan Praktikum Modul 1 - Codeblocks IDE & Pengenalan Bahas C++ (Bagian Pertama)</h1>
<p align="center">Muhammad Azhar nur Hafizh - 109082500049</p>

## Dasar Teori
Bahasa C++ diciptakan oleh Bjarne Stroustrup di AT&T Bell Laboratories pada awal tahun 1980-an [3]. Pada praktikum struktur data ini, C++ digunakan untuk mengimplementasikan berbagai konsep lanjutan seperti array multidimensi, manipulasi memori (pointer dan reference), fungsi, prosedur, serta modularitas program berbasis menu interaktif.

### A. Struktur Program dan Identifier<br/>
Array adalah struktur data yang terdiri dari kumpulan variabel dengan tipe data sama yang disimpan dalam alamat memori berdekatan.Array 1 Dimensi: Digunakan untuk menyimpan deretan data linier, seperti penyimpanan elemen arrA = {11, 8, 5, 7, 12, 26, 3, 54, 33, 55} pada program pencarian nilai minimum, maksimum, dan rata-rata.   Array 2 Dimensi (Matriks): Direpresentasikan dengan dua indeks [baris][kolom], yang sangat efisien untuk operasi aljabar matriks berukuran 3x3 seperti penjumlahan, pengurangan, dan perkalian matriks.

### B. Pointer dan Reference<br/>
Manipulasi memori secara langsung sangat penting dalam struktur data untuk efisiensi pengoperasian data.Pointer (*): Variabel khusus yang menyimpan alamat memori dari variabel lain. Penggunaannya memerlukan operator alamat & untuk mengakses alamat memori dan operator dereferensi * untuk mengakses nilai yang ditunjuk.   Reference (&): Alias atau nama lain dari sebuah variabel yang sudah ada. Parameter reference memungkinkan fungsi mengubah nilai variabel asli secara langsung tanpa perlu menyalin nilainya (pass-by-reference)

### C. Input dan Output<br/>
Output dengan cout: Digunakan untuk mencetak teks, hasil perhitungan, atau menampilkan isi matriks/array ke layar dengan operator <<. Perintah endl atau karakter \n dipakai untuk ganti baris.
Input dengan cin: Menggunakan operator >> untuk membaca data masukan dari keyboard, terutama untuk menerima input pilihan menu interaktif (switch-case).
Escape Sequence: Karakter khusus seperti \t (tabulasi) digunakan untuk merapikan tampilan matriks 3x3 dalam format baris dan kolom.

### D. Operator<br/>
Operator adalah simbol yang memerintahkan kompiler untuk melakukan manipulasi data atau perhitungan.
Operator Aritmatika: Penjumlahan (+), pengurangan (-), perkalian (*), dan pembagian (/) yang digunakan dalam operasi matriks serta perhitungan rata-rata.
Operator Relasi dan Logika: Operator relasi (<, >, ==, !=) dipakai dalam fungsi pencarian nilai minimum/maksimum serta pengecekan menu.
Operator Increment (++): Digunakan pada struktur perulangan (nested loop maupun perulangan for) untuk menaikkan indeks iterasi sebanyak 1.

### E. Kondisional, Perulangan, Pointer, dan Reference<br/>
Percabangan if-else dan switch-case: if-else menyeleksi kondisi nilai (seperti pembanding minimum/maksimum), sedangkan switch-case dirancang untuk menu interaktif dengan banyak alternatif pilihan, diakhiri break serta opsi default.Perulangan (for, do-while): for digunakan untuk menelusuri elemen array/matriks, sedangkan do-while membungkus menu agar program minimal berjalan sekali hingga pengguna memilih keluar.Pointer (*) dan Reference (&): Pointer menyimpan alamat memori dengan operator & dan dereferensi *, sedangkan reference (&) menjadi alias variabel agar fungsi dapat mengubah nilai asli secara langsung (pass-by-reference).   Fungsi dan Prosedur: Fungsi mengembalikan nilai dengan return (misal cariMinimum()), sedangkan prosedur menggunakan tipe void tanpa pengembalian nilai langsung (misal hitungRataRata()).

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
<img width="1160" height="470" alt="Screenshot 2026-09-30 231137" src="https://github.com/user-attachments/assets/38143458-8ee0-4916-9e4f-f309d447850e" />

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

<img width="1470" height="312" alt="Screenshot 2026-09-30 231350" src="https://github.com/user-attachments/assets/ef4ddcab-adfb-4a54-ade7-affeb5253588" />

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
<img width="1077" height="913" alt="Screenshot 2026-09-30 231534" src="https://github.com/user-attachments/assets/b7d1b6a3-b27d-41a9-bd68-0d26488cb745" />


Program ini menggunakan array satu dimensi arrA. Terdapat fungsi cariMinimum dan cariMaksimum yang mengembalikan nilai bertipe int, serta prosedur hitungRataRata (menggunakan tipe void) untuk menampilkan hasil perhitungan rata-rata. Seluruh fungsionalitas diakses secara interaktif menggunakan kontrol menu switch-case di dalam perulangan do-while.

## Kesimpulan
Secara keseluruhan, ketiga program C++ ini mengimplementasikan konsep struktur data yang esensial: program pertama menggunakan array dua dimensi untuk melakukan operasi dasar matriks 3x3 meliputi penjumlahan, pengurangan, dan perkalian; program kedua mendemonstrasikan teknik manipulasi memori melalui pointer dan reference untuk menukar nilai tiga variabel sekaligus; serta program ketiga berhasil mengintegrasikan penggunaan fungsi (cariMinimum, cariMaksimum), prosedur (hitungRataRata), dan menu interaktif switch-case untuk mengelola serta menganalisis elemen-elemen di dalam array satu dimensi secara modular.

## Referensi
[2] Modul 2 Struktur Data: Code Blocks IDE & Pengenalan Bahasa C++ (Bagian kedua). Fakultas Informatika, Telkom University.
