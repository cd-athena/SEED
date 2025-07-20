## Provisioning

This dataset captures the energy consumption and carbon emissions associated with video encoding workloads executed on AWS EC2 instances. The computations reflect CPU usage, RAM energy, storage energy, and Power Usage Effectiveness (PUE) across multiple global regions. The final emissions are calculated using region-specific Carbon Intensity (CI) values.


## 📄 Column Descriptions

| Column Name | Description |
|-------------|-------------|
| `SI`, `TI` | Sequence and temporal index of the video segment |
| `codec` | Video codec used |
| `preset` | Encoder preset |
| `video` | Video file name |
| `width`, `height` | Video resolution |
| `bitrate [kb/s]` | Target bitrate for streaming |
| `instance_type` | AWS EC2 instance type (e.g., `c5.large`) |
| `serve_cpu_model` | CPU model used in the EC2 instance |
| `server_cpu_count` | Number of CPUs in the instance |
| `duration [s]` | Encoding duration of the video segment |
| `average_cpu_utilization [%]` | Average CPU usage during encoding |
| `cpu_energy [kWh]` | CPU energy consumption |
| `storage_energy [kWh]` | Storage system energy |
| `provisioning_energy [kWh]` | Sum of CPU and storage energy |
| `provisioning_energy_PUE_<Region> [kWh]` | Energy including PUE overhead for a specific region |
| `emission_<Region>_CI_<value> [gramsCO₂e/kWh]` | Carbon emissions per region using regional CI |

---

## **region-specific PUE:**  
   - Frankfurt: 1.35
   - Ireland: 1.11
   - Paris: 1.04
   - Northern Virginia: 1.15

## **regional Carbon Intensity (CI) values  & CI Sources :**
   CI values obtained from [Electricity Maps](https://app.electricitymaps.com/zone/US-MIDA-PJM/72h/hourly) on July 11, 2025, at 2:00 AM (GMT-5).
   - Frankfurt: 334 gCO₂e/kWh
   - Ireland: 494 gCO₂e/kWh
   - Paris: 13 gCO₂e/kWh
   - Northern Virginia: 472 gCO₂e/kWh


## 📊 Dataset Sources

- **VCD** – Video Complexity Dataset:  https://ftp.itec.aau.at/datasets/video-complexity/.
- **VEED** – Video Encoding Energy and CO₂ Emissions Dataset:  https://github.com/cd-athena/VEED-dataset

---

## 💻 Instance Types

Experiments used the following EC2 instance types:
```
c5.large, c5.xlarge, c5.2xlarge, c5.9xlarge, m5.2xlarge, r5.2xlarge
```

---


## 🧪 Streaming Configurations
Codec:
`libx264`, `libx265`

Encoder preset: `medium`

Adaptive bitrate streaming settings used:
- 360p (145 kbit/s)
- 540p (1600 kbit/s)
- 720p (3400 kbit/s)
- 1080p (5800 kbit/s)
- 1440p (8100 kbit/s)
- 2160p (16800 kbit/s)

## Consumption

## 📑 Column Descriptions

| Column Name | Description |
|-------------|-------------|
| `video` | Video file name |
| `width`, `height` | Video resolution |
| `bitrate [kb/s]` | Target bitrate for streaming |
| `codec` | Video codec used (e.g., AVC, HEVC) |
| `preset` | Encoder preset (e.g., fast, medium) |
| `energy_decode_wh` | Energy consumed during decoding (Wh) |
| `energy_NIC_LTE_TH_<rate> [kWh]` | NIC energy for LTE at various throughput levels (e.g., 20, 42, 60 Mbps) |
| `device_cpu_utilization` | CPU usage during decoding (fraction of total) |
| `user_time_decoding` | CPU time in user mode during decoding |
| `system_time_decoding` | CPU time in system mode during decoding |
| `display_energy_kWh` | Energy consumed by the display subsystem (kWh) |
| `emission_display_energy_kWh_<Region>` | CO₂ emissions from display energy in specific regions |
| `SI`, `TI` | Sequence and temporal index of the video segment |
| `cpu_energy [kWh]` | CPU energy consumption |
| `storage_energy [kWh]` | Storage system energy consumption |
| `provisioning_energy [kWh]` | Sum of CPU and storage energy |
| `provisioning_energy_PUE_<Region> [kWh]` | Provisioning energy with PUE overhead for a specific region |
| `emission_<Region>_CI_<value> [gramsCO₂e/kWh]` | CO₂ emissions per region using regional carbon intensity |

