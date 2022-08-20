# library-krsbi-beta ( Mbed )

Jika anda membututhkan sofwarenya silahkan download https://studio.mbed.com/installers/latest/win/MbedStudio.exe

<h3>Full API list</h3>
https://os.mbed.com/docs/mbed-os/v6.15/apis/index.html Ini adalah daftar lengkap API yang ditawarkan oleh penulis aplikasi Mbed OS (tidak termasuk API internal, yang tidak dimaksudkan untuk digunakan oleh kode aplikasi). Daftar tersebut menunjukkan API mana yang didukung oleh profil bare metal, dan yang mana yang diaktifkan secara manual (berlawanan dengan yang diaktifkan secara default). Untuk konsistensi, kami juga menampilkan dukungan API profil lengkap, meskipun itu - dan diharapkan tetap - semua API.

Untuk daftar API yang dihapus di Mbed OS 6, lihat daftar API yang tidak digunakan lagi di bagian bawah halaman ini.

<h3>Scheduling</h3>

Kemampuan penjadwalan Mbed OS mencakup pengelolaan objek seperti utas, objek sinkronisasi, dan pengatur waktu. Ini juga menyediakan antarmuka untuk melampirkan fungsi pengait idle khusus aplikasi, membaca jumlah tick OS dan mengimplementasikan fungsionalitas untuk melaporkan kesalahan RTOS.


<h3>RTOS</h3>
<table border="1px">
  <tr>
    <th><h3>API</h3></th>
    <th><h3>Full profile</h3></th>
    <th><h3>Bare metal profile</h3></th>
  </tr>
  <tr>
    <td>ConditionVariable</td>
    <td>✔</td>
    <td></td>
  </tr>
  <tr>
    <td>EventFlags</td>
    <td>✔</td>
    <td>✔</td>
  </tr>
  <tr>
    <td>Idle loop</td>
    <td>✔</td>
    <td></td>
  </tr>
  <tr>
    <td>Kernel interface functions</td>
    <td>✔</td>
    <td>get_ms_count only</td>
  </tr>
  <tr>
    <td>Mail</td>
    <td>✔</td>
    <td></td>
  </tr>
  <tr>
    <td>Mutex</td>
    <td>✔</td>
    <td>✔</td>
  </tr>
  <tr>
    <td>Queue</td>
    <td>✔</td>
    <td></td>
  </tr>
  <tr>
    <td>Semaphore</td>
    <td>✔</td>
    <td>✔</td>
  </tr>
  <tr>
    <td>ThisThread</td>
    <td>✔</td>
    <td>✔</td>
  </tr>
  <tr>
    <td>Thread</td>
    <td>✔</td>
    <td></td>
  </tr>
</table>

<h2>Referensi PwmOut ( Native )</h2>
<h3>PwmOut hello, world</h3>
Contoh kode ini menggunakan periode default 0,020 detik dan meningkatkan siklus tugas dari 0% menjadi 100% dengan peningkatan 10%.


```
/*
 * Copyright (c) 2014-2020 Arm Limited and affiliates.
 * SPDX-License-Identifier: Apache-2.0
 */

#include "mbed.h"

// Adjust pin name to your board specification.
// You can use LED1/LED2/LED3/LED4 if any is connected to PWM capable pin,
// or use any PWM capable pin, and see generated signal on logical analyzer.
PwmOut led(LED1);

int main()
{
    // specify period first
    led.period(4.0f);      // 4 second period
    led.write(0.50f);      // 50% duty cycle, relative to period
    //led = 0.5f;          // shorthand for led.write()
    //led.pulsewidth(2);   // alternative to led.write, set duty cycle time in seconds
    while (1);
}
```

<h2>PwmOut code examples</h2>
<h3>Example one</h3>

Contoh kode ini menetapkan periode dalam detik dan siklus tugas sebagai persentase periode dalam floating point (kisaran: 0 hingga 1). Efek dari cuplikan kode ini adalah mengedipkan LED2 selama siklus empat detik, 50% aktif, untuk pola dua detik aktif, dua detik mati.


```
/*
 * Copyright (c) 2017-2020 Arm Limited and affiliates.
 * SPDX-License-Identifier: Apache-2.0
 */

#include "mbed.h"

// Adjust pin name to your board specification.
// You can use LED1/LED2/LED3/LED4 if any is connected to PWM capable pin,
// or use any PWM capable pin, and see generated signal on logical analyzer.
PwmOut led(LED2);

int main()
{
    // specify period first, then everything else
    led.period(4.0f);  // 4 second period
    led.write(0.50f);  // 50% duty cycle
    while (1);         // led flashing
}

```

<h3>Example two</h3>

Contoh berikut melakukan hal yang sama, tetapi alih-alih menentukan siklus tugas sebagai persentase relatif dari periode, ini menetapkannya sebagai nilai absolut dalam hitungan detik. Dalam hal ini kami memiliki periode empat detik dan siklus tugas dua detik, artinya LED akan menyala selama dua detik dan mati selama dua detik.


```

/*
 * Copyright (c) 2017-2020 Arm Limited and affiliates.
 * SPDX-License-Identifier: Apache-2.0
 */

#include "mbed.h"

// Adjust pin name to your board specification.
// You can use LED1/LED2/LED3/LED4 if any is connected to PWM capable pin,
// or use any PWM capable pin, and see generated signal on logical analyzer.
PwmOut led(LED2);

int main()
{
    // specify period first, then everything else
    led.period(4.0f);  // 4 second period
    led.pulsewidth(2); // 2 second pulse (on)
    while (1);         // led flashing
}

```

<h3>Membuat jeda</h3>

Jika anda ingin menjeda dalam memproses program Roda Motor DC silahkan tulis codingan bawah ini.

```
// 1000 itu adalah sebuah waktu lama dalam menjeda
ThisThread::sleep_for(1000);
```
