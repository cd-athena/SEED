## Provisioning

This dataset captures the energy consumption and carbon emissions associated with video encoding workloads executed on AWS EC2 instances. The computations reflect CPU usage, RAM energy, storage energy, and Power Usage Effectiveness (PUE) across multiple global regions. The final emissions are calculated using region-specific Carbon Intensity (CI) values.


## **region-specific PUE:**  
   - Frankfurt: 1.35
   - Ireland: 1.11
   - Paris: 1.04
   - Northern Virginia: 1.15

## **regional Carbon Intensity (CI) values:**
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


## 🧪 Encoding Configurations
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



## 📑 SEED Column Descriptions

| **Dataset column name**                                | **Description**                                                                 |
|--------------------------------------------------------|---------------------------------------------------------------------------------|
| `video`, `codec`, `width`, `bitrate`                   | Video metadata                                                                  |
| `instance/device`, `cpu_model`                         | Instance/device info                                                            |
| `net`                                                  | Network info                                                                    |
| `<stage>_duration`                                     | Encoding or decoding duration (seconds)                                         |
| `average_cpu_utilization`                              | CPU utilization (%)                                                             |
| `encoding_energy`                                      | Energy used for encoding video (kWh)                                            |
| `storage_energy`                                       | Energy used to store encoded video (kWh)                                        |
| `provisioning_energy_<region>_<PUE>`                   | Total provisioning energy considering datacenter PUEs (kWh)                     |
| `decoding_energy`                                      | Energy used for decoding video (kWh)                                            |
| `retrieval_<NIC>_<bandwidth>_energy`                   | Energy used to retrieve video through NIC (kWh)                                 |
| `display_energy`                                       | Energy used to display video (kWh)                                              |
| `emission_<stage>_<region>_<CI>`                       | CO₂ emissions (g)                                                               |


