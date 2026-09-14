# Plugin eksis untuk direktori Claude

## Summary

Repo baru. Connectors Directory terkunci di paket Claude Team (D-79), tetapi direktori kedua —
plugin directory yang dipakai Claude Code dan Cowork — menerima pengajuan lewat Console, dan
dokumentasinya menyebut jalur itu khusus untuk penulis yang bukan bagian organisasi Team. Console
gratis, dan sebuah plugin boleh memuat remote MCP apa adanya, jadi connector eksis (D-59) dibungkus
sebagai plugin tanpa satu baris pun kode server berubah.

## Changes

- `.claude-plugin/plugin.json`: manifest, MIT, homepage `/developers`
- `.mcp.json`: server remote `https://api.eksis.io/mcp` tanpa header
- `skills/publishing-with-eksis/SKILL.md`: aturan per platform, urutan memeriksa sebelum menyusun,
  dan pemisahan tegas antara menjadwalkan dan menerbitkan seketika
- `README.md`: kemampuan, cara pasang, dan bagian Privacy Policy
- `LICENSE`: MIT

## Decisions

- `.mcp.json` sengaja tanpa header: dengan begitu Claude menemui 401 dan menjalankan OAuth, yang
  berarti plugin ini bekerja di paket Free juga (D-77). Menaruh kunci API di sana akan mengunci
  plugin ke satu workspace dan membocorkan kunci ke repo publik
- Repo publik dan MIT karena aturan direktori menolak plugin bersumber tertutup. Isinya hanya
  manifest dan dokumentasi; tidak ada kode eksis di dalamnya
- Satu skill, bukan kumpulan command: yang paling sering salah adalah model menyusun post sebelum
  membaca aturan platformnya, dan itu satu skill yang menjawabnya

## Verification

- `claude plugin validate --strict`: lolos
- Endpoint yang dirujuk diuji hidup di produksi hari ini: `tools/list` menjawab 13 tool
- Diajukan 14 Sep 2026 lewat Console; dasbor pengiriman berbunyi "eksis - Dikirim dan menunggu tinjauan"

## Limitations

- Plugin directory menjangkau Claude Code dan Cowork, bukan chat claude.ai. Pengguna claude.ai tetap
  memasang eksis sebagai custom connector
- Plugin directory tidak menjangkau chat claude.ai; itu tetap milik Connectors Directory yang berbayar

## Follow-up

- Menunggu hasil tinjauan Anthropic; pembaruan repo terangkat otomatis setelah terbit, tanpa
  pengajuan ulang
- Identitas penerbit masih perorangan (organisasi Console berdiri di akun Google pemilik); pindahkan
  ke PT Eksis Karya Digital kalau verifikasi bisnisnya sudah beres
