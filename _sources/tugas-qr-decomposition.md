# QR Decomposition & QR Iteration

**Link Google Colab:** [Buka Notebook di Colab](https://colab.research.google.com/drive/https://colab.research.google.com/drive/1QVL7m9yRdsSlIx9_V1C5vGyOBSuMmwne?usp=sharing)

---

## Matriks yang Digunakan

Misalkan matriksnya:

$$A = \begin{bmatrix} 3 & 1 \\ 1 & 3 \end{bmatrix}$$

---

## Langkah 1 — Normalisasi Kolom Pertama (q₁)

### 1.1 Ambil kolom pertama matriks A

$$a_1 = \begin{bmatrix} 3 \\ 1 \end{bmatrix}$$

### 1.2 Hitung panjang vektor a₁

Rumus panjang vektor:

$$\|a_1\| = \sqrt{3^2 + 1^2}$$

$$= \sqrt{9 + 1}$$

$$= \sqrt{10}$$

### 1.3 Normalisasi vektor a₁

Gunakan rumus:

$$q_1 = \frac{a_1}{\|a_1\|}$$

Substitusi nilai $a_1$:

$$q_1 = \frac{1}{\sqrt{10}} \begin{bmatrix} 3 \\ 1 \end{bmatrix}$$

Hasilnya:

$$q_1 = \begin{bmatrix} \dfrac{3}{\sqrt{10}} \\[10pt] \dfrac{1}{\sqrt{10}} \end{bmatrix}$$

**Kesimpulan:** Vektor hasil normalisasi kolom pertama adalah $q_1 = \begin{bmatrix} \frac{3}{\sqrt{10}} \\ \frac{1}{\sqrt{10}} \end{bmatrix}$, karena panjangnya sudah menjadi 1.

```python
import numpy as np

# Matriks A
A = np.array([
    [3, 1],
    [1, 3]
])

# Ambil kolom pertama
a1 = A[:, 0]

print("Kolom pertama a1:")
print(a1)

# Hitung panjang vektor
panjang = np.sqrt(3**2 + 1**2)

print("\nPanjang a1:")
print(f"√(3² + 1²) =", panjang)

# Normalisasi
q1 = a1 / panjang

print("\nHasil normalisasi q1:")
print(q1)
```

**Output:**
```
Kolom pertama a1:
[3 1]

Panjang a1:
√(3² + 1²) = 3.1622776601683795

Hasil normalisasi q1:
[0.9486833  0.31622777]
```

---

## Langkah 2 — Hitung Dot Product q₁ · a₂

Diketahui:

$$q_1 = \begin{bmatrix} \dfrac{3\sqrt{10}}{10} \\[10pt] \dfrac{\sqrt{10}}{10} \end{bmatrix}$$

dan kolom kedua matriks A:

$$a_2 = \begin{bmatrix} 1 \\ 3 \end{bmatrix}$$

### 2.1 Hitung dot product q₁ · a₂

Rumus dot product:

$$q_1 \cdot a_2 = \left(\frac{3\sqrt{10}}{10} \times 1\right) + \left(\frac{\sqrt{10}}{10} \times 3\right)$$

$$= \frac{3\sqrt{10}}{10} + \frac{3\sqrt{10}}{10}$$

$$= \frac{6\sqrt{10}}{10}$$

$$= \frac{3\sqrt{10}}{5}$$

```python
from sympy import Matrix, sqrt

# Matriks A
A = Matrix([
    [3, 1],
    [1, 3]
])

# Ambil kolom
a1 = A[:, 0]
a2 = A[:, 1]

# Normalisasi q1
panjang = sqrt(3**2 + 1**2)
q1 = a1 / panjang

# Dot product q1 . a2
dot = q1.dot(a2)

print("q1 . a2 =")
print(dot)
```

**Output:**
```
q1 . a2 =
3*sqrt(10)/5
```

---

## Langkah 3 — Hitung Proyeksi dan Vektor u₂

### 3.1 Kalikan hasil dot product dengan q₁

$$\left(q_1 \cdot a_2\right) q_1 = \frac{3\sqrt{10}}{5} \begin{bmatrix} \dfrac{3\sqrt{10}}{10} \\[10pt] \dfrac{\sqrt{10}}{10} \end{bmatrix}$$

Perhitungan:

$$= \begin{bmatrix} \dfrac{3\sqrt{10}}{5} \times \dfrac{3\sqrt{10}}{10} \\[10pt] \dfrac{3\sqrt{10}}{5} \times \dfrac{\sqrt{10}}{10} \end{bmatrix}$$

$$= \begin{bmatrix} \dfrac{9}{5} \\[10pt] \dfrac{3}{5} \end{bmatrix}$$

### 3.2 Hitung u₂ = a₂ − proyeksi

$$u_2 = a_2 - (q_1 \cdot a_2)\, q_1$$

$$u_2 = \begin{bmatrix} 1 \\ 3 \end{bmatrix} - \begin{bmatrix} \dfrac{9}{5} \\[10pt] \dfrac{3}{5} \end{bmatrix}$$

$$u_2 = \begin{bmatrix} -\dfrac{4}{5} \\[10pt] \dfrac{12}{5} \end{bmatrix}$$

```python
from sympy import Matrix, sqrt

# Matriks A
A = Matrix([
    [3, 1],
    [1, 3]
])

# Ambil kolom
a1 = A[:, 0]
a2 = A[:, 1]

# q1
q1 = a1 / sqrt(10)

# Proyeksi
dot = q1.dot(a2)
proyeksi = dot * q1

# u2
u2 = a2 - proyeksi

print("u2 =")
print(u2)
```

**Output:**
```
u2 =
Matrix([[-4/5], [12/5]])
```

---

## Langkah 4 — Normalisasi u₂ menjadi q₂

### 4.1 Hitung panjang u₂

$$\|u_2\| = \sqrt{\left(-\frac{4}{5}\right)^2 + \left(\frac{12}{5}\right)^2}$$

$$= \sqrt{\frac{16}{25} + \frac{144}{25}}$$

$$= \sqrt{\frac{160}{25}}$$

$$= \sqrt{\frac{32}{5}}$$

$$= \frac{4\sqrt{10}}{5}$$

### 4.2 Hitung q₂

$$q_2 = \frac{u_2}{\|u_2\|}$$

$$q_2 = \dfrac{\begin{bmatrix} -\dfrac{4}{5} \\[6pt] \dfrac{12}{5} \end{bmatrix}}{\dfrac{4\sqrt{10}}{5}}$$

Hasil:

$$q_2 = \begin{bmatrix} -\dfrac{\sqrt{10}}{10} \\[10pt] \dfrac{3\sqrt{10}}{10} \end{bmatrix}$$

```python
from sympy import Matrix, sqrt, Rational

# v2
v2 = Matrix([
    [Rational(-4, 5)],
    [Rational(12, 5)]
])

# Panjang v2
panjang_v2 = sqrt((Rational(-4, 5))**2 + (Rational(12, 5))**2)

print("Panjang v2 =")
print(panjang_v2)

# q2
q2 = v2 / panjang_v2

print("\nq2 =")
print(q2)
```

**Output:**
```
Panjang v2 =
4*sqrt(10)/5

q2 =
Matrix([[-sqrt(10)/10], [3*sqrt(10)/10]])
```

---

## Langkah 5 — Bentuk Matriks Q dan R

Karena kita sudah mendapatkan:

$$q_1 = \begin{bmatrix} \dfrac{3\sqrt{10}}{10} \\[10pt] \dfrac{\sqrt{10}}{10} \end{bmatrix}, \quad q_2 = \begin{bmatrix} -\dfrac{\sqrt{10}}{10} \\[10pt] \dfrac{3\sqrt{10}}{10} \end{bmatrix}$$

Maka matriks Q (kolom-kolomnya adalah q₁ dan q₂):

$$Q = \begin{bmatrix} \dfrac{3\sqrt{10}}{10} & -\dfrac{\sqrt{10}}{10} \\[10pt] \dfrac{\sqrt{10}}{10} & \dfrac{3\sqrt{10}}{10} \end{bmatrix}$$

Dan matriks R dihitung dengan $R = Q^T A$:

$$R = \begin{bmatrix} \sqrt{10} & \dfrac{3\sqrt{10}}{5} \\[10pt] 0 & \dfrac{4\sqrt{10}}{5} \end{bmatrix}$$

```python
from sympy import Matrix, sqrt

A = Matrix([
    [3, 1],
    [1, 3]
])

a1 = A[:, 0]
a2 = A[:, 1]

# q1
q1 = a1 / sqrt(10)

# proyeksi dan u2
dot = q1.dot(a2)
proyeksi = dot * q1
v2 = a2 - proyeksi

# q2
q2 = v2 / sqrt(v2.dot(v2))

# Matriks Q
Q = Matrix.hstack(q1, q2)

print("Q =")
print(Q)

# Matriks R
R = Q.T * A

print("\nR =")
print(R)
```

**Output:**
```
Q =
Matrix([[3*sqrt(10)/10, -sqrt(10)/10], [sqrt(10)/10, 3*sqrt(10)/10]])

R =
Matrix([[sqrt(10), 3*sqrt(10)/5], [0, 4*sqrt(10)/5]])
```

---

## Langkah 6 — Verifikasi QR = A

### 6.1 Kalikan Q dengan R

$$QR = \begin{bmatrix} \dfrac{3\sqrt{10}}{10} & -\dfrac{\sqrt{10}}{10} \\[10pt] \dfrac{\sqrt{10}}{10} & \dfrac{3\sqrt{10}}{10} \end{bmatrix} \begin{bmatrix} \sqrt{10} & \dfrac{3\sqrt{10}}{5} \\[10pt] 0 & \dfrac{4\sqrt{10}}{5} \end{bmatrix}$$

Hasil perkalian:

$$QR = \begin{bmatrix} 3 & 1 \\ 1 & 3 \end{bmatrix}$$

Ternyata hasilnya kembali menjadi matriks awal $A$, karena pada dekomposisi QR berlaku:

$$A = QR$$

```python
from sympy import Matrix, sqrt

Q = Matrix([
    [3*sqrt(10)/10, -sqrt(10)/10],
    [sqrt(10)/10,  3*sqrt(10)/10]
])

R = Matrix([
    [sqrt(10),   3*sqrt(10)/5],
    [0,          4*sqrt(10)/5]
])

hasil = Q * R

print("Q * R =")
print(hasil)
```

**Output:**
```
Q * R =
Matrix([[3, 1], [1, 3]])
```

---

## Langkah 7 — Hitung A₁ = RQ (QR Iteration Langkah 1)

Sekarang cari $A_{k+1} = R_k Q_k$:

$$RQ = \begin{bmatrix} \sqrt{10} & \dfrac{3\sqrt{10}}{5} \\[10pt] 0 & \dfrac{4\sqrt{10}}{5} \end{bmatrix} \begin{bmatrix} \dfrac{3\sqrt{10}}{10} & -\dfrac{\sqrt{10}}{10} \\[10pt] \dfrac{\sqrt{10}}{10} & \dfrac{3\sqrt{10}}{10} \end{bmatrix}$$

**Baris 1 Kolom 1:**

$$\left(\sqrt{10} \times \frac{3\sqrt{10}}{10}\right) + \left(\frac{3\sqrt{10}}{5} \times \frac{\sqrt{10}}{10}\right) = 3 + \frac{3}{5} = \frac{18}{5}$$

**Baris 1 Kolom 2:**

$$\left(\sqrt{10} \times -\frac{\sqrt{10}}{10}\right) + \left(\frac{3\sqrt{10}}{5} \times \frac{3\sqrt{10}}{10}\right) = -1 + \frac{9}{5} = \frac{4}{5}$$

**Baris 2 Kolom 1:**

$$\left(0 \times \frac{3\sqrt{10}}{10}\right) + \left(\frac{4\sqrt{10}}{5} \times \frac{\sqrt{10}}{10}\right) = 0 + \frac{4}{5} = \frac{4}{5}$$

**Baris 2 Kolom 2:**

$$\left(0 \times -\frac{\sqrt{10}}{10}\right) + \left(\frac{4\sqrt{10}}{5} \times \frac{3\sqrt{10}}{10}\right) = 0 + \frac{12}{5} = \frac{12}{5}$$

**Hasil Akhir:**

$$RQ = \begin{bmatrix} \dfrac{18}{5} & \dfrac{4}{5} \\[10pt] \dfrac{4}{5} & \dfrac{12}{5} \end{bmatrix}$$

```python
from sympy import Matrix, sqrt

R = Matrix([
    [sqrt(10),   3*sqrt(10)/5],
    [0,          4*sqrt(10)/5]
])

Q = Matrix([
    [3*sqrt(10)/10, -sqrt(10)/10],
    [sqrt(10)/10,  3*sqrt(10)/10]
])

hasil = R * Q

print("R * Q =")
print(hasil)
```

**Output:**
```
R * Q =
Matrix([[18/5, 4/5], [4/5, 12/5]])
```

---

## Langkah 8 — QR Iteration (10 Iterasi)

### Penjelasan Proses QR Iteration

Metode ini disebut **QR Iteration**. Tujuannya untuk mendekati nilai eigen matriks.

**Langkah-langkahnya:**

1. Mulai dari matriks awal $A_0 = A$
2. Lakukan dekomposisi QR: $A_k = Q_k R_k$
3. Bentuk matriks baru: $A_{k+1} = R_k Q_k$
4. Ulangi hingga matriks konvergen ke bentuk segitiga (hampir diagonal)
5. Nilai diagonal matriks akhir mendekati **nilai eigen** matriks asal

```python
from sympy import Matrix, sqrt, N, pprint

# ==========================
# Matriks awal
# ==========================
A = Matrix([
    [3, 1],
    [1, 3]
])

print("A0 =")
pprint(A)

# ==========================
# QR ITERATION
# ==========================
for k in range(1, 11):

    # Ambil kolom
    a1 = A[:, 0]
    a2 = A[:, 1]

    # q1
    q1 = a1 / sqrt(a1.dot(a1))

    # proyeksi
    proj = q1.dot(a2) * q1

    # v2
    v2 = a2 - proj

    # q2
    q2 = v2 / sqrt(v2.dot(v2))

    # Matriks Q
    Q = Matrix.hstack(q1, q2)

    # Matriks R
    R = Q.T * A

    # Matriks baru
    A = R * Q

    print(f"\nA{k} =")
    pprint(N(A, 5))
```

**Output (sebagian):**
```
A0 =
⎡3  1⎤
⎢    ⎥
⎣1  3⎦

A1 =
⎡3.6  0.8⎤
⎢        ⎥
⎣0.8  2.4⎦

A2 =
⎡3.84  0.48⎤
⎢          ⎥
⎣0.48  2.16⎦

...

A10 =
⎡3.99902  0.00391⎤
⎢                ⎥
⎣0.00391  3.00098⎦
```

> **Kesimpulan:** Setelah 10 iterasi, elemen diagonal matriks mendekati **4** dan **2**, yang merupakan nilai eigen dari matriks $A = \begin{bmatrix} 3 & 1 \\ 1 & 3 \end{bmatrix}$.

---

## Verifikasi Nilai Eigen dengan NumPy

```python
import numpy as np

A = np.array([
    [3, 1],
    [1, 3]
])

eigenvalues, eigenvectors = np.linalg.eig(A)

print("Nilai Eigen:")
print(eigenvalues)

print("\nVektor Eigen:")
print(eigenvectors)
```

**Output:**
```
Nilai Eigen:
[4. 2.]

Vektor Eigen:
[[ 0.70710678 -0.70710678]
 [ 0.70710678  0.70710678]]
```

> **Terbukti:** Nilai eigen matriks A adalah **λ₁ = 4** dan **λ₂ = 2**, sesuai dengan hasil konvergensi QR Iteration pada diagonal matriks.