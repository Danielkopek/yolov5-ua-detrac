# YOLOv5 × UA-DETRAC — Vehicle Detection

> Vehicle detection on the UA-DETRAC benchmark dataset using YOLOv5.

---

## About

This project adapts [YOLOv5](https://github.com/ultralytics/yolov5) for training and evaluation on the [UA-DETRAC](http://detrac-db.rit.albany.edu/) dataset — a large-scale benchmark for multi-object vehicle detection and tracking recorded from real traffic surveillance cameras.

The goal is to fine-tune YOLOv5 on UA-DETRAC to detect vehicles (cars, buses, vans, others) in challenging real-world conditions including occlusion, weather changes, and varying lighting.

---

## Features

- YOLOv5 trained on UA-DETRAC vehicle classes
- Preprocessing pipeline to convert UA-DETRAC annotations to YOLO format
- Training, validation, and inference scripts
- Evaluation against UA-DETRAC benchmark metrics

---

## Dataset

[UA-DETRAC](http://detrac-db.rit.albany.edu/) is a challenging real-world dataset collected from 24 locations in Beijing and Tianjin, China.

- 100 video sequences
- Over 140,000 frames
- 8,250 labeled vehicles
- 4 vehicle classes: car, bus, van, others

> Download the dataset from the [official site](http://detrac-db.rit.albany.edu/) and place it in the `data/` folder.

---

## Installation

```bash
git clone https://github.com/Danielkopek/yolov5-ua-detrac.git
cd yolov5-ua-detrac
pip install -r requirements.txt
```

Requires Python 3.8+ and PyTorch 1.8+.

---

## Usage

### Prepare dataset

```bash
python data/prepare_detrac.py --source data/UA-DETRAC/
```

### Train

```bash
python train.py --data data/detrac.yaml --weights yolov5s.pt --epochs 50
```

### Inference

```bash
python detect.py --weights runs/train/exp/weights/best.pt --source data/UA-DETRAC/test/
```

### Evaluate

```bash
python val.py --weights runs/train/exp/weights/best.pt --data data/detrac.yaml
```

---

## Project Structure

```
yolov5-ua-detrac/
├── data/
│   ├── detrac.yaml          # Dataset config
│   └── prepare_detrac.py    # Annotation conversion script
├── models/                  # YOLOv5 model configs
├── utils/                   # Utility functions
├── train.py                 # Training script
├── detect.py                # Inference script
├── val.py                   # Evaluation script
└── requirements.txt
```

---

## License

This project is licensed under the [GNU Affero General Public License v3.0](LICENSE).

The YOLOv5 base code is © Ultralytics, also licensed under AGPL-3.0.

---

## Acknowledgements

- [Ultralytics YOLOv5](https://github.com/ultralytics/yolov5)
- [UA-DETRAC Benchmark](http://detrac-db.rit.albany.edu/)
