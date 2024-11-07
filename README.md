# Latihan 1: Aplikasi Pertambahan Dua Angka

### Pembuat
- **Nama**: Ferdhyan Dwi Rangga Saputra
- **NPM**: 2210010171

---

## 1. Deskripsi Program
Aplikasi ini merupakan kalkulator sederhana yang memungkinkan pengguna untuk:
- Memasukkan dua angka pada dua TextField.
- Menampilkan hasil penambahan saat tombol **Tambah** diklik.
- Menghapus input di kedua TextField dan mengarahkan fokus ke TextField pertama saat tombol **Hapus** diklik.

## 2. Komponen GUI
- **JFrame**: Window utama aplikasi.
- **JPanel**: Panel untuk menampung komponen.
- **JLabel**: Label deskripsi input dan hasil.
- **JTextField**: Input angka pertama, angka kedua, dan hasil.
- **JButton**: Tombol untuk melakukan operasi **Tambah**, **Hapus**, dan **Keluar**.

## 3. Logika Program
- Operasi penambahan dua angka.
- Validasi input untuk memastikan pengguna memasukkan angka.

## 4. Events
Menggunakan **ActionListener** untuk menangani event dari tombol **Tambah**, **Hapus**, dan **Keluar**:

### A. Tombol Tambah
Menampilkan hasil penambahan setelah memvalidasi input.
```java
private void btnTambahActionPerformed(java.awt.event.ActionEvent evt) {                                          
         try {
            int angkaPertama = Integer.parseInt(txtAngkaPertama.getText());
            int angkaKedua = Integer.parseInt(txtAngkaKedua.getText());
            int hasil = angkaPertama + angkaKedua;
            lblHasil.setText("Hasil: " + hasil); // Menampilkan hasil penjumlahan di JLabel
        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(this, "Input tidak valid! Pastikan hanya memasukkan angka.", "Error", JOptionPane.ERROR_MESSAGE);
            lblHasil.setText("Hasil: Error");
        }
    }  
```

### B. Tombol Hapus
```java
    private void btnHapusActionPerformed(java.awt.event.ActionEvent evt) {                                         
        txtAngkaPertama.setText("");
        txtAngkaKedua.setText("");
        lblHasil.setText("Hasil: ");
        txtAngkaPertama.requestFocus();
    }  
```
### C. Tombol Keluar
```java
    private void btnKeluarActionPerformed(java.awt.event.ActionEvent evt) {                                          
        int confirm = JOptionPane.showConfirmDialog(this, "Apakah Anda yakin ingin keluar?", "Konfirmasi Keluar", JOptionPane.YES_NO_OPTION);
        if (confirm == JOptionPane.YES_OPTION) {
            System.exit(0); // Keluar dari aplikasi
        }
    }                                           
```     
## 5. Variasi:
### A. KeyAdapter pada JTextField untuk membatasi input hanya angka
```java
KeyAdapter hanyaAngkaKeyAdapter = new KeyAdapter() {
            @Override
            public void keyTyped(KeyEvent e) {
                char c = e.getKeyChar();
                if (!Character.isDigit(c) && c != KeyEvent.VK_BACK_SPACE) {
                    e.consume(); // Mengabaikan input selain angka
                    JOptionPane.showMessageDialog(null, "Hanya boleh memasukkan angka.", "Input Error", JOptionPane.ERROR_MESSAGE);
                }
            }
        };

        txtAngkaPertama.addKeyListener(hanyaAngkaKeyAdapter);
        txtAngkaKedua.addKeyListener(hanyaAngkaKeyAdapter);
```
### B. Gunakan JOptionPane untuk menampilkan error input
```java
JOptionPane.showMessageDialog(null, "Hanya boleh memasukkan angka.", "Input Error", JOptionPane.ERROR_MESSAGE);
```
### C. Implementasikan FocusListener untuk membersihkan JTextField saat mendapatkan fokus.
```java
FocusAdapter clearOnFocus = new FocusAdapter() {
            @Override
            public void focusGained(FocusEvent e) {
                ((javax.swing.JTextField) e.getComponent()).setText("");
            }
        };

        txtAngkaPertama.addFocusListener(clearOnFocus);
        txtAngkaKedua.addFocusListener(clearOnFocus);            
```
## 6. Tampilan Saat di Run :
   

![Screenshot 2024-11-07 235039](https://github.com/user-attachments/assets/42b51c97-eca2-4144-9c9b-71394e215460)

## Indikator Penilaian:

| No  | Komponen         |  Persentase  |
| :-: | --------------   |   :-----:    |
|  1  | Komponen GUI     |    20    |
|  2  | Logika Program   |    20    |
|  3  | Events           |    15    |
|  4  | Kesesuaian UI    |    15    |
|  5  | Memenuhi Variasi |    30    |
|     | TOTAL        | 100 |
