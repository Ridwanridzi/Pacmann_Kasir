# Dokumentasi
---
## Rangkuman

---
### Latar Belakang
Andi ingin menambahkan sistem self-service di supermarket miliknya agar customer bisa membeli barang sesuai kebutuhan mereka di tempat yang jauh dari supermarket, misalnya saat di kota lain

### Penjelasan Requirements & Objectives
#### Requirement:
- **add_item([ <nama_item>, <jumlah_item>, <harga_per_item> ])** <br/>
&nbsp;Method yang digunakan untuk menambahkan item sesuai dengan data dibawah ini:
  - **<nama_item>:** attribute nama barang yang akan dibeli oleh customer
  - **<jumlah_item>:** attribute jumlah barang yang akan dibeli oleh customer
  - **<harga_per_item>:** attribute harga barang per satuan
- **update_item_name(<id_item>, <update_nama_item>)** <br/>
&nbsp;Method yang digunakan untuk mengubah nama barang sesuai dengan id barang
	- **<id_item>:** attribute id barang yang akan diubah oleh customer
	- **<update_nama_item>:** attribute nama barang yang baru
- **update_item_qty(<id_item>, <update_jumlah_item>)**
&nbsp;Method yang digunakan untuk mengubah jumlah barang sesuai dengan id barang
	- **<id_item>**: attribute id barang yang akan diubah oleh customer
	- **<update_jumlah_item>**: attribute jumlah barang yang baru
- **update_item_price(<id_item>, <update_harga_item>)**
&nbsp;Method yang digunakan untuk mengubah harga barang sesuai dengan id barang
	- **<id_item>**: attribute id barang yang akan diubah oleh customer
	-	**<update_harga_item>**: attribute harga barang yang baru
- **delete_item(<id_item>)** <br/>
&nbsp;Method yang digunakan untuk menghapus salah satu atau beberapa item barang dari list keranjang barang yang akan dibeli berdasarkan id barang
  - **<id_item>:** attribute id barang yang akan dihapus oleh customer
- **reset_transaction()** <br/>
&nbsp;Method yang digunakan untuk menghapus semua barang belanjaan di dalam list keranjang yang tidak akan dibeli
- **check_order()** <br/>
&nbsp;Method yang digunakan untuk mengecek barang yang telah diinputkan kedalam keranjang, apakah sudah sesuai dengan keinginan atau tidak. Ditampilkan dalam bentuk tabel.
- **total_price()** <br/>
&nbsp;Method yang digunakan untuk menampilkan harga total keseluruhan item barang yang dibeli beserta diskonnya. Nilai yang ditampilkan adalah total harga yang telah dikenakan diskon.

#### Objektif:
Membuat aplikasi python kasir self-service sehingga customer/pelanggan bisa menginput barang sendiri sesuai dengan yang mereka inginkan

### Penjelasan Flowchart
![alt text]((https://github.com/Ridwanridzi/Pacmann_Kasir/blob/main/flowchart.png))

### Conclusion

---

## Test Case

### Tambah Barang
```python
# inisialisasi transaksi dengan instance
transaksi_1 = Transaction()

# menambah item
transaksi_1.add_items(['kompor', 2, 100_000])
transaksi_1.add_items(['mie', 5, 3_000])
transaksi_1.add_items(['tempe', 3, 5_000])

# menampilkan pesanan
transaksi_1.check_order()

# menampilkan output test case
# {'nama_item': [jumlah, harga]}
transaksi_1.test_case_output(transaksi_1.keranjang)
```
### Update Barang
```python
# inisialisasi transaksi dengan instance baru
transaksi_2 = Transaction()

# menambah item
transaksi_2.add_items(['kompor', 2, 100_000])
transaksi_2.add_items(['mie', 5, 3_000])
transaksi_2.add_items(['tempe', 3, 5_000])

# mengubah nama item
transaksi_2.update_item_name(id_item=3, update_nama='tahu')

# mengubah harga item
transaksi_2.update_item_price(id_item=1, update_harga=150_000)

# mengubah jumlah item
transaksi_2.update_item_qty(id_item=2, update_jumlah=10)

# menampilkan output test case
# {'nama_item': [jumlah, harga]}
transaksi_2.test_case_output(transaksi_2.keranjang)
```
### Delete Barang
```python
# inisialisasi transaksi dengan instance baru
transaksi_3 = Transaction()

# menambah item
transaksi_3.add_items(['kompor', 2, 100_000])
transaksi_3.add_items(['mie', 5, 3_000])
transaksi_3.add_items(['tempe', 3, 5_000])

# menghapus item
transaksi_3.delete_item(2)

# menampilkan output test case
# {'nama_item': [jumlah, harga]}
transaksi_3.test_case_output(transaksi_3.keranjang)
```
### Check Order

#### Check tanpa error
```python
# inisialisasi transaksi dengan instance baru
transaksi_4 = Transaction()

# menambah item
transaksi_4.add_items(['kompor', 2, 100_000])
transaksi_4.add_items(['mie', 5, 3_000])
transaksi_4.add_items(['tempe', 3, 5_000])

# menghapus item
print("Dibawah ini output check_order")
transaksi_4.check_order()

# menampilkan output test case
# {'nama_item': [jumlah, harga]}
transaksi_4.test_case_output(transaksi_4.keranjang)
```
#### Check jika error
```python
# inisialisasi transaksi dengan instance baru
transaksi_5 = Transaction()

# menambah item
transaksi_5.add_items(['kompor', 2, 100_000])
transaksi_5.add_items(['mie', '5', 3_000])
transaksi_5.add_items(['tempe', 3, 5_000])

# menghapus item
print("Dibawah ini output check_order")
transaksi_5.check_order()

# menampilkan output test case
# {'nama_item': [jumlah, harga]}
transaksi_5.test_case_output(transaksi_5.keranjang)
```
### Reset Transaksi
```python
# inisialisasi transaksi dengan instance baru
transaksi_6 = Transaction()

# menambah item
transaksi_6.add_items(['kompor', 2, 100_000])
transaksi_6.add_items(['mie', 5, 3_000])
transaksi_6.add_items(['tempe', 3, 5_000])

# menampilkan output test case
# {'nama_item': [jumlah, harga]}
transaksi_6.test_case_output(transaksi_6.keranjang)

# reset transaksi
transaksi_6.reset_transaction()

# cek pesanan
transaksi_6.check_order()
```
### Total Harga
```python
# inisialisasi transaksi dengan instance
transaksi_7 = Transaction()

# menambah item
transaksi_7.add_items(['kompor', 2, 100_000])
transaksi_7.add_items(['mie', 5, 3_000])
transaksi_7.add_items(['tempe', 3, 5_000])

# menampilkan output test case
# {'nama_item': [jumlah, harga]}
transaksi_7.test_case_output(transaksi_7.keranjang)

# hitung total belanja (termasuk diskon)
transaksi_7.total_price()
```
### Menu Transaksi
```python
transaksi = Transaction()
transaksi.menu()
```
