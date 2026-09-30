# Serenity Yoga Company Profile

Landing page statis Serenity Yoga berbasis Astro, Vue islands, TypeScript, Tailwind CSS, dan Motion.

## Prasyarat

- Node.js 22.12 atau lebih baru

## Menjalankan project

```sh
npm install
npm run dev
```

Build production:

```sh
npm run build
```

## Arsitektur

Project mengikuti Feature-Sliced Design yang disesuaikan untuk Astro:

- `src/app`: layout dan style global.
- `src/pages`: file-based routes Astro.
- `src/widgets`: section besar halaman.
- `src/features`: aksi pengguna dan Vue islands.
- `src/entities`: model bisnis lintas fitur bila dibutuhkan.
- `src/shared`: UI primitive, assets, dan utilitas generik.

Panduan lengkap tersedia di `docs/fsd.md`.
