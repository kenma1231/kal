# 📐 Refleksi Geometri

## 🔗 Demo Interaktif
clik link ini untuk mengarah ke colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1Lz38CM2TZ-KhdKLYer2dtQ_u4aGe6XMO?usp=sharing)

> **Cara pakai:** Klik badge di atas → Colab terbuka → Jalankan cell → UI langsung muncul.

---

> **Refleksi** (pencerminan) adalah transformasi geometri yang memindahkan setiap titik
> pada suatu bangun ke posisi baru yang merupakan **bayangan cerminnya** terhadap suatu sumbu.
> Jarak titik asal ke sumbu cermin **selalu sama** dengan jarak bayangan ke sumbu cermin.

---

## 1. Konsep Dasar

Bayangkan kamu meletakkan cermin datar di atas kertas berkotak. Setiap titik pada bangun
akan memiliki bayangan di sisi lain cermin, dengan jarak yang persis sama. Itulah refleksi.

Dua hal yang **tidak berubah** setelah refleksi:

- Ukuran dan bentuk bangun (kongruen)
- Jarak antar titik

Satu hal yang **berubah**:

- Orientasi — bangun terlihat "terbalik" seperti di cermin

---

## 2. Refleksi terhadap Sumbu X

### Aturan

$$
(x,\ y) \xrightarrow{\text{Ref. sumbu X}} (x,\ -y)
$$

Nilai **x tetap**, nilai **y dibalik tandanya**.

### Cara kerja

Sumbu X adalah garis cermin horizontal. Setiap titik "dijatuhkan" tegak lurus ke sumbu X,
lalu dipantulkan sejauh yang sama ke sisi bawah (atau atas).

```
Titik asal  P(3, 4)
             │  ↑ 4 satuan
─────────────┼──────────  ← Sumbu X (cermin)
             │  ↓ 4 satuan
Bayangan    P'(3, -4)
```

### Contoh

| Titik Asal | Bayangan Ref-X | Keterangan         |
|:----------:|:--------------:|:-------------------|
| (2, 3)     | (2, -3)        | y positif → negatif |
| (5, -1)    | (5, 1)         | y negatif → positif |
| (4, 0)     | (4, 0)         | Titik di sumbu X tidak berpindah |
| (-3, 6)    | (-3, -6)       | x tidak berubah    |

### Rumus umum untuk bangun dengan n titik

Jika bangun memiliki titik-titik $A(x_1, y_1),\ B(x_2, y_2),\ \ldots$, maka setelah refleksi
terhadap sumbu X:

$$
A'(x_1,\ -y_1),\quad B'(x_2,\ -y_2),\quad \ldots
$$

---

## 3. Refleksi terhadap Sumbu Y

### Aturan

$$
(x,\ y) \xrightarrow{\text{Ref. sumbu Y}} (-x,\ y)
$$

Nilai **y tetap**, nilai **x dibalik tandanya**.

### Cara kerja

Sumbu Y adalah garis cermin vertikal. Setiap titik "didorong" tegak lurus ke sumbu Y,
lalu dipantulkan sejauh yang sama ke sisi kiri (atau kanan).

```
Bayangan       Titik asal
P'(-3, 4)      P(3, 4)
     ←3─────────┼─────3→
                │
               Sumbu Y
               (cermin)
```

### Contoh

| Titik Asal | Bayangan Ref-Y | Keterangan         |
|:----------:|:--------------:|:-------------------|
| (2, 3)     | (-2, 3)        | x positif → negatif |
| (-5, 1)    | (5, 1)         | x negatif → positif |
| (0, 7)     | (0, 7)         | Titik di sumbu Y tidak berpindah |
| (6, -4)    | (-6, -4)       | y tidak berubah    |

### Rumus umum untuk bangun dengan n titik

$$
A'(-x_1,\ y_1),\quad B'(-x_2,\ y_2),\quad \ldots
$$

---

## 4. Perbandingan Refleksi X vs Refleksi Y

| Aspek            | Refleksi Sumbu X        | Refleksi Sumbu Y        |
|:-----------------|:-----------------------:|:-----------------------:|
| Cermin / sumbu   | Sumbu X (horizontal)    | Sumbu Y (vertikal)      |
| Koordinat berubah | y → -y                 | x → -x                  |
| Koordinat tetap  | x                       | y                        |
| Arah bayangan    | Atas ↔ Bawah            | Kiri ↔ Kanan             |
| Contoh           | (3, 5) → (3, -5)        | (3, 5) → (-3, 5)        |

---

## 5. Cara Menggambar Refleksi (Manual)

### Langkah-langkah

1. **Tentukan titik-titik** sudut bangun asal, misalnya persegi $ABCD$.
2. **Terapkan rumus** pada setiap titik untuk mendapatkan bayangan.
3. **Plot** titik-titik bayangan di sistem koordinat.
4. **Hubungkan** titik-titik bayangan sesuai urutan semula.
5. **Verifikasi** — ukur jarak setiap titik asal ke sumbu, bandingkan dengan jarak bayangan ke sumbu (harus sama).

### Contoh lengkap: Persegi ABCD

Titik asal:

$$
A(2,\ 2),\quad B(5,\ 2),\quad C(5,\ 5),\quad D(2,\ 5)
$$

**Setelah refleksi sumbu X** (y → -y):

$$
A'(2,\ -2),\quad B'(5,\ -2),\quad C'(5,\ -5),\quad D'(2,\ -5)
$$

**Setelah refleksi sumbu Y** (x → -x):

$$
A''(-2,\ 2),\quad B''(-5,\ 2),\quad C''(-5,\ 5),\quad D''(-2,\ 5)
$$

---

## 6. Sifat-Sifat Penting Refleksi

### Isometri (Kongruensi)

Refleksi adalah **transformasi isometri** — bangun bayangan kongruen dengan bangun asal.
Panjang sisi, besar sudut, dan luas bangun tidak berubah.

### Involutif

Jika suatu bangun direfleksikan dua kali terhadap sumbu yang sama, hasilnya kembali ke
posisi semula:

$$
\text{Ref}(\text{Ref}(P)) = P
$$

### Jarak ke Sumbu

Untuk setiap titik $P$ dan bayangannya $P'$:

$$
d(P,\ \text{sumbu}) = d(P',\ \text{sumbu})
$$

Garis $PP'$ selalu **tegak lurus** terhadap sumbu cermin.

### Titik pada Sumbu

Titik yang terletak tepat di atas sumbu cermin **tidak berpindah** (titik tetap / fixed point).

---

## 7. Representasi Matriks

Refleksi dapat ditulis dalam bentuk perkalian matriks, berguna untuk komputasi:

### Refleksi terhadap sumbu X

$$
\begin{pmatrix} x' \\ y' \end{pmatrix}
=
\begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}
\begin{pmatrix} x \\ y \end{pmatrix}
$$

### Refleksi terhadap sumbu Y

$$
\begin{pmatrix} x' \\ y' \end{pmatrix}
=
\begin{pmatrix} -1 & 0 \\ 0 & 1 \end{pmatrix}
\begin{pmatrix} x \\ y \end{pmatrix}
$$

### Implementasi di Python (NumPy)

```python
import numpy as np

# Titik-titik bangun (kolom = satu titik)
points = np.array([[2, 5, 5, 2],   # baris x
                   [2, 2, 5, 5]])  # baris y

# Matriks refleksi sumbu X
M_refx = np.array([[ 1,  0],
                   [ 0, -1]])

# Matriks refleksi sumbu Y
M_refy = np.array([[-1,  0],
                   [ 0,  1]])

ref_x = M_refx @ points   # hasil refleksi X
ref_y = M_refy @ points   # hasil refleksi Y

print("Asal  :", points.T)
print("Ref-X :", ref_x.T)
print("Ref-Y :", ref_y.T)
```

---

## 8. Penjelasan Kode Visualisasi

Kode `refleksi_geometri.py` bekerja dengan langkah berikut:

### Perhitungan refleksi

```python
# Pengguna memasukkan 4 titik
pts = [(2, 2), (5, 2), (5, 5), (2, 5)]

# Refleksi X: balik tanda y
ref_x = [(x, -y) for x, y in pts]

# Refleksi Y: balik tanda x
ref_y = [(-x, y) for x, y in pts]
```

### Animasi (kunci perbaikan)

Animasi menggunakan **interpolasi linier** dari titik asal ke titik tujuan.
Persamaan interpolasi untuk setiap frame $f$ dari total $F$ frame:

$$
x_t = x_0 + (x_1 - x_0) \cdot \frac{f}{F}, \qquad
y_t = y_0 + (y_1 - y_0) \cdot \frac{f}{F}
$$

```python
for f in range(frames + 1):
    t = f / frames
    interp = [
        (
            pts[i][0] + (target[i][0] - pts[i][0]) * t,  # interpolasi x
            pts[i][1] + (target[i][1] - pts[i][1]) * t,  # interpolasi y
        )
        for i in range(4)
    ]
```

> **Catatan perbaikan:** Versi sebelumnya menggunakan variabel `OFFSET` untuk menggeser
> posisi bangun di layar, sehingga interpolasi dimulai dari koordinat yang salah dan animasi
> terlihat "melompat". Versi baru menghapus OFFSET — semua bangun digambar di koordinat
> aslinya, dan interpolasi berjalan dengan benar dari awal hingga akhir.

---

## 9. Latihan

Coba kerjakan soal-soal berikut, lalu verifikasi dengan program:

1. Segitiga dengan titik $P(1, 3),\ Q(4, 1),\ R(2, 5)$.
   Tentukan bayangan setelah refleksi terhadap sumbu X dan sumbu Y.

2. Trapesium $A(-3, 0),\ B(3, 0),\ C(2, 4),\ D(-2, 4)$.
   Refleksikan terhadap sumbu X. Apakah ada titik yang tidak berpindah?

3. Jika bayangan suatu titik setelah refleksi sumbu Y adalah $(5, -3)$,
   berapakah koordinat titik asalnya?

4. Sebuah bangun direfleksikan terhadap sumbu X, kemudian hasilnya direfleksikan lagi
   terhadap sumbu Y. Apakah hasil akhirnya sama dengan rotasi 180° terhadap titik asal?
   Jelaskan dengan contoh!

---

*Dibuat untuk mendampingi program `refleksi_geometri.py` di Google Colab.*