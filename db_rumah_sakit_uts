CREATE DATABASE IF NOT EXISTS db_rumah_sakit;
USE db_rumah_sakit;

-- =====================================================
-- SOAL 1: MEMBUAT 5 TABEL DATABASE RUMAH SAKIT
-- =====================================================

CREATE TABLE IF NOT EXISTS pasien (
    id_pasien INT PRIMARY KEY,
    nama_pasien VARCHAR(100),
    jenis_kelamin CHAR(1),
    tanggal_lahir DATE,
    alamat VARCHAR(200),
    no_hp VARCHAR(15),
    CHECK (jenis_kelamin IN ('L', 'P'))
);

CREATE TABLE IF NOT EXISTS poli (
    id_poli INT PRIMARY KEY,
    nama_poli VARCHAR(100),
    lantai INT,
    status_poli VARCHAR(20),
    CHECK (status_poli IN ('Aktif', 'Nonaktif'))
);

CREATE TABLE IF NOT EXISTS dokter (
    id_dokter INT PRIMARY KEY,
    nama_dokter VARCHAR(100),
    id_poli INT,
    spesialisasi VARCHAR(100),
    tarif_konsultasi DECIMAL(12,2),
    status_dokter VARCHAR(20),
    FOREIGN KEY (id_poli) REFERENCES poli(id_poli),
    CHECK (tarif_konsultasi >= 0),
    CHECK (status_dokter IN ('Aktif', 'Cuti', 'Nonaktif'))
);

CREATE TABLE IF NOT EXISTS kunjungan (
    id_kunjungan INT PRIMARY KEY,
    id_pasien INT,
    id_dokter INT,
    tanggal_kunjungan DATE,
    jenis_kunjungan VARCHAR(30),
    diagnosis VARCHAR(200),
    status_kunjungan VARCHAR(30),
    FOREIGN KEY (id_pasien) REFERENCES pasien(id_pasien),
    FOREIGN KEY (id_dokter) REFERENCES dokter(id_dokter),
    CHECK (jenis_kunjungan IN ('Umum', 'Kontrol', 'Darurat')),
    CHECK (status_kunjungan IN ('Menunggu', 'Diperiksa', 'Selesai', 'Batal'))
);

CREATE TABLE IF NOT EXISTS pembayaran (
    id_pembayaran INT PRIMARY KEY,
    id_kunjungan INT UNIQUE,
    tanggal_bayar DATE,
    biaya_konsultasi DECIMAL(12,2),
    biaya_obat DECIMAL(12,2),
    biaya_laboratorium DECIMAL(12,2),
    diskon DECIMAL(12,2),
    metode_bayar VARCHAR(30),
    status_bayar VARCHAR(20),
    FOREIGN KEY (id_kunjungan) REFERENCES kunjungan(id_kunjungan),
    CHECK (biaya_konsultasi >= 0),
    CHECK (biaya_obat >= 0),
    CHECK (biaya_laboratorium >= 0),
    CHECK (diskon >= 0),
    CHECK (metode_bayar IN ('Tunai', 'Transfer', 'Asuransi')),
    CHECK (status_bayar IN ('Lunas', 'Belum Lunas'))
);

-- =====================================================
-- SOAL 3: DATA PENGUJIAN
-- =====================================================

INSERT INTO pasien
(id_pasien, nama_pasien, jenis_kelamin, tanggal_lahir, alamat, no_hp)
VALUES
(1, 'Andi Saputra', 'L', '2002-05-10', 'Bandar Lampung', '081234567801'),
(2, 'Siti Rahma', 'P', '2003-08-15', 'Kedaton', '081234567802'),
(3, 'Budi Santoso', 'L', '2001-02-20', 'Rajabasa', '081234567803'),
(4, 'Dewi Anggraini', 'P', '2004-11-25', 'Sukarame', '081234567804'),
(5, 'Rizky Pratama', 'L', '2002-07-12', 'Kemiling', '081234567805'),
(6, 'Putri Amelia', 'P', '2003-04-18', 'Way Halim', '081234567806'),
(7, 'Fajar Nugraha', 'L', '2001-09-30', 'Teluk Betung', '081234567807'),
(8, 'Nadia Putri', 'P', '2004-01-05', 'Tanjung Karang', '081234567808'),
(9, 'Dimas Arya', 'L', '2002-12-22', 'Sukabumi', '081234567809'),
(10, 'Intan Permata', 'P', '2003-06-14', 'Langkapura', '081234567810');

INSERT INTO poli
(id_poli, nama_poli, lantai, status_poli)
VALUES
(1, 'Poli Umum', 1, 'Aktif'),
(2, 'Poli Anak', 2, 'Aktif'),
(3, 'Poli Gigi', 1, 'Aktif'),
(4, 'Poli Mata', 2, 'Aktif'),
(5, 'Poli Jantung', 3, 'Aktif'),
(6, 'Poli Kulit', 2, 'Aktif'),
(7, 'Poli Saraf', 3, 'Aktif'),
(8, 'Poli THT', 2, 'Aktif'),
(9, 'Poli Bedah', 3, 'Aktif'),
(10, 'Poli Gizi', 1, 'Nonaktif');

INSERT INTO dokter
(id_dokter, nama_dokter, id_poli, spesialisasi, tarif_konsultasi, status_dokter)
VALUES
(1, 'Dr. Aditya Putra', 1, 'Dokter Umum', 75000, 'Aktif'),
(2, 'Dr. Maya Sari', 2, 'Dokter Anak', 100000, 'Aktif'),
(3, 'Dr. Bima Prakoso', 3, 'Dokter Gigi', 125000, 'Aktif'),
(4, 'Dr. Rina Lestari', 4, 'Dokter Mata', 150000, 'Aktif'),
(5, 'Dr. Dedi Kurniawan', 5, 'Dokter Jantung', 200000, 'Aktif'),
(6, 'Dr. Siska Amelia', 6, 'Dokter Kulit', 125000, 'Cuti'),
(7, 'Dr. Fajar Hidayat', 7, 'Dokter Saraf', 175000, 'Aktif'),
(8, 'Dr. Nanda Putri', 8, 'Dokter THT', 150000, 'Aktif'),
(9, 'Dr. Reza Firmansyah', 9, 'Dokter Bedah', 250000, 'Aktif'),
(10, 'Dr. Citra Dewi', 10, 'Dokter Gizi', 100000, 'Aktif');

INSERT INTO kunjungan
(id_kunjungan, id_pasien, id_dokter, tanggal_kunjungan,
 jenis_kunjungan, diagnosis, status_kunjungan)
VALUES
(1, 1, 1, '2026-10-01', 'Umum', 'Demam', 'Selesai'),
(2, 2, 2, '2026-10-02', 'Umum', 'Flu', 'Selesai'),
(3, 3, 3, '2026-10-03', 'Kontrol', 'Gigi berlubang', 'Selesai'),
(4, 4, 4, '2026-10-04', 'Umum', 'Iritasi mata', 'Selesai'),
(5, 5, 5, '2026-10-05', 'Darurat', 'Nyeri dada', 'Diperiksa'),
(6, 6, 6, '2026-10-06', 'Kontrol', 'Alergi kulit', 'Selesai'),
(7, 7, 7, '2026-10-07', 'Darurat', 'Sakit kepala berat', 'Batal'),
(8, 8, 8, '2026-10-08', 'Umum', 'Radang tenggorokan', 'Selesai'),
(9, 1, 9, '2026-10-09', 'Kontrol', 'Pemeriksaan lanjutan', 'Selesai'),
(10, 2, 1, '2026-10-10', 'Umum', 'Batuk', 'Menunggu'),
(11, 3, 2, '2026-10-11', 'Darurat', 'Demam tinggi', 'Selesai');

INSERT INTO pembayaran
(id_pembayaran, id_kunjungan, tanggal_bayar,
 biaya_konsultasi, biaya_obat, biaya_laboratorium,
 diskon, metode_bayar, status_bayar)
VALUES
(1, 1, '2026-10-01', 75000, 20000, 0, 5000, 'Tunai', 'Lunas'),
(2, 2, '2026-10-02', 100000, 30000, 0, 0, 'Transfer', 'Lunas'),
(3, 3, '2026-10-03', 125000, 50000, 25000, 10000, 'Asuransi', 'Lunas'),
(4, 4, '2026-10-04', 150000, 25000, 0, 0, 'Tunai', 'Lunas'),
(5, 5, '2026-10-05', 200000, 100000, 150000, 25000, 'Transfer', 'Belum Lunas'),
(6, 6, '2026-10-06', 125000, 50000, 0, 5000, 'Asuransi', 'Lunas'),
(7, 7, '2026-10-07', 175000, 0, 0, 0, 'Tunai', 'Belum Lunas'),
(8, 8, '2026-10-08', 150000, 40000, 50000, 10000, 'Transfer', 'Lunas'),
(9, 9, '2026-10-09', 250000, 75000, 100000, 25000, 'Asuransi', 'Lunas'),
(10, 11, '2026-10-11', 100000, 50000, 25000, 0, 'Tunai', 'Belum Lunas');

-- =====================================================
-- SOAL 4: INNER JOIN
-- =====================================================

CREATE OR REPLACE VIEW view_no4 AS
SELECT
    p.id_pasien,
    p.nama_pasien,
    d.id_dokter,
    d.nama_dokter,
    po.nama_poli,
    d.spesialisasi,
    k.tanggal_kunjungan,
    k.status_kunjungan,
    k.diagnosis
FROM kunjungan k
INNER JOIN pasien p
    ON k.id_pasien = p.id_pasien
INNER JOIN dokter d
    ON k.id_dokter = d.id_dokter
INNER JOIN poli po
    ON d.id_poli = po.id_poli;

-- =====================================================
-- SOAL 5: LEFT JOIN
-- =====================================================

CREATE OR REPLACE VIEW view_no5 AS
SELECT
    p.id_pasien,
    p.nama_pasien,
    p.no_hp,
    COUNT(k.id_kunjungan) AS jumlah_kunjungan,
    MAX(k.tanggal_kunjungan) AS kunjungan_terakhir
FROM pasien p
LEFT JOIN kunjungan k
    ON p.id_pasien = k.id_pasien
GROUP BY
    p.id_pasien,
    p.nama_pasien,
    p.no_hp;

-- =====================================================
-- SOAL 6: RIGHT JOIN
-- =====================================================

CREATE OR REPLACE VIEW view_no6 AS
SELECT
    d.nama_dokter,
    d.spesialisasi,
    po.nama_poli,
    k.id_kunjungan,
    k.status_kunjungan
FROM kunjungan k
RIGHT JOIN dokter d
    ON k.id_dokter = d.id_dokter
INNER JOIN poli po
    ON d.id_poli = po.id_poli;

-- =====================================================
-- SOAL 7: JOIN PEMERIKSAAN DAN PEMBAYARAN
-- =====================================================

CREATE OR REPLACE VIEW view_no7 AS
SELECT
    p.nama_pasien,
    d.nama_dokter,
    po.nama_poli,
    k.tanggal_kunjungan,
    k.diagnosis,
    pb.biaya_konsultasi
        + pb.biaya_obat
        + pb.biaya_laboratorium AS total_sebelum_diskon,
    pb.diskon,
    pb.biaya_konsultasi
        + pb.biaya_obat
        + pb.biaya_laboratorium
        - pb.diskon AS total_tagihan,
    pb.metode_bayar,
    pb.status_bayar
FROM kunjungan k
INNER JOIN pasien p
    ON k.id_pasien = p.id_pasien
INNER JOIN dokter d
    ON k.id_dokter = d.id_dokter
INNER JOIN poli po
    ON d.id_poli = po.id_poli
LEFT JOIN pembayaran pb
    ON k.id_kunjungan = pb.id_kunjungan;

-- =====================================================
-- SOAL 8: IF TUNGGAL
-- =====================================================

CREATE OR REPLACE VIEW view_no8 AS
SELECT
    id_pembayaran,
    id_kunjungan,
    tanggal_bayar,
    biaya_konsultasi,
    biaya_obat,
    biaya_laboratorium,
    diskon,
    metode_bayar,
    status_bayar,
    IF(
        diskon > 0,
        'Mendapat Diskon',
        'Tidak Mendapat Diskon'
    ) AS keterangan_diskon
FROM pembayaran;

-- =====================================================
-- SOAL 9: IF MAJEMUK
-- =====================================================

CREATE OR REPLACE VIEW view_no9 AS
SELECT
    id_pembayaran,
    id_kunjungan,
    (
        biaya_konsultasi
        + biaya_obat
        + biaya_laboratorium
        - diskon
    ) AS total_biaya,
    IF(
        (
            biaya_konsultasi
            + biaya_obat
            + biaya_laboratorium
            - diskon
        ) < 100000,
        'Ekonomis',
        IF(
            (
                biaya_konsultasi
                + biaya_obat
                + biaya_laboratorium
                - diskon
            ) < 300000,
            'Menengah',
            'Premium'
        )
    ) AS klasifikasi_biaya
FROM pembayaran;

-- =====================================================
-- SOAL 10: IF MAJEMUK DAN OPERATOR LOGIKA
-- =====================================================

CREATE OR REPLACE VIEW view_no10 AS
SELECT
    k.id_kunjungan,
    k.id_pasien,
    k.id_dokter,
    k.jenis_kunjungan,
    k.status_kunjungan,
    pb.status_bayar,
    IF(
        k.jenis_kunjungan = 'Darurat'
        AND k.status_kunjungan <> 'Batal',
        'Prioritas Tinggi',
        IF(
            k.jenis_kunjungan = 'Kontrol'
            AND k.status_kunjungan = 'Selesai',
            'Kontrol Selesai',
            IF(
                k.status_kunjungan = 'Batal',
                'Tidak Dilayani',
                'Pelayanan Reguler'
            )
        )
    ) AS status_prioritas
FROM kunjungan k
LEFT JOIN pembayaran pb
    ON k.id_kunjungan = pb.id_kunjungan;

-- =====================================================
-- SELESAI: PERINTAH DI BAWAH UNTUK MELIHAT HASIL VIEW
-- Jalankan SELECT ini setelah proses import jika diperlukan.
-- =====================================================

-- SELECT * FROM view_no4;
-- SELECT * FROM view_no5;
-- SELECT * FROM view_no6;
-- SELECT * FROM view_no7;
-- SELECT * FROM view_no8;
-- SELECT * FROM view_no9;
-- SELECT * FROM view_no10;
