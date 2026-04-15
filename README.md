[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23573982&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** email@example.com
**Name:** Tan Long

---

## Mo ta

Bai lab xay dung mot ETL Pipeline tu dong doc du lieu JSON, kiem tra chat luong du lieu (loai bo gia am va category rong), chuan hoa danh muc sang Title Case, tinh gia giam 10%, va luu ket qua ra CSV. Sau do chay Agent Simulation de so sanh ket qua khi su dung Clean Data va Garbage Data.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Buoc 1: Tao garbage data
python generate_garbage.py

# Buoc 2: Chay Agent voi ca 2 bo du lieu
python agent_simulation.py
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- Tong so records trong `raw_data.json`: **5**
- Records hop le sau Validate: **3** (loai 2 records: gia am + category rong)
- Records da luu vao `processed_data.csv`: **3**
- Agent voi Clean Data: tra loi chinh xac (Laptop $1200)
- Agent voi Garbage Data: tra loi sai do outlier (Nuclear Reactor $999,999)
