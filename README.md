# RPC Map-Reduce Publication Analysis

## 📌 Objective
This project implements a distributed Map-Reduce pipeline using Python multiprocessing and RPC communication to analyze publication metadata.

The goal is to extract the **Top 10 most frequent first words** from publication titles (`pub_0.txt` to `pub_999.txt`).

---

## ⚙️ Architecture

- **Map Phase**: 
  Each worker retrieves publication titles via RPC and counts first-word frequencies.

- **Reduce Phase**:
  Aggregates counts from all workers and computes global top-10 words.

- **Parallelism**:
  Implemented using `multiprocessing.Pool`.

- **RPC Communication**:
  - `/login` → get secret key
  - `/lookup` → fetch title
  - `/verify` → validate results

---

## 🚀 How to Run

### 1. Install dependencies
```bash
pip install -r requirements.txt
```

### 2. Run the script
```bash
python MDS202513_Assignment.py
```

---

## 🐳 Docker Usage

### Build image
```bash
docker build -t rpc-mapreduce .
```

### Run container
```bash
docker run rpc-mapreduce
```

### Export image
```bash
docker save -o firstname_RollNumber_Assignment01.tar rpc-mapreduce
```

---

## ⚠️ Important Notes

- API rate limit: **100 requests/sec**
- Retry logic implemented for **429 errors**
- Each worker uses its own session key

---

## 📊 Output

Example:
```
Top 10 words: ['A', 'The', 'On', ...]
{
    "score": 10,
    "total": 10,
    "correct": true
}
```

---

## 📁 Project Structure

```
.
├── MDS202513_Assignment.py
├── requirements.txt
├── Dockerfile
├── README.md
└── screenshot.png
```

---

## 🎯 Evaluation Checklist

- ✅ Map-Reduce implemented
- ✅ Multiprocessing used
- ✅ RPC communication handled
- ✅ Docker image created
- ✅ Codespace execution verified
- ✅ Screenshot included

---

## 👨‍💻 Author
Aryan Chauhan  
MDS Program
