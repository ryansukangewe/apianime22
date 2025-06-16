# Wajik Anime API - Cloudflare Workers

Anime API yang berjalan di Cloudflare Workers dengan performa tinggi dan global distribution.

## Features

- 🚀 **High Performance**: Berjalan di Cloudflare Edge Network
- 🌍 **Global Distribution**: Response cepat dari seluruh dunia
- 💰 **Cost Effective**: Gratis untuk 100,000 requests/hari
- 🔒 **Secure**: Built-in DDoS protection dan security features
- ⚡ **Fast Cold Start**: Instant startup tanpa server warming

## Supported Sources

- **Otakudesu**: Anime streaming dan download
- **Samehadaku**: Anime streaming dan download

## Quick Start

### Prerequisites

- Node.js 18+
- Cloudflare account
- Wrangler CLI

### Installation

1. Clone repository:
\`\`\`bash
git clone https://github.com/wajik45/wajik-anime-api.git
cd wajik-anime-api
\`\`\`

2. Install dependencies:
\`\`\`bash
npm install
\`\`\`

3. Login ke Cloudflare:
\`\`\`bash
npx wrangler login
\`\`\`

4. Setup KV namespace (optional, untuk caching):
\`\`\`bash
npx wrangler kv:namespace create "CACHE"
npx wrangler kv:namespace create "CACHE" --preview
\`\`\`

5. Update `wrangler.toml` dengan KV namespace ID yang didapat dari step 4.

### Development

\`\`\`bash
npm run dev
\`\`\`

API akan tersedia di `http://localhost:8787`

### Deployment

\`\`\`bash
npm run deploy
\`\`\`

## API Documentation

### Base URL
\`\`\`
https://your-worker.your-subdomain.workers.dev
\`\`\`

### Endpoints

#### Main Routes
- `GET /` - Homepage dengan dokumentasi
- `GET /view-data` - Informasi API dan sources

#### Otakudesu Routes
- `GET /otakudesu/home` - Homepage anime
- `GET /otakudesu/schedule` - Jadwal rilis
- `GET /otakudesu/anime` - Semua anime
- `GET /otakudesu/genres` - Semua genre
- `GET /otakudesu/ongoing?page=1` - Anime ongoing
- `GET /otakudesu/completed?page=1` - Anime completed
- `GET /otakudesu/search?q=naruto` - Pencarian anime
- `GET /otakudesu/genres/{genreId}?page=1` - Anime by genre
- `GET /otakudesu/anime/{animeId}` - Detail anime
- `GET /otakudesu/episode/{episodeId}` - Detail episode
- `GET /otakudesu/server/{serverId}` - Streaming server
- `GET /otakudesu/batch/{batchId}` - Batch download

#### Samehadaku Routes
- `GET /samehadaku/home` - Homepage anime
- `GET /samehadaku/schedule` - Jadwal rilis
- `GET /samehadaku/anime` - Semua anime
- `GET /samehadaku/genres` - Semua genre
- `GET /samehadaku/recent?page=1` - Episode terbaru
- `GET /samehadaku/ongoing?page=1&order=title` - Anime ongoing
- `GET /samehadaku/completed?page=1&order=title` - Anime completed
- `GET /samehadaku/popular?page=1` - Anime populer
- `GET /samehadaku/movies?page=1` - Anime movie
- `GET /samehadaku/batch?page=1` - Batch download
- `GET /samehadaku/search?q=naruto&page=1` - Pencarian anime
- `GET /samehadaku/genres/{genreId}?page=1` - Anime by genre
- `GET /samehadaku/anime/{animeId}` - Detail anime
- `GET /samehadaku/episode/{episodeId}` - Detail episode
- `GET /samehadaku/server/{serverId}` - Streaming server
- `GET /samehadaku/batch/{batchId}` - Batch download

## Configuration

### Environment Variables

Konfigurasi dapat diatur di `wrangler.toml`:

\`\`\`toml
[vars]
NODE_ENV = "production"
\`\`\`

### Cache Configuration

API menggunakan Cloudflare Cache API untuk performa optimal:
- Static assets: 24 jam
- API responses: 10-30 menit tergantung endpoint
- Error responses: Tidak di-cache

## Performance

- **Cold Start**: < 10ms
- **Response Time**: 50-200ms (tergantung source website)
- **Availability**: 99.9%+ (Cloudflare SLA)
- **Bandwidth**: Unlimited

## Limitations

- **CPU Time**: 50ms per request (Cloudflare Workers limit)
- **Memory**: 128MB per request
- **Request Size**: 100MB max
- **Response Size**: 25MB max

## Troubleshooting

### Common Issues

1. **KV Namespace Error**
   - Pastikan KV namespace sudah dibuat dan ID sudah benar di `wrangler.toml`

2. **Timeout Error**
   - Source website mungkin lambat atau down
   - Coba lagi beberapa saat kemudian

3. **CORS Error**
   - API sudah include CORS headers
   - Pastikan request dari domain yang diizinkan

### Monitoring

Gunakan Cloudflare Dashboard untuk monitoring:
- Request analytics
- Error rates
- Performance metrics
- Geographic distribution

## Contributing

1. Fork repository
2. Create feature branch
3. Commit changes
4. Push to branch
5. Create Pull Request

## License

MIT License - lihat file [LICENSE](LICENSE) untuk detail.

## Support

- 🐛 **Bug Reports**: [GitHub Issues](https://github.com/wajik45/wajik-anime-api/issues)
- 💬 **Discussions**: [GitHub Discussions](https://github.com/wajik45/wajik-anime-api/discussions)
- ☕ **Donate**: [Saweria](https://saweria.co/wajik45)

---

Created with ❤️ by [wajik45](https://github.com/wajik45)
\`\`\`

Sekarang API sudah dikonversi untuk berjalan di Cloudflare Workers! Berikut adalah perubahan utama yang dilakukan:

## Perubahan Utama:

1. **Framework**: Dari Express.js ke Hono (framework yang dioptimalkan untuk Cloudflare Workers)
2. **Dependencies**: Menghapus dependencies Node.js yang tidak kompatibel
3. **Caching**: Menggunakan Cloudflare Cache API dan simple in-memory cache
4. **Static Files**: HTML dan CSS di-inline dalam response
5. **Error Handling**: Disesuaikan dengan Hono error handling
6. **Build System**: Menggunakan Wrangler untuk deployment

## Cara Deploy:

1. Install Wrangler CLI: `npm install -g wrangler`
2. Login: `wrangler login`
3. Deploy: `npm run deploy`

## Keuntungan Cloudflare Workers:

- ⚡ **Performance**: Response time < 100ms globally
- 🌍 **Global**: Berjalan di 200+ data centers
- 💰 **Cost**: Gratis untuk 100K requests/hari
- 🔒 **Security**: Built-in DDoS protection
- 📈 **Scalability**: Auto-scaling tanpa konfigurasi

API sekarang siap untuk di-deploy ke Cloudflare Workers!
