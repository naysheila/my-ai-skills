# personal AI Infrastructure & Learning Skills

Selamat datang di repositori infrastruktur AI personal milik **Naysheila Firyal Ramdani**. 

Repositori ini berfungsi sebagai pusat kendali untuk mengelola **Agent Skills**, konfigurasi **Model Context Protocol (MCP)**, dan panduan alur kerja (*workflow*) pembelajaran berbasis AI yang adaptif, terstruktur, serta terhubung langsung dengan catatan pribadi di **Notion**.

---

## Daftar Isi
1. [Overview Agent Skills](#-daftar-agent-skills)
2. [Panduan Persiapan Awal (Zero-to-Hero Setup)](#-panduan-persiapan-awal-zero-to-hero-setup)
   - [Langkah 1: Menghubungkan Notion MCP](#langkah-1-menghubungkan-notion-mcp-server)
   - [Langkah 2: Menyiapkan Database di Notion](#langkah-2-menyiapkan-database-di-notion)
   - [Langkah 3: Memuat (Loading) Skill ke AI](#langkah-3-memuat-loading-skill-ke-ai)
3. [Panduan Penggunaan Pertama Kali (First-Run Session)](#-panduan-penggunaan-pertama-kali-first-run-session)
4. [Panduan Penggunaan Sehari-hari (Daily Workflow)](#-panduan-penggunaan-sehari-hari-daily-workflow)
5. [Troubleshooting & Troubleshooting Tips](#-troubleshooting)

---

## Daftar Agent Skills

| Nama Skill | Versi | Target Konteks | Deskripsi Ringkas |
| :--- | :--- | :--- | :--- |
| `learning-assistant-sms-3` | v1.2.0 | Mahasiswa SI / IT Sem 3 | Asisten belajar Sokratik, evaluasi kognitif adaptif, & auto-sync Notion MCP. |

---

## Panduan Persiapan Awal (Zero-to-Hero Setup)

Ikuti alur ini dari awal jika kamu baru pertama kali memasang sistem ini di perangkat baru atau antarmuka AI baru (misalnya Claude Desktop atau Cursor).

### Langkah 1: Menghubungkan Notion MCP Server

Agar AI dapat membaca dan menulis catatan ke Notion milikmu secara otomatis, kamu perlu mengintegrasikan **Notion MCP Server**.

1. **Buat Integration Key di Notion:**
   - Buka [Notion Integrations Page](https://www.notion.so/my-integrations).
   - Klik **"+ New integration"**.
   - Beri nama (misal: `AI Learning Assistant`), pilih Workspace milikmu, lalu simpan.
   - Salin **Internal Integration Secret / API Key** yang diberikan (simpan secara aman).

2. **Berikan Akses pada Folder/Database Notion:**
   - Buka folder atau database Mata Kuliah Semester 3 di aplikasi Notion milikmu.
   - Klik titik tiga `...` di pojok kanan atas halaman $\rightarrow$ pilih **Connections / Sambungan**.
   - Cari nama integrasi yang baru kamu buat (`AI Learning Assistant`), lalu beri akses **Allow / Hubungkan**.

3. **Pasang Konfigurasi MCP di Aplikasi AI (misal: Claude Desktop):**
   - Buka file konfigurasi Claude Desktop kamu:
     - **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`
     - **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
   - Masukkan konfigurasi JSON berikut (ganti `PASTE_YOUR_NOTION_API_KEY_HERE` dengan API Key dari Langkah 1.1):

```json
{
  "mcpServers": {
    "notion": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-notion"
      ],
      "env": {
        "NOTION_API_KEY": "PASTE_YOUR_NOTION_API_KEY_HERE"
      }
    }
  }
}
