# PEPR Batteries – **OPENSTORM**

> *Operando multi‑technique characterisation of battery materials: from the lab bench to large‑scale instruments.*

**OPENSTORM** ("Operando Energy Storage Material Characterisation") is a French national consortium funded through the **PEPR Batteries – France 2030** programme. The project brings together synchrotron & neutron facilities, academic labs, and industrial partners to build an *open*, *modular*, and *multi‑modal* platform for understanding how batteries work — and fail — in real time.\
This repository hosts the **data‑science & machine‑learning layer** of that platform.

| 🔑 Key ideas                | ✨ What it means                                                                        |
| --------------------------- | -------------------------------------------------------------------------------------- |
| **Multimodal sensors**      | Electrical (V, I), thermal, acoustic, X‑ray / µ‑CT, spectroscopy…                      |
| **Time‑resolved, operando** | Measurements collected *while* the cell cycles, across timescales ms → months          |
| **Open & FAIR**             | Standardised metadata schema, open‑source code, reproducible pipelines                 |
| **AI‑powered analytics**    | Deep learning models for State‑of‑Health (SOH) prediction & degradation fingerprinting |

---

## 📂 Repository Layout

```text
PEPR_Batteries_OpenStorm/
├── docs/                   # specs, diagrams, manuscripts, banner image
│   └── img/openstorm_banner.png
├── data/                   # raw ↔ processed datasets (not in git)
├── configs/                # YAML experiment configs
├── openstorm/              # python package (datasets, models, utils)
│   ├── datasets.py
│   └── models/
├── scripts/                # train / evaluate / infer entrypoints
├── tests/                  # pytest unit tests
├── requirements.txt
└── README.md               # you are here
```

---

## 🚀 Quick Start

```bash
# 1. clone
$ git clone https://github.com/<your-org>/PEPR_Batteries_OpenStorm.git
$ cd PEPR_Batteries_OpenStorm

# 2. install deps (Linux/macOS, Python ≥ 3.9)
$ pip install -r requirements.txt

# 3. run a smoke‑test on synthetic data
$ python scripts/train_multimodal_model.py --config configs/baseline.yaml
```

👉  **Real‑world data**: put an HDF5 or Parquet file in `data/raw/` and update `dataset.path` in your YAML config. The loader auto‑detects *data* and *labels* arrays; extend `openstorm/datasets.py` for custom formats.

---

## 🧠 Research Goals

- **Early‑warning SOH** – predict capacity fade ≥ 5 cycles ahead with < 2 % RMSE
- **Failure‑mode ID** – classify Li plating, SEI growth, cracking… from multi‑channel signatures
- **Scalable deployment** – convert PyTorch models to TorchScript / ONNX for BMS firmware

---

## ✨ Results Snapshot *(open‑storm‑cell‑A, 4‑modal)*

| Model             | MAE (capacity) | F1 (failure) |
| ----------------- | -------------- | ------------ |
| LSTM baseline     | 1.8 %          | 0.72         |
| CNN + Transformer | **1.3 %**      | **0.85**     |

See `docs/paper/` for full benchmarks & ablations.

---

## 🤝 Contributing

1. **Open an issue** and describe your bug / feature idea.
2. **Fork → branch** (`feat/your-topic`).
3. Run `pre‑commit run ‑‑all-files` (black, ruff, mypy).
4. Push & open a **PR**; GitHub Actions will run tests.

We follow the [PEP 517] build backend and the DCO sign‑off procedure.

---

## 📜 License

Distributed under the **MIT license**. See `LICENSE`.

---

## 🙌 Acknowledgements

Project coordinated by **CEA‑IRIG**, **ICGM**, and partners at SOLEIL, ESRF, ILL, CNRS laboratories, & industrial stakeholders. Funded by the French Government under grant **ANR‑22‑PENR‑0001** (PEPR Batteries, France 2030).