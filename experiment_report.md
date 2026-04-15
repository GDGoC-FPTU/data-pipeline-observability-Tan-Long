# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600168
**Name:** Tan Long
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Correct — Laptop ($1200) is the highest-priced electronics item after validation |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 1 | Wrong — Nuclear Reactor is an extreme outlier that was never validated or filtered |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi su dung du lieu "rac" (`garbage_data.csv`), Agent tra loi sai vi du lieu dau vao chua nhieu van de nghiem trong ve chat luong. Cu the:

- **Extreme Outlier**: San pham "Nuclear Reactor" co gia $999,999 — cao bat thuong so voi cac san pham thong thuong. Vi Agent dung logic `idxmax()` de chon san pham co gia cao nhat, no lap tuc chon outlier nay thay vi mot san pham thuc su phu hop.
- **Duplicate IDs**: Record voi `id=1` xuat hien 2 lan (Laptop va Banana), gay ra su nham lan ve danh tinh du lieu.
- **Wrong Data Types**: San pham "Broken Chair" co `price = "ten dollars"` (string thay vi so), khien cac phep tinh so hoc co the bi loi.
- **Null Values**: Record "Ghost Item" co `id=None` va `category=None`, la du lieu khong co y nghia nhung van lot vao tap du lieu ma Agent su dung.

Tat ca cac van de tren cho thay rang neu khong co buoc Validate va Transform truoc, Agent se bi "ngo doc" boi du lieu sai, dan den cac khuyen nghi khong the chap nhan duoc trong thuc te.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y.

Du cho prompt co duoc thiet ke tot den dau, neu du lieu dau vao chua nhieu loi (outliers, nulls, sai kieu du lieu), Agent van se tra loi sai. Trong thi nghiem nay, cung mot cau query va cung mot logic Agent, ket qua hoan toan khac nhau chi vi chat luong du lieu. ETL Pipeline voi buoc Validate la lop bao ve quan trong nhat truoc khi du lieu den tay AI/Agent.
