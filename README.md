# Projek UTS ARVR Bagian AR
### Tema: 3d Rooms

#### Dibuat oleh Mohammad Usman Asegaf

#### Berikut adalah demonya:

https://github.com/user-attachments/assets/c284556d-87ee-4e43-accc-d2898aa17e7e

perubahan yang tadinya akan bebarengan dengan uas namun terlalu banyak bug:


Fitur yang Ada dalam Kode
Marker-Based AR:

Kode menggunakan AR.js untuk membuat pengalaman Augmented Reality (AR) berbasis marker. Setiap marker (berdasarkan barcode) akan menampilkan objek 3D yang berbeda saat terdeteksi oleh kamera.

Hover Scaling:

Fitur ini memungkinkan objek 3D untuk membesar sedikit saat kursor mouse berada di atasnya. Ini memberikan feedback visual bahwa objek tersebut dapat diinteraksi.

Kode Terkait: Komponen hover-scale menggunakan event listener mouseenter dan mouseleave untuk mengubah skala objek.

Drag and Rotate:

Pengguna dapat menggeser dan memutar objek 3D dengan mouse atau sentuhan (pada perangkat mobile). Ini meningkatkan interaktivitas dengan objek AR.

Kode Terkait: Komponen drag-rotate menggunakan event listener mousedown, mousemove, mouseup, serta touchstart, touchmove, dan touchend untuk mendukung interaksi pada perangkat mobile.

Marker Sound:

Setiap kali marker terdeteksi, suara akan diputar. Saat marker hilang, suara akan berhenti. Ini menambahkan elemen audio untuk meningkatkan pengalaman AR.

Kode Terkait: Komponen marker-sound menggunakan event listener markerFound dan markerLost untuk mengontrol pemutaran suara.

Click Animation:

Saat objek 3D diklik, objek akan melakukan animasi scaling (membesar atau mengecil). Ini memberikan feedback visual saat pengguna berinteraksi dengan objek.

Kode Terkait: Komponen click-animation menggunakan event listener click untuk memicu animasi scaling.

Animasi Rotasi Otomatis:

Objek 3D tertentu (seperti pokemon_arena.glb) memiliki animasi rotasi otomatis yang berputar 360 derajat secara terus-menerus.

Kode Terkait: Atribut animation pada entitas a-entity dengan properti rotation.

Text Labels:

Setiap marker memiliki teks label yang muncul di atas objek 3D. Label ini memberikan informasi tentang objek yang ditampilkan.

Kode Terkait: Elemen <a-text> yang ditempatkan di dalam <a-marker>.

Cursor Interactivity:

Kursor kamera memungkinkan pengguna untuk berinteraksi dengan objek 3D secara langsung. Kursor ini akan berubah saat berada di atas objek yang dapat diinteraksi.

Kode Terkait: Elemen <a-cursor> di dalam <a-entity camera>.

Lighting:

Pencahayaan directional ditambahkan untuk meningkatkan visualisasi objek 3D. Pencahayaan ini membantu objek terlihat lebih realistis.

Kode Terkait: Elemen <a-light> dengan tipe directional.

Responsive Design:

Kode dirancang untuk bekerja di berbagai perangkat, termasuk desktop dan mobile. Ini dicapai dengan menangani event touch dan mouse secara bersamaan.

Kode Terkait: Penanganan event touchstart, touchmove, dan touchend di komponen drag-rotate.

Penjelasan Kode
Komponen hover-scale:

Komponen ini mendeteksi ketika kursor mouse berada di atas objek (mouseenter) dan mengubah skala objek. Saat kursor meninggalkan objek (mouseleave), skala objek dikembalikan ke ukuran semula.

Kode Terkait:

javascript
Copy
el.addEventListener('mouseenter', () => { ... });
el.addEventListener('mouseleave', () => { ... });
Komponen marker-sound:

Komponen ini memutar suara saat marker terdeteksi (markerFound) dan menghentikan suara saat marker hilang (markerLost).

Kode Terkait:

javascript
Copy
el.addEventListener('markerFound', () => { this.sound.play(); });
el.addEventListener('markerLost', () => { this.sound.pause(); });
Komponen drag-rotate:

Komponen ini memungkinkan pengguna untuk memutar objek dengan menyeret mouse atau sentuhan. Perubahan posisi mouse atau sentuhan (mousemove atau touchmove) dihitung untuk mengubah rotasi objek.

Kode Terkait:

javascript
Copy
el.addEventListener('mousedown', (e) => { ... });
window.addEventListener('mousemove', (e) => { ... });
window.addEventListener('touchmove', (e) => { ... });
Komponen click-animation:

Komponen ini memicu animasi scaling saat objek diklik. Animasi ini didefinisikan melalui atribut animation yang diteruskan ke komponen.

Kode Terkait:

javascript
Copy
el.addEventListener('click', () => { ... });
Animasi Rotasi Otomatis:

Animasi ini diterapkan pada objek pokemon_arena.glb dengan properti rotation yang berubah dari 0 0 0 ke 0 360 0 dalam durasi 8000 ms (8 detik) dan diulang secara terus-menerus.

Kode Terkait:

html
Copy
animation="property: rotation; to: 0 360 0; startEvents: loaded; dur: 8000; loop: true"
Run HTML
Marker dan Objek 3D:

Setiap marker (<a-marker>) memiliki objek 3D (<a-entity gltf-model>) yang ditampilkan saat marker terdeteksi. Objek ini dilengkapi dengan skala, rotasi, dan animasi yang sesuai.

Kode Terkait:

html
Copy
<a-marker type="barcode" value="0">
  <a-entity gltf-model="assets/pokemon_arena.glb" ...></a-entity>
</a-marker>
Run HTML
Text Labels:

Label teks (<a-text>) ditempatkan di atas objek 3D untuk memberikan informasi tambahan.

Kode Terkait:

html
Copy
<a-text value="Arena" position="0 3 0" anchor="center" color="white"></a-text>
Run HTML
Kamera dan Kursor:

Kamera (<a-entity camera>) dilengkapi dengan kursor (<a-cursor>) yang memungkinkan interaksi dengan objek 3D.

Kode Terkait:

html
Copy
<a-entity camera>
  <a-cursor></a-cursor>
</a-entity>
Run HTML
Pencahayaan:

Pencahayaan directional (<a-light>) ditambahkan untuk meningkatkan visualisasi objek 3D.

Kode Terkait:

html
Copy
<a-light type="directional" position="0 5 5" intensity="1.5"></a-light>
Run HTML

