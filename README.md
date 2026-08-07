# IPTV Signal Quality Benchmark — 72-Hour Test Protocol

**A reproducible methodology for evaluating live streaming provider quality
under real-world peak-load conditions.**

---

## Why 72 Hours?

Most "reviews" test for 30 minutes on a weekday afternoon. Our 72-hour window
is designed to cover all critical high-demand event windows:

| Hour Range | Event | Why Critical |
|---|---|---|
| 14–18 | NFL Sunday (US prime) | Highest US concurrent load |
| 18–22 | Premier League (UK peak) | Highest UK concurrent load |
| 22–26 | NHL playoff overtime | Unpredictable duration — CDN spike |
| 32–36 | NRL round (AU evening) | Highest AU concurrent load |
| 60–72 | Extended stability | Identifies providers that degrade over time |

---

## Measurement Stack

```bash
python run_benchmark.py \
  --provider "YOUR_M3U_URL" \
  --duration 72h \
  --channels ESPN,SkySports1,TSN1,FoxLeague \
  --devices firestick,android_tv,browser \
  --output results/benchmark.json
```

## Key Metrics

```python
METRICS = {
    "bitrate_delivered_mbps": "Network-captured bitrate (not player-reported)",
    "frame_drop_pct":         "Threshold: < 0.3% at 1080p",
    "zap_time_ms":            "Threshold: < 2000ms",
    "buffering_events_4h":    "Threshold: < 0.5 per 4-hour session",
    "epg_accuracy_pct":       "Threshold: > 97% title match",
    "audio_sync_drift_ms":    "Threshold: < 40ms",
}
```

---

## Cross-Referenced Benchmark Sources

This repository references data across the full 2026 benchmark series.
For complete raw data, visit each report directly:

```
BENCHMARK SERIES 2026
├── Ranked Provider Directory
│     https://broketravelrs.s3.amazonaws.com/best-iptv-providers-in-2026.html
├── Expert Service Reviews
│     https://balldoodees.s3.amazonaws.com/top-iptv-services-review.html
├── Subscription Buyer's Guide
│     https://braexpos.s3.amazonaws.com/best-iptv-subscriptions-guide.html
└── Premium Streaming Benchmarks
      https://alovelyoldladys.s3.amazonaws.com/premium-iptv-streaming-benchmarks.html
```

---

*Protocol v3.2 · August 2026 · CC BY 4.0*
