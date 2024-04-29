# Meluncurkan sebuah Aplikasi React* ke GitHub Pages (Halaman Github)

\* dibuat menggunakan `create-react-app`

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
   - Tingkatkan paket Termux ke versi baru
     ```shell
     $ pkg upgrade && pkg upgrade
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

    > Seandainya kalian mau nama yang lain (seperti `react-cantiks`, dsb.), kalian bisa menggantinya dengan nama yang lain (contohnya `my-app` --> `react-cantiks`).
  
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
    > Repositori Git akan mempunyai satu branch, namanya (a) `master`, nama asal dari pemasangan Git yang segar; atau (b) nilai dari pengkonfigurasi Git, `init.defaultBranch`, jika perangkat kalian menjalankan Git 2.28 atau lebih baru _dan_ kalian sudah [menetapkan variabel itu](https://github.blog/2020-07-27-highlights-from-git-2-28/#introducing-init-defaultbranch) dalam konfigurasi Git (misalnya lewat perintah `$ git config --global init.defaultBranch main`).
    >
    > Karena aku tidak menetapkan nilainya, branch yang ada di repositoriku dinamakan `master`. Jika saja nama branch kalian berbeda (bisa dicek dengan  `$ git branch`), sepreti `main`; kalian bisa **ganti** nama branch yang ada di keseluruhan tutorial dengan nama lain (contohnya `master` → `main`).

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

1. Open the `package.json` file in a text editor.
   
    ```shell
    $ vi package.json
    ```

    > In this tutorial, the text editor I'll be using is [vi](https://www.vim.org/). You can use any text editor you want; for example, [Visual Studio Code](https://code.visualstudio.com/).

2. Add a `homepage` property in this format\*: `https://{username}.github.io/{repo-name}`

    > \* For a [project site](https://pages.github.com/#project-site), that's the format. For a [user site](https://pages.github.com/#user-site), the format is: `https://{username}.github.io`. You can read more about the `homepage` property in the ["GitHub Pages" section](https://create-react-app.dev/docs/deployment/#github-pages) of the `create-react-app` documentation.

    ```diff
    {
      "name": "my-app",
      "version": "0.1.0",
    + "homepage": "https://gitname.github.io/react-gh-pages",
      "private": true,
    ```
At this point, the React app's `package.json` file includes a property named `homepage`.

### 5. Add deployment scripts to the `package.json` file

1. Open the `package.json` file in a text editor (if it isn't already open in one).
   
    ```shell
    $ vi package.json
    ```

2. Add a `predeploy` property and a `deploy` property to the `scripts` object:

    ```diff
    "scripts": {
    +   "predeploy": "npm run build",
    +   "deploy": "gh-pages -d build",
        "start": "react-scripts start",
        "build": "react-scripts build",
    ```

At this point, the  React app's `package.json` file includes deployment scripts.

### 6. Add a "remote" that points to the GitHub repository

1. Add a "[remote](https://git-scm.com/docs/git-remote)" to the local Git repository.

    You can do that by issuing a command in this format: 
    
    ```shell
    $ git remote add origin https://github.com/{username}/{repo-name}.git
    ```
    
    To customize that command for your situation, replace `{username}` with your GitHub username and replace `{repo-name}` with the name of the GitHub repository you created in Step 1.

    In my case, I'll run:

    ```shell
    $ git remote add origin https://github.com/gitname/react-gh-pages.git
    ```

    > That command tells Git where I want it to push things whenever I—or the `gh-pages` npm package acting on my behalf—issue the `$ git push` command from within this local Git repository.

At this point, the local repository has a "remote" whose URL points to the GitHub repository you created in Step 1.

### 7. Push the React app to the GitHub repository

1. Push the React app to the GitHub repository

    ```shell
    $ npm run deploy
    ```

    > That will cause the `predeploy` and `deploy` scripts defined in `package.json` to run.
    >
    > Under the hood, the `predeploy` script will build a distributable version of the React app and store it in a folder named `build`. Then, the `deploy` script will push the contents of that folder to a new commit on the `gh-pages` branch of the GitHub repository, creating that branch if it doesn't already exist.

    > By default, the new commit on the `gh-pages` branch will have a commit message of "Updates". You can [specify a custom commit message](https://github.com/gitname/react-gh-pages/issues/80#issuecomment-1042449820) via the `-m` option, like this:
    > ```shell
    > $ npm run deploy -- -m "Deploy React app to GitHub Pages"
    > ```

At this point, the GitHub repository contains a branch named `gh-pages`, which contains the files that make up the distributable version of the React app. However, we haven't configured GitHub Pages to _serve_ those files yet.

### 8. Configure GitHub Pages

1. Navigate to the **GitHub Pages** settings page
   1. In your web browser, navigate to the GitHub repository
   1. Above the code browser, click on the tab labeled "Settings"
   1. In the sidebar, in the "Code and automation" section, click on "Pages"
1. Configure the "Build and deployment" settings like this: 
   1. **Source**: Deploy from a branch
   2. **Branch**: 
      - Branch: `gh-pages`
      - Folder: `/ (root)`
1. Click on the "Save" button

**That's it!** The React app has been deployed to GitHub Pages! :rocket:

At this point, the React app is accessible to anyone who visits the `homepage` URL you specified in Step 4. For example, the React app I deployed is accessible at https://gitname.github.io/react-gh-pages.

### 9. (Optional) Store the React app's _source code_ on GitHub

In a previous step, the `gh-pages` npm package pushed the distributable version of the React app to a branch named `gh-pages` in the GitHub repository. However, the _source code_ of the React app is not yet stored on GitHub.

In this step, I'll show you how you can store the source code of the React app on GitHub.

1. Commit the changes you made while you were following this tutorial, to the `master` branch of the local Git repository; then, push that branch up to the `master` branch of the GitHub repository.

    ```shell
    $ git add .
    $ git commit -m "Configure React app for deployment to GitHub Pages"
    $ git push origin master
    ```

    > I recommend exploring the GitHub repository at this point. It will have two branches: `master` and `gh-pages`. The `master` branch will contain the React app's source code, while the `gh-pages` branch will contain the distributable version of the React app.

# References

1. [The official `create-react-app` deployment guide](https://create-react-app.dev/docs/deployment/#github-pages)
2. [GitHub blog: Build and deploy GitHub Pages from any branch](https://github.blog/changelog/2020-09-03-build-and-deploy-github-pages-from-any-branch/)
3. [Preserving the `CNAME` file when using a custom domain](https://github.com/gitname/react-gh-pages/issues/89#issuecomment-1207271670)

# Notes

- Special thanks to GitHub (the company) for providing us with the GitHub Pages hosting service for free.
- And now, time to turn the default React app generated by `create-react-app` into something unique!
- This repository consists of two branches: 
    - `master` - the _source code_ of the React app
    - `gh-pages` - the React app _built from_ that source code

 # Contributors

Thanks to these people for contributing to the maintenance of this tutorial.

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

This list is maintained manually—for now—and includes (a) each person who submitted a pull request that was eventually merged into `master`, and (b) each person who contributed in a different way (e.g. providing constructive feedback) and who approved of me including them in this list.
