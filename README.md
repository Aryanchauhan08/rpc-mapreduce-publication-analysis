# RPC Map-Reduce Publication Analysis

## 📌 Objective

This project implements a **distributed Map-Reduce pipeline** using Python to analyze publication metadata via **Remote Procedure Calls (RPC)**.

The task is to compute the **Top 10 most frequent first words** from publication titles (`pub_0.txt` to `pub_999.txt`) hosted on a remote server.

---

## ⚙️ Approach & Architecture

### 🔹 Map Phase

* Each worker process:

  * Authenticates with the RPC server (`/login`)
  * Retrieves publication titles (`/lookup`)
  * Extracts the first word
  * Maintains a local frequency count

### 🔹 Reduce Phase

* Aggregates results from all workers
* Computes global frequency distribution
* Extracts **Top 10 most frequent words**

### 🔹 Parallelism

* Implemented using `multiprocessing.Pool`
* Workload split into chunks for efficiency

### 🔹 RPC Workflow

1. `/login` → Obtain session-specific `secret_key`
2. `/lookup` → Fetch publication title
3. `/verify` → Validate final result

---

## 🚀 Execution

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Run the Program

```bash
python MDS202513_Assignment.py
```

---

## 🐳 Docker Instructions

### Build Image

```bash
docker build -t rpc-mapreduce .
```

### Run Container

```bash
docker run rpc-mapreduce
```

### Export Image (for submission)

```bash
docker save -o aryan_MDS202513_Assignment01.tar rpc-mapreduce
```

---

## ⚠️ Key Implementation Details

* Handles **API throttling (429 errors)** using retry + delay
* Ensures **parallel-safe RPC calls**
* Each worker maintains an independent session (`secret_key`)
* Uses efficient aggregation via `collections.Counter`

---

## 📊 Sample Output

```
Top 10 words: ['Advanced', 'Analytical', 'Comprehensive', ...]
{
    "score": 10,
    "total": 10,
    "correct": true
}
```

---

## 📸 Codespaces Output Screenshot

The execution proof is included as:


Output .png

This screenshot shows:

* Codespaces environment
* Terminal execution
* Final output with **score = 10/10**

---

## 📁 Repository Structure

```
.
├── MDS202513_Assignment.py
├── requirements.txt
├── Dockerfile
├── README.md
└── Output.png
```

---

## ✅ Evaluation Checklist

* ✔ Map-Reduce architecture implemented
* ✔ Multiprocessing used correctly
* ✔ RPC communication handled properly
* ✔ Rate limiting managed
* ✔ Dockerized execution
* ✔ Codespaces execution verified (10/10 score)
* ✔ Screenshot included

---

## 👨‍💻 Author

**Aryan Chauhan**
MDS202513
MDS Program
