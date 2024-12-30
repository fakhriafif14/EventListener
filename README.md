# Project-OOP-berbasis-MVC


1.Package classes (Komponen Dasar):


BaseModel.java

Class abstrak untuk operasi database dasar

Mendefinisikan method CRUD: findAll(), findById(), insert(), update(), delete()

Menggunakan generic type <T> untuk fleksibilitas

Menyimpan koneksi database yang akan digunakan subclass


Database.java

Mengelola koneksi MySQL
Konfigurasi: localhost:3306/akademik_db
Username: root, tanpa password
Menggunakan driver mysql-connector-j-8.0.31


RowMapper.java

Interface untuk konversi ResultSet ke objek
Memudahkan mapping data dari database ke class model




Package model (Data dan Akses Data):


Mahasiswa.java

POJO class dengan properti: id, nim, nama, jurusan, alamat
Dilengkapi constructor dan getter/setter
Merepresentasikan entitas mahasiswa dalam program


MahasiswaModel.java

Extends BaseModel<Mahasiswa>
Implementasi operasi database spesifik untuk mahasiswa
Menggunakan PreparedStatement untuk keamanan
RowMapper untuk konversi ResultSet ke objek Mahasiswa
Query SQL untuk CRUD operations




Package view (Interface Pengguna):


FormMahasiswa.java

JFrame dengan layout BorderLayout
Komponen:

Form input (GridLayout): ID, NIM, Nama, Jurusan, Alamat
Panel tombol: Save, Delete, Clear
Tabel data mahasiswa dengan scrolling


Method untuk:

Mendapatkan data form (getMahasiswa())
Mengupdate tabel (setMahasiswas())
Membersihkan form (clearForm())
Menambah event listener






Package controller (Logika Aplikasi):


MahasiswaController.java

Menghubungkan MahasiswaModel dan FormMahasiswa
Menangani operasi:

Menyimpan data (insert/update)
Menghapus data
Membersihkan form
Refresh tabel


Error handling dengan JOptionPane
Event handling untuk tombol-tombol form




Main.java:


Entry point aplikasi
Inisialisasi:

Koneksi database
Model, View, Controller
Menampilkan form


Error handling untuk kegagalan koneksi

Flow Program:

User membuka aplikasi
Form ditampilkan dengan tabel data existing
User dapat:

Input data baru
Edit data existing
Hapus data
Clear form


Setiap aksi akan:

Diproses controller
Diupdate ke database via model
Refresh tampilan tabel
Menampilkan feedback ke user



Database Operations:

Insert: Menambah mahasiswa baru
Update: Mengubah data mahasiswa existing
Delete: Menghapus data berdasarkan ID
Select: Mengambil semua data atau by ID
