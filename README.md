# Meluncurkan sebuah Aplikasi React* ke GitHub Pages (Halaman Github)

\* dibuat menggunakan `create-react-app`

# Sumber asli

Kredit untuk [gitname, click here for original tutorial](https://github.com/gitname/react-gh-pages)

# Permulaan

Dalam tutorial ini, Aku akan tunjukkan gimana caranya bisa membuat Aplikasi React dan meluncurkannya ke GitHub Pages.

Untuk membuatnya, kalian gunakan perintah [`create-react-app`](https://create-react-app.dev/) (membutuhkan npm), yaitu alat yang membuat aplikasi React dari awal. Setelah itu, kalian bisa gunakan [`gh-pages`](https://github.com/tschaub/gh-pages), untuk meluncurkan situs web kalian ke [GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages), sebuah layanan web hosting gratis dari Github.

Jika kalian mengikuti tutorial ini dengan benar, kalian akan mendapatkan Aplikasi React benar-benar dijalankan di Github.

## Terjemahan

Tutorial ini telah diterjemahkan dari Bahasa Inggris ke dalam bahasa berikut:
- [Cina Tradisional](https://github.com/gitname/react-gh-pages/issues/167#issuecomment-1925551338) (kredit: [@creaper9487](https://github.com/creaper9487))

# Tutorial

## Persyaratan

1. [Node dan npm](https://nodejs.org/en/download/). Versi yang lebih baru, biasanya lebih baik:
    ```shell
    $ node --version
    v21.6.2

    $ npm --version
    10.2.4
    ```
    > dimana perintah yang digunakan adalah `npm` dan `npx`. Perintah ini akan dipakai di sini.

2. [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git). Bisa dipasang di Windows, Mac, Linux, maupun Android.

    ```shell
    $ git --version
    git version 2.44.0
    ```

3. Akun [GitHub](https://github.com/signup).

4. Khusus kamu pengguna Android, gunakan [Termux](https://github.com/termux):
   - Izinkan Termux menggunakan penyimpanan ponselmu
     ```shell
     $ termux-setup-storage
     ```
   - Tingkatkan paket Termux ke versi baru
     ```shell
     $ pkg upgrade && pkg update
     ```
   - Pasang `git` dan `nodejs`
     ```shell
     $ pkg install git && pkg install nodejs
     ```
   
   Jika sudah, lanjut ke bagian **Prosedur**.
   

## Prosedur

### 1. Buat repositori **kosong** lewat GitHub

1. Masuk ke akun Github.
2. Kunjungi formulir [Create a new repository](https://github.com/new).
3. Isi sesuai data berikut:
    - **Repository name:** Namanya bebas\*.

        > \* Untuk [situs proyek](https://pages.github.com/#project-site), kalian bisa masukkan nama apa saja. Sedangkan [situs pengguna](https://pages.github.com/#user-site), GitHub [membutuhkan](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages#types-of-github-pages-sites) nama repositori yang sesuai format berikut: `{username}.github.io` (contohnya `gitname.github.io`)
        
        > Nama yang sudah kalian masukkan tadi akan muncul di beberapa tempat: (a) di dalam referensi repositori melalui Github, (b) tautan repositori, dan (c) in tautan tempat aplikasi React diluncurkan.

        > Dalam tutorial ini, aku akan pilih sebagai situs proyek.

        Aku akan namai: `react-gh-pages`
        
   - **Privasi repositori:** Pilih _Publik_ (atau _Privat_\*).

        > \* Untuk pengguna [GitHub versi gratis](https://docs.github.com/en/get-started/learning-about-github/githubs-products#github-free-for-user-accounts), hanya bisa memilih _Publik_ untuk menjalankan Github Pages. Sedangkan pengguna [GitHub Pro](https://docs.github.com/en/get-started/learning-about-github/githubs-products#github-pro) (dan pengguna berbayar lainnya), baik repositori _Publik_ maupun _Privat_ bisa digunakan untuk GitHub Pages.

        Karena kita pengguna gratisan, maka kita pilih: _Publik_

   - **Inisiasi repositori:** Biarkan semua kotak centang kosong.

        > Karena itu akan membuat repositori menjadi kosong, daripada mengisinya dengan file `README.md`, `.gitignore`, dan/atau `LICENSE`.
4. Setelah dirasa tidak ada yang terlewat, klik Submit.

Sampai di sini, kita sudah membuat repositori kosong, yang akan diisi dengan aplikasi React milik kita.

### 2. Buat Aplikasi React

1. Buat aplikasi react dengan nama `my-app`:

    > Jika kalian mau nama yang lain (seperti `react-cantiks`, dsb.), kalian bisa menggantinya dengan nama yang lain (contohnya `my-app` --> `react-cantiks`).
  
    ```shell
    $ npx create-react-app my-app
    ```

    > Perintah ini akan membuat proyek baru dengan bahasa program Javascript. Yang mau pakai [TypeScript](https://create-react-app.dev/docs/adding-typescript/#installation), kalian bisa gunakan perintah ini:
    > ```shell
    > $ npx create-react-app my-app --template typescript
    > ```

    Kedua perintah di atas (pilih salah satu) akan membuat sebuah folder bernama `my-app` (atau sesuai nama yang kalian mau tadi,) yang isinya adalah aplikasi React beserta alat-alat esensial lainnya.
   
    > Sebagai info tambahan, folder itu juga adalah repositori Git. Akan dijelaskan lebih lanjut pada Langkah 6

    > #### Nama Branch: `master` vs. `main`
    > 
    > Repositori Git akan mempunyai satu _branch_, namanya (a) `master`, nama asal dari pemasangan Git yang segar; atau (b) nilai dari pengkonfigurasi Git, `init.defaultBranch`, jika perangkat kalian menjalankan Git 2.28 atau lebih baru _dan_ kalian sudah [menetapkan variabel itu](https://github.blog/2020-07-27-highlights-from-git-2-28/#introducing-init-defaultbranch) dalam konfigurasi Git (misalnya lewat perintah `$ git config --global init.defaultBranch main`).
    >
    > Karena aku tidak menetapkan nilainya, _branch_ yang ada di repositoriku dinamakan `master`. Jika saja nama _branch_ kalian berbeda (bisa dicek dengan  `$ git branch`), seperti `main`; kalian bisa **ganti** nama _branch_ yang ada di keseluruhan tutorial dengan nama lain (contohnya `master` → `main`).

3. Masuk ke folder proyek yang telah kita buat:
  
    ```shell
    $ cd my-app
    ```

Sampai di sini, kita sudah masuk di dalam folder proyek React beserta sumber kode di dalamnya. Sisa perintah yang ada di bawah ini dapat dijalankan dalam folder tersebut.

### 3. Pasang paket npm `gh-pages`

1. Pasang paket npm [`gh-pages`](https://github.com/tschaub/gh-pages) dan pilih sebagai [development dependency](https://docs.npmjs.com/specifying-dependencies-and-devdependencies-in-a-package-json-file):
 
    ```shell
    $ npm install gh-pages --save-dev
    ```

Sampai di sini, `gh-pages` sudah terpasang di perangkat kita dan aplikasi React kita sudah terhubung di dalam file `package.json`.

### 4. Tambah properti `homepage` ke dalam file `package.json`

1. Edit file `package.json` menggunakan teks editor.
   
    ```shell
    $ vi package.json
    ```

    > Dalam tutorial ini, aku menggunakan [vi](https://www.vim.org/). Kalau gak tau, kalian bisa gunakan aplikasi teks editor yang lain, misalnya [Visual Studio Code](https://code.visualstudio.com/).
    > Atau, untuk pengguna Android, bisa menggunakan teks editor bawaan Termux dengan perintah `$ nano package.json`.

2. Tambah properti `homepage` dalam format ini\*: `https://{username}.github.io/{nama-repo}`

    > \* Untuk [situs proyek](https://pages.github.com/#project-site), itu tadi formatnya. Sedangkan untuk [situs pengguna](https://pages.github.com/#user-site), formatnya: `https://{username}.github.io`. Kalian bisa baca lebih jelasnya properti `homepage` ini di [halaman "GitHub Pages"](https://create-react-app.dev/docs/deployment/#github-pages) tentang peluncuran situs halaman.

    ```diff
    {
      "name": "my-app",
      "version": "0.1.0",
    + "homepage": "https://gitname.github.io/react-gh-pages",
      "private": true,
    ```
Sampai saat ini, file `package.json` aplikasi React ini telah ditambahkan properti `homepage`.

### 5. Tambahkan skrip peluncuran ke dalam file `package.json`

1. Buka lagi file `package.json` (kalau misalnya sudah disimpan, tapi mau diedit lagi).
   
    ```shell
    $ vi package.json
    ```

2. Tambahkan properti `predeploy` serta `deploy` ke dalam obyek `scripts`:

    ```diff
    "scripts": {
    +   "predeploy": "npm run build",
    +   "deploy": "gh-pages -d build",
        "start": "react-scripts start",
        "build": "react-scripts build",
    ```

Sampai di sini, aplikasi React sudah bisa diluncurkan.

### 6. Tambahkan "remote" yang mengarah pada repositori Github

1. Khusus yang baru memasang Git, inisiasi terlebih dulu Git ke dalam folder aplikasi React kalian dengan perintah ini:
   ```shell
   $ cd my-app
   $ git init
   $ git add .
   $ git config --global user.name {nama-akun-github}
   ```

   Ini untuk mencegah error pada saat menggunakan perintah selanjutnya.

2. Tambahkan "[remote](https://git-scm.com/docs/git-remote)" ke dalam repositori Git lokal: 
    
    ```shell
    $ git remote add origin https://github.com/{username}/{nama-repo}.git
    ```

    Sebagai contoh, kutulis seperti ini:

    ```shell
    $ git remote add origin https://github.com/gitname/react-gh-pages.git
    ```

    > Perintah ini mengotomatisasi perintah `$ git push` ke dalam repositori Github yang sudah kita buat sebelumnya pada Langkah 1.

### 7. Dorong Aplikasi React ke Repositori Github

1. Dorong Aplikasi React milik kita menggunakan perintah ini:

    ```shell
    $ npm run deploy
    ```

    > Yang akan menyebabkan skrip `predeploy` dan `deploy` yang sudah ditulis di file `package.json` dijalankan.
    >
    > Skrip `predeploy` akan membuat aplikasi React versi distribusi dan disetor ke dalam forder bernama `build`. Lalu, skrip `deploy` akan mendorong konten dalam folder tersebut dalam sebuah _commit_ baru _branch_`gh-pages` repositori Github, kalau belum ada.

    > Secara default, _commit_ baru di _branch_ `gh-pages` akan ada pesan _commit_ yakni "Updates". Kalian bisa [menentukan pesan sendiri](https://github.com/gitname/react-gh-pages/issues/80#issuecomment-1042449820) lewat opsi `-m`, seperti ini:
    > ```shell
    > $ npm run deploy -- -m "Luncurkan aplikasi React ke Github"
    > ```

Sampai di sini, repositori Github berisi _branch_ bernama `gh-pages`, di mana isinya adalah file aplikasi React versi distribusi. Bagaimanapun, kita belum mengatur Github Pages untuk _menjalankan_ file tersebut.

### 8. Atur GitHub Pages

1. Cari menu pengaturan **GitHub Pages** 
   1. Di browser kalian, masuk ke repositori Github kalian.
   1. Di atas browser kode, klik pada tab yang berlabel "Settings".
   1. Di menu samping, tepatnya bagian "Code and automation", klik "Pages".
1. Atur pengaturan "Build and deployment" seperti ini: 
   1. **Source**: Deploy from a branch
   2. **Branch**: 
      - Branch: `gh-pages`
      - Folder: `/ (root)`
1. Klik tombol "Save".

**Itu dia!** Aplikasi React kita sekarang sudah meluncur! :rocket:

Sampai di sini, kalian sudah bisa membagikan URL aplikasi React ke teman-teman (ada di Langkah 4.) Sebagai contoh, URL milikku adalah https://gitname.github.io/react-gh-pages.

### 9. (Yang ini boleh di-skip) Setor _kode sumber_ aplikasi React ke GitHub

1. _Commit_ perubahan ketika kalian mengikuti tutorial ini ke _branch_ repositori Git lokal `master`; setelah itu, dorong ke _branch_ repositori Github `master` milik kalian.

    ```shell
    $ git add .
    $ git commit -m "Penambahan kode sumber aplikasi React"
    $ git push origin master
    ```

    > Di titik ini, aku menyarankan untuk menjelajahi repositori. Akan ada dua _branche_: `master` dan `gh-pages`. _Branch_ `master` berisi kode sumber aplikasi React, sedangkan _branch_ `gh-pages` berisi aplikasi React versi distribusi.

# Referensi

1. [Panduan peluncuran resmi `create-react-app`](https://create-react-app.dev/docs/deployment/#github-pages)
2. [GitHub blog: Bangun dan luncurkan Github Pages dari _branch_ apa saja](https://github.blog/changelog/2020-09-03-build-and-deploy-github-pages-from-any-branch/)
3. [Menyediakan file `CNAME` ketika menggunakan domain kustom](https://github.com/gitname/react-gh-pages/issues/89#issuecomment-1207271670)

# Catatan

- Terima kasih yang sebesar-besarnya kepada Github yang telah menyediakan hosting gratis untuk developer pemula.
- Dan saatnya, untuk mengembangkan aplikasi React menjadi suatu yang unik.
- Repositori ini memiliki dua _branch_:
    - `master` - _kode sumber_ aplikasi React.
    - `gh-pages` - aplikasi React yang _dibuat dari_ kode sumber tersebut.

 # Kontributor

Terimakasih buat kalian yang telah membantu dalam proses pengembangan tutorial ini.

<!--

Template:
---------

<a href="https://github.com/____" target="_blank" title="____">
  <img src="https://github.com/____.png?size=40" height="40" width="40" alt="____" />
</a>

Instructions:
-------------

1. Copy the template and paste it below.
2. Replace the four "____" strings with the contributor's GitHub username.

Note: I specified the avatars using HTML because, when I did so using Markdown,
      only the _custom_ avatars appeared at the size I specified via the URL
      (e.g. 40px squared, for `https://github.com/gitname.png?size=40`);
      the GitHub-generated avatars seemed to ignore the size parameter and,
      instead, appear at their full size (approximately 420px squared).
      By using HTML, I can force _both_ types to appear at 40px squared.

-->

<a href="https://github.com/gitname" target="_blank" title="gitname">
  <img src="https://github.com/gitname.png?size=40" height="40" width="40" alt="gitname" />
</a>
<a href="https://github.com/rhulse" target="_blank" title="rhulse">
  <img src="https://github.com/rhulse.png?size=40" height="40" width="40" alt="rhulse" />
</a>
<a href="https://github.com/AbhishekCode" target="_blank" title="AbhishekCode">
  <img src="https://github.com/AbhishekCode.png?size=40" height="40" width="40" alt="AbhishekCode" />
</a>
<a href="https://github.com/adnjoo" target="_blank" title="adnjoo">
  <img src="https://github.com/adnjoo.png?size=40" height="40" width="40" alt="adnjoo" />
</a>
<a href="https://github.com/thebeatlesphan" target="_blank" title="thebeatlesphan">
  <img src="https://github.com/thebeatlesphan.png?size=40" height="40" width="40" alt="thebeatlesphan" />
</a>
<a href="https://github.com/valerio-pescatori" target="_blank" title="valerio-pescatori">
  <img src="https://github.com/valerio-pescatori.png?size=40" height="40" width="40" alt="valerio-pescatori" />
</a>
<a href="https://github.com/jackweyhrich" target="_blank" title="jackweyhrich">
  <img src="https://github.com/jackweyhrich.png?size=40" height="40" width="40" alt="jackweyhrich" />
</a>
<a href="https://github.com/nymugit" target="_blank" title="Aku2Nama">
  <img src="https://github.com/nymugit.png?size=40" height="40" width="40" alt="nymugit" />
</a>

This list is maintained manually—for now—and includes (a) each person who submitted a pull request that was eventually merged into `master`, and (b) each person who contributed in a different way (e.g. providing constructive feedback) and who approved of me including them in this list.
