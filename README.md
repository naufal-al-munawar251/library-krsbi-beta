# library-krsbi-beta

<h3>Full API list</h3>
https://os.mbed.com/docs/mbed-os/v6.15/apis/index.html Ini adalah daftar lengkap API yang ditawarkan oleh penulis aplikasi Mbed OS (tidak termasuk API internal, yang tidak dimaksudkan untuk digunakan oleh kode aplikasi). Daftar tersebut menunjukkan API mana yang didukung oleh profil bare metal, dan yang mana yang diaktifkan secara manual (berlawanan dengan yang diaktifkan secara default). Untuk konsistensi, kami juga menampilkan dukungan API profil lengkap, meskipun itu - dan diharapkan tetap - semua API.

Untuk daftar API yang dihapus di Mbed OS 6, lihat daftar API yang tidak digunakan lagi di bagian bawah halaman ini.

<h3>Scheduling</h3>

The Mbed OS scheduling capabilities include managing objects such as threads, synchronization objects and timers. It also provides interfaces for attaching an application-specific idle hook function, reads the OS tick count and implements functionality to report RTOS errors.


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
</table>

<h2>Referensi PwmOut</h2>
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
