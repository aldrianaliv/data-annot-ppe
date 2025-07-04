# Synapsis.id : ML Data Engineer Challenges

PT. Qwerty ingin mengembangkan sistem berbasis Artificial Intelligence (AI) untuk mendeteksi pelanggaran  Personal Protective Equipment (PPE) yang dilakukan personil di ruang lingkup kerja melalui footage di CCTV. 

Secara garis besar, PT. Qwerty meminta sistem AI ini untuk dapat **mendeteksi** jika personil **mengenakan/tidak mengenakan PPE**. PT. Qwerty mewajibkan personil untuk mengenakan atribut sebagai berikut:

> - Hardhat : Helmet
> - Safety Vest : Vest
> - Gloves : Gloves
> - Safety Glasses : Glasses
> - Steel-toe boot : Boots

## Dataset Annotation Planning
### Skema Labeling
| Label | Definition |
|-------|------------|
| Helmet | Pelindung kepala berbahan keras dan berwarna cerah (merah, putih, kuning, biru, hijau, merah muda/pink dan jingga)|
| Vest | Rompi berwarna cerah (jingga atau hijau neon) dengan bahan reflektif |
| Gloves | Sarung tangan untuk pelindung tangan, membalut hingga pergelangan tangan |
| Glasses | Kacamata pelindung mata |
| Boots | Sepatu yang menutupi pergelangan kaki|

### Pertimbangan Skema Labeling

Di area konstruksi yang berisiko tinggi, daftar alat pelindung diri (PPE) konstruksi sangat penting untuk melindungi karyawan dari berbagai risiko. Selain kemampuan PPE yang tepat untuk mencegah kecelakaan, daftar ini juga berperan krusial dalam meningkatkan budaya keselamatan di tempat kerja. OSHA telah menunjukkan bahwa penggunaan alat pelindung diri yang tepat secara signifikan mengurangi kemungkinan terjadinya insiden.

![Construction PPE](https://www.slingsby.com/media/catalog/product/4/2/428897_2.jpg?optimize=medium&bg-color=255,255,255&fit=bounds&height=700&width=700&canvas=700:700)

Kelima label yang diajukan adalah komponen utama PPE yang krusial untuk keselamatan pekerja.

> - Helmet: Melindungi kepala dari benturan benda jatuh atau kecelakaan.
> - Vest: Memastikan visibilitas pekerja di area berbahaya.
> - Gloves: Melindungi tangan dari luka potong, bakar, atau bahan kimia.
> - Boots: Melindungi kaki dari benda tajam, beban berat, atau cairan serta membantu mobilitas melalui medan yang berat.
> - Glasses: Melindungi mata dari debu, percikan las, atau partikel kecil.

### Panduan Anotasi
#### Base Guideline:
- Anotasi dilakukan menggunakan format bounding box persegi panjang mengelilingi objek.

- Setiap objek PPE yang terlihat harus diberikan label sesuai dengan skema di atas.

- Fokus hanya pada pekerja manusia dan PPE yang ***digunakan*** oleh manusia.

#### **Extra Cautions**:
**Partial Occlusion:**
- Jika objek PPE sebagian tertutup (contoh: tertutup tangan, alat, atau bagian tubuh lain), tetap anotasi sepanjang identifikasi objek dapat dilakukan dengan yakin.

**Blurry/Low-resolution Image:**
- Jika objek PPE masih dapat dikenali dengan jelas, lakukan anotasi.

- Jika terlalu buram dan tidak dapat dipastikan jenis objeknya, abaikan.

**Multiple People dalam Satu Frame:**
- Anotasi setiap PPE yang terlihat per individu.

- Jika PPE hanya terlihat sebagian (contoh: hanya helm, tidak terlihat wajahnya), tetap anotasi sesuai labelnya.

- Beri perhatian pada overlap antar bounding box agar tidak menutupi objek lain.

