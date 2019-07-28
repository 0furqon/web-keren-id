---
title: Instalasi nodejs di Ubuntu 18.04
date: 2019-01-07
published: true
tags: ['nodejs', 'pemula', 'javascript']
series: false
cover_image: ./images/alexandr-podvalny-220262-unsplash.jpg
canonical_url: false
description: "Nodejs merupakan runtime javascript yang dibuat dengan tujuan memudahkan pengembang dalam membuat aplikasi yang *scalable*. Jika sebelumnya javascript hanya digunakan sebagai media interaktif di dalam sebuah tampilan antar muka halaman web, nodejs memungkinkan pengembang untuk membuat aplikasi yang dapat berjalan di Operating System (OS) sebagai aplikasi mandiri.."
---

Nodejs merupakan runtime javascript yang dibuat dengan tujuan memudahkan pengembang dalam membuat aplikasi yang *scalable*. Jika sebelumnya javascript hanya digunakan sebagai media interaktif di dalam sebuah tampilan antar muka halaman web, nodejs memungkinkan pengembang untuk membuat aplikasi yang dapat berjalan di Operating System (OS) sebagai aplikasi mandiri.

## Prasyarat

Artikel ini mengasumsikan bahwa penulis menggunakan OS Ubuntu 18.04, namun seharusnya dapat diaplikasikan dengan berbagai macam distribusi linux lainnya. Sebelum memulai, pastikan user yang digunakan merupakan user non-root yang memiliki *sudo privileges*,

## Apa Itu NVM?

Node Version Manager (NVM) merupakan sebuah *tools* yang dapat digunakan untuk mengelola banyak installasi nodejs di dalam satu machine yang membantu kita dalam melakukan installasi dan pembaruan berbagai versi nodejs. Kita dapat dengan mudah melakukan pergantian versi nodejs ditengah siklus pengembangan. NVM juga mempermudah update version sehingga kita tak perlu susah susah 

Beberapa kemudahan yang didapat dengan menggunakan NVM antara lain:
- Akses setiap versi Node.js dari satu mesin, baik versi *latest* maupun *Long Term Support (LTS)*
- Fitur *alias* yang memudahkan pengembang untuk menggunakan versi nodejs sesuai kebutuhan
- Selamat tinggal proses update versi nodejs yang ribet dan rentan membuat *error* 
- File konfigurasi .nvmrc untuk pengembang yang nyaman dengan penggunaan dotfiles
- Dapat digunakan di banyak *shell* favorit : Sh, Bash, Zsh, Dash, Ksh

## *Setup* NVM

Selama pengembang nyaman dengan penggunaan *Command Line Interface (CLI)* maka proses setup NVM merupakan hal yang mudah. Artikel ini akan membahas proses installasi menggunakan OS Ubuntu 18.04.2 dan shell Bash, namun pengguna *distro* dan shell lainnya dapat mengikuti langkah-langkahnya dengan menyesuaikan beberapa pengaturan saja.

### Langkah #1: Installasi NVM

Untuk melakukan instalasi dan pembaruan kamu dapat mengunduh *script* instalasi dan menjalankan. Saat artikel ini dibuat versi terbaru adalah v0.34.0. Versi terbaru dari *script* ini bisa didapatkan dari [dokumentasi](https://github.com/nvm-sh/nvm#install--update-script).

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
```

atau menggunakan Wget jika Curl tidak tersedia:

```
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
```

Setelah proses instalasi berhasil, pastikan environment NVM_DIR sudah ter-*export* di dalam file konfigurasi *shell*. Untuk pengguna bash, dapat mengakses file `~/.bash_profile`, `~/.profile`, atau `~/.bashrc`, kemudian mengecek apakah sudah ada penambahan seperti berikut

```sh
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

Jika belum ada maka kamu harus menambahkan baris di atas ke dalam baris akhir file konfigurasi, setelah itu jalankan perintah `source` untuk menerapkan perubahan konfigurasi *shell*.

Contohnya kamu melakukan perubahan di file `~/.bashrc` maka perintah yang dijalankan

```sh
source ~/.bashrc
```

Terakhir cek apakah NVM sudah terinstall dengan benar dengan menjalankan perintah

```sh
command -v nvm
```

Jika *output* yang dikeluarkan berupa `nvm`, selamat kamu sudah berhasil melakukan proses instalasi. Jika belum maka cek sekali lagi konfigurasi *shell* masing-masing


### Langkah #2: Instalasi nodejs dan npm

Pertama unduh nodejs dengan menggunakan perintah `install`. Misalkan kita ingin menggunakan nodejs versi LTS terbaru maka perintah yang digunakan adalah

```
nvm install --lts --latest-npm
```

Dengan nvm kita bisa melakukan installasi berbgai macam versi nodejs sesuai dengan kebutuhan development. Misalkan kamu ingin menggunakan nodejs versi 11.15.0 maka dapat menjalankan perintah

```
nvm install v11.15.0
```

Untuk memilih versi nodejs yang aktif dapat menjalankan perintah `nvm use <versi-yang-ingin-digunakan>` contohnya seperti ini

```
nvm use v11.15.0
```

Terakhir cek apakah nodejs versi tadi sudah berhasil dipilih dengan menggunakan perintah

```
node -v
```

Jika menghasilkan output `v11.15.0`, selamat kamu berhasil melakukan instalasi nodejs menggunakan nvm.

#### Berbagai Sumber

- https://github.com/nvm-sh/nvm/blob/master/README.md
- https://itnext.io/nvm-the-easiest-way-to-switch-node-js-environments-on-your-machine-in-a-flash-17babb7d5f1b
