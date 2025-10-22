# tugas_1_dasarpemrograman-
tugas mandiri program menghitung gaji karyawan 
# Fungsi untuk menghitung gaji karyawan
def hitung_gaji(golongan, pendidikan, jam_kerja):
    gaji_pokok = 300_000

    # Persentase tunjangan jabatan
    tunjangan_golongan = {
        1: 0.02,
        2: 0.10,
        3: 0.15
    }

    # Persentase tunjangan pendidikan
    tunjangan_pendidikan = {
        "SMA": 0.025,
        "D1": 0.05,
        "D3": 0.10,
        "S1": 0.30
    }

    # Hitung tunjangan jabatan
    persen_jabatan = tunjangan_golongan.get(golongan, 0)
    nilai_jabatan = gaji_pokok * persen_jabatan

    # Hitung tunjangan pendidikan
    persen_pendidikan = tunjangan_pendidikan.get(pendidikan.upper(), 0)
    nilai_pendidikan = gaji_pokok * persen_pendidikan

    # Hitung honor lembur
    honor_lembur = 0
    if jam_kerja > 8:
        honor_lembur = (jam_kerja - 8) * 3500

    # Total gaji
    total_gaji = gaji_pokok + nilai_jabatan + nilai_pendidikan + honor_lembur

    return nilai_jabatan, nilai_pendidikan, honor_lembur, total_gaji

# Input dari pengguna
print("PROGRAM HITUNG GAJI KARYAWAN\n")
nama = input("Nama Karyawan: ")
golongan = int(input("Golongan Jabatan: "))
pendidikan = input("Pendidikan: ")
jam_kerja = int(input("Jumlah jam kerja: "))

# Hitung gaji
tunjangan_jabatan, tunjangan_pendidikan, honor_lembur, total_gaji = hitung_gaji(golongan, pendidikan, jam_kerja)

# Output
print("\nKaryawan yang bernama", nama)
print("Honor yang diterima")
print(f"Tunjangan Jabatan     Rp {tunjangan_jabatan:,.0f}")
print(f"Tunjangan Pendidikan  Rp {tunjangan_pendidikan:,.0f}")
print(f"Honor Lembur          Rp {honor_lembur:,.0f}")
print("-" * 40)
print(f"Total Gaji (Gaji pokok + tunjangan + lembur) Rp {total_gaji:,.0f}")
