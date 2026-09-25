# AI Team Playbook — ist-automation

Folder ini adalah paket siap-copy untuk membantu developer/QA memakai AI saat mengubah project ini.

## Cara pakai

1. Copy `AGENTS.md` ke root repository bila coding agent yang dipakai mendukung instruksi repository.
2. Sebelum meminta AI mengubah kode, berikan `01-PROJECT-CONTEXT.md` dan `02-AI-SAFETY-RULES.md` sebagai konteks.
3. Ambil template yang sesuai dari `03-PROMPT-TEMPLATES.md`, isi bagian di dalam `[kurung siku]`, lalu kirim ke AI.
4. Sebelum merge, pakai `04-CHANGE-CHECKLIST.md` untuk review hasilnya.

Dokumen ini sengaja tidak menyertakan nilai profile, kredensial, nomor nasabah, atau data test. Jangan pernah memasukkan nilai rahasia dari `Profiles/`, `pool.json`, laporan, atau log ke prompt AI publik.

## Isi paket

| File | Fungsi |
|---|---|
| `AGENTS.md` | Instruksi operasional untuk coding agent di repository ini. |
| `01-PROJECT-CONTEXT.md` | Peta arsitektur dan konvensi project. |
| `02-AI-SAFETY-RULES.md` | Batas aman agar perubahan AI tidak melebar atau merusak suite. |
| `03-PROMPT-TEMPLATES.md` | Prompt siap pakai untuk analisis, perbaikan, feature, dan review. |
| `04-CHANGE-CHECKLIST.md` | Checklist manusia sebelum menjalankan/merge perubahan. |

## Prinsip utama

AI boleh membantu membaca, menjelaskan, mengusulkan, dan mengedit dalam scope kecil. AI tidak boleh menebak locator, test data, credential, tag, atau dampak perubahan. Jika bukti tidak cukup, AI harus berhenti dan melaporkan yang dibutuhkan.
