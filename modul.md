# Prompt Tugas Akhir SDL

## Digital Bomb Defuse Game Berbasis FSM Moore pada FPGA Nexys A7-100T

Bertindaklah sebagai seorang ahli desain sistem digital, engineer FPGA profesional, serta dosen pembimbing Tugas Akhir yang berpengalaman dalam pengembangan sistem berbasis Verilog HDL menggunakan FPGA Xilinx Nexys A7-100T pada software Xilinx Vivado.

Saya sedang menyusun proyek Tugas Akhir mata kuliah Sistem Digital Lanjut (SDL) dengan judul:

# “Digital Bomb Defuse Game Berbasis Finite State Machine (FSM) Moore pada FPGA Nexys A7-100T”

Tolong bantu saya merancang proyek ini secara lengkap, sistematis, modular, akademis, dan siap digunakan sebagai implementasi Tugas Akhir. Fokus utama proyek adalah penerapan konsep FSM Moore pada sistem permainan digital simulasi penjinak bom (bomb defuse game) yang dijalankan pada FPGA.

---

# Kriteria dan Ketentuan Proyek

## 1. Arsitektur Sistem

Sistem harus dirancang menggunakan pendekatan **Finite State Machine (FSM) tipe Moore**, di mana output hanya dipengaruhi oleh current state.

FSM minimal memiliki 4 state utama berikut:

- **IDLE** → kondisi awal/reset sistem
- **ARMED** → kondisi bom aktif dan countdown berjalan
- **DEFUSED** → kondisi berhasil menjinakkan bom
- **EXPLODED** → kondisi gagal / bom meledak

Diperbolehkan menambahkan state tambahan apabila diperlukan untuk meningkatkan kompleksitas dan kualitas sistem.

---

## 2. Modularitas Program (WAJIB)

Proyek harus menerapkan prinsip **modular programming** pada Verilog HDL dengan memisahkan sistem menjadi beberapa modul independen.

Minimal terdapat 4 modul utama berikut:

### Modul 1 — Behavioral / Dataflow Module

Digunakan untuk:

- Membaca input switch
- Membandingkan kode input pemain dengan kode rahasia
- Menghasilkan sinyal valid/invalid
- Menghitung jumlah kesalahan input

Gunakan pendekatan behavioral atau dataflow modeling.

---

### Modul 2 — Coding Reuse / Top Module

Berfungsi sebagai:

- Modul utama sistem
- Penghubung seluruh submodule
- Tempat instantiation semua modul
- Pengelolaan wiring antar modul

Tambahkan komentar berikut pada bagian paling atas file:

```verilog
// Tugas Akhir - Kelompok 22
```

---

### Modul 3 — Clocking & Display Module

Modul ini wajib mencakup:

#### a. Clock Divider

- Mengubah clock bawaan FPGA Nexys A7 sebesar 100 MHz menjadi clock lambat (misalnya 1 Hz)
- Digunakan untuk countdown timer

#### b. 7-Segment Decoder

- Menampilkan countdown timer
- Menampilkan status tertentu jika diperlukan
- Mendukung display pada 7-segment Nexys A7

---

### Modul 4 — FSM Control Module

Berfungsi sebagai:

- Pengontrol utama seluruh logika sistem
- Pengatur transisi state
- Pengendali output LED, timer, dan status permainan
- Implementasi penuh FSM Moore

---

# 3. Fitur Panic Countdown (WAJIB)

Sistem harus memiliki fitur keamanan berupa **Panic Countdown** dengan ketentuan:

- Setiap input kode yang salah menambah skor kesalahan pemain
- Jika skor kesalahan mencapai 3 kali:
  - Sistem langsung masuk ke state darurat
  - Countdown dipercepat atau langsung menuju state EXPLODED
  - LED indikator bahaya aktif
  - Sistem dianggap gagal

Pastikan logika trigger panic countdown dijelaskan secara detail pada penjelasan program dan FSM.

---

# 4. Komponen Input dan Output

## Input

Gunakan komponen berikut:

- Switch (SW) → sebagai input kode
- Push Button (BTN) → sebagai tombol start/reset/submit

## Output

Gunakan:

- LED → indikator status sistem
- 7-Segment Display → countdown timer
- Optional: buzzer logic / blinking LED simulation

---

# 5. Ketentuan Teknis Verilog

Gunakan:

- Verilog HDL
- Pendekatan synthesizable
- Penulisan kode yang rapi dan mudah dipahami
- Penamaan sinyal yang konsisten
- Komentar penjelas pada setiap bagian penting kode

Hindari:

- Kode redundan
- Multiple driver
- Latch tidak disengaja
- Delay non-synthesizable (#delay)

---

# 6. Target Board dan Software

Gunakan:

- FPGA Board: Nexys A7-100T
- Software: Xilinx Vivado

Pastikan seluruh pin constraint kompatibel dengan Nexys A7-100T.

---

# Output yang Harus Dihasilkan

Tolong hasilkan pembahasan secara berurutan dan lengkap sesuai format berikut:

---

# A. Penjelasan Program

Jelaskan secara rinci:

- Konsep permainan bomb defuse
- Cara kerja sistem secara keseluruhan
- Mekanisme countdown
- Cara kerja FSM Moore
- Fungsi setiap modul
- Alur input dan output
- Mekanisme panic countdown
- Interaksi switch, button, LED, dan 7-segment

---

# B. Desain Diagram FSM

Berikan penjelasan deskriptif mengenai:

- Setiap state
- Fungsi tiap state
- Kondisi transisi antar state
- Input yang mempengaruhi transisi
- Output yang dihasilkan tiap state

Gunakan format yang mudah dipahami untuk dokumentasi laporan.

---

# C. Tabel Kebenaran / State Transition Table

Buat tabel lengkap yang memuat:

- Current State
- Input
- Kondisi
- Next State
- Output

Pastikan tabel sesuai dengan implementasi FSM Moore.

---

# D. Kode Program Verilog Lengkap

Pisahkan kode menjadi beberapa file berikut:

- `Top_Module.v`
- `FSM_Control.v`
- `Clock_Divider.v`
- `Seg7_Decoder.v`
- `Code_Comparator.v`
- (Tambahkan modul lain jika diperlukan)

Pastikan:

- Semua modul saling terhubung
- Tidak ada syntax error
- Siap disimulasikan pada Vivado
- Menggunakan instantiation modular

---

# E. File Constraint (.xdc)

Berikan file `.xdc` lengkap dan akurat khusus untuk Nexys A7-100T yang mencakup:

- Clock pin (E3)
- Switch
- Push button
- LED
- 7-segment display (anode & cathode)

Gunakan format constraint Vivado yang benar.

---

# 7. Tambahan Dokumentasi (Opsional tetapi Direkomendasikan)

Jika memungkinkan, tambahkan:

- Diagram blok sistem
- Penjelasan timing
- Simulasi waveform
- Skenario pengujian
- Penjelasan implementasi pada FPGA nyata
- Analisis kelebihan dan kekurangan sistem

---

# 8. Ketentuan Gaya Penulisan

Gunakan gaya penjelasan yang:

- Formal
- Teknis
- Akademis
- Sistematis
- Mudah dipahami mahasiswa
- Cocok dimasukkan ke laporan Tugas Akhir
- Cocok digunakan untuk presentasi seminar FPGA

Pastikan seluruh pembahasan terstruktur dengan baik dan mendukung implementasi proyek secara nyata pada FPGA Nexys A7-100T menggunakan Xilinx Vivado.
