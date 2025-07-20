# SEED: Streaming Energy Consumption and Emissions Dataset

The **Streaming Energy consumption and Emissions Dataset (SEED)** is an open and FAIR-compliant benchmark designed for energy- and carbon-aware video streaming research. It provides segment-level measurements of energy usage and CO₂ emissions across cloud provisioning and end-user consumption stages.

📄 The complete dataset documentation and methodology are described in the paper:  
**"SEED: Energy and Emission Estimation Dataset for Adaptive Video Streaming"**  [PDF]

## Dataset Structure

```bash
SEED/
├── README.md
├── Provisioning_Encoding_Storage.csv
├── Consumption_Retrieval_Decoding.csv
└── Consumption_Display.csv
```

Each CSV file contains detailed energy and emission measurements for over 500 video segments, under various configurations and conditions.

---

## 📚 CSV File Descriptions

### 1. `Provisioning_Encoding_Storage.csv`

Measures server-side energy and emissions during video encoding and storage.

| Column | Description |
|--------|-------------|
| `video`, `codec`, `width`, `bitrate [kb/s]` | Video metadata |
| `instance_type`, `cpu_model` | Cloud instance details |
| `encoding_duration [s]`, `average_cpu_utilization [%]` | Encoding benchmarks |
| `cpu_energy [kWh]`, `storage_energy [kWh]` | Energy consumed |
| `provisioning_energy_<region>_<PUE> [kWh]` | Region-specific PUE-adjusted energy |
| `emission_<stage>_<region>_<CI> [g]` | CO₂ emissions (see below) |

---

### 2. `Consumption_Retrieval_Decoding.csv`

Captures client-side retrieval (LTE/Ethernet), decoding energy, and emissions.

| Column | Description |
|--------|-------------|
| `video`, `codec`, `width`, `bitrate [kb/s]` | Video and encoding parameters |
| `net`, `userDevice`, `cpu_model` | Network and hardware setup |
| `decoding_duration [s]`, `average_cpu_utilization [%]` | Decode benchmarks |
| `energy_decode [Wh]` | Decoding energy |
| `energy_NIC_<ETH/LTE>_<throughput> [kWh]` | NIC energy at various throughputs |
| `emission_<NIC>_<region>_<CI> [g]` | CO₂ emissions from network usage |

---

### 3. `Consumption_Display.csv`

Contains display energy consumption data.

| Column | Description |
|--------|-------------|
| `video` | Video segment identifier |
| `display_energy [kWh]` | Energy for rendering the video |
| `emission_display_<region>_<CI> [g]` | Associated CO₂ emissions |

---

## ⚙️ Benchmark Summary

- **VCD** – Video Complexity Dataset:  https://ftp.itec.aau.at/datasets/video-complexity/
- **VEED** – Video Encoding Energy and CO₂ Emissions Dataset:  https://github.com/cd-athena/VEED-dataset

- **Codecs**: HEVC and AVC
- **Resolutions**: From 360p to 2160p
- **Bitrates**: 145 kb/s to 16800 kb/s
- **Provisioning**: AWS EC2 instances across Frankfurt, Ireland, Paris, and Northern Virginia
- **Networking**: LTE dongle and Ethernet at various throughputs (16.7 to 60 Mb/s)
- **Decoding**: Intel Xeon Gold 5218 on a PC
- **Display**: LG OLED 4K Monitor (model 27EP950-B)

---

## 🌍 Region-Specific PUE

- **Frankfurt**: 1.35  
- **Ireland**: 1.11  
- **Paris**: 1.04  
- **Northern Virginia**: 1.15

---

## 🏭 Regional Carbon Intensity (CI)

CI values obtained from [Electricity Maps](https://app.electricitymaps.com/zone/US-MIDA-PJM/72h/hourly) on July 11, 2025, at 2:00 AM (GMT-5):

- **Frankfurt**: 334 gCO₂e/kWh  
- **Ireland**: 494 gCO₂e/kWh  
- **Paris**: 13 gCO₂e/kWh  
- **Northern Virginia**: 472 gCO₂e/kWh

---

## 💻 Instance Types

Experiments used the following EC2 instance types:

```
c5.large, c5.xlarge, c5.2xlarge, c5.9xlarge, m5.2xlarge, r5.2xlarge
```
