# 🚀 From L/R to Visible Network

> You are not measuring packets.  
> **You are watching time.**

<img width="1536" height="1024" alt="serialization-vs-throughput" src="https://github.com/user-attachments/assets/b700a8bc-f4d9-4c1b-b801-dc1ae8e4af7e" />


---

## 🧠 What This Project Is

Most engineers know:
Serialization Delay = L / R

But very few have actually **seen it**.

This project bridges the gap:

**From:**
- A textbook formula (L/R)

**To:**
- A visible, measurable network behavior

---

## ⚡ Core Insight

> **Serialization is constant.  
> Throughput is not.**

---

## 🧩 The Mental Model

Throughput = Frame Size / (Serialization + Gap)

---

## 🔥 Why This Matters

Even on a perfect **10 Mbps link**, you may observe:

- 9.8 Mbps  
- 5 Mbps  
- 2 Mbps  

👉 The link didn’t change.  
👉 **The timing did.**

---

## 🧪 Lab Topology

![Lab Topology](./Lab-Topology.jpg)


---

## ⏱️ What You Are Actually Observing

### Packet Train

Frame1 Frame2 Frame3 Frame4
|-----| |-----| |-----| |-----|
L/R L/R L/R L/R


👉 Continuous → Full throughput  
👉 Gaps → Throughput drop  

---

### The Full System

Serialization → Packet Train → ACK Clock → Queue → Throughput


---

## 📊 Expected Results

| Link Speed | Frame Size | Δt (Theory) | Δt (Observed) |
|------------|------------|------------|---------------|
| 10 Mbps    | 1518 B     | ~1.2 ms    | ✔ Match       |
| 100 Mbps   | 1518 B     | ~0.12 ms   | ✔ Match       |
| 1 Gbps     | 1518 B     | ~0.012 ms  | ✔ Match       |

---

## 📸 Packet Evidence (Replace with your captures)

### 10 Mbps

- Δt ≈ 1.2 ms  
- Very stable spacing  

---

### 100 Mbps

- Δt ≈ 0.12 ms  
- 10× compression  

---

### 1 Gbps

- Δt ≈ 0.012 ms  
- Approaching timestamp precision limit  

---

## 🔬 Reproducible Steps

### 1️⃣ Setup

- Direct connection (Client ↔ Server)
- Fix NIC speed (10M / 100M / 1G)
- Insert TAP
- Connect analyzer

---

### 2️⃣ Generate Traffic

curl -O http://server/testfile.bin
 

---

### 3️⃣ Capture

- Use NPM Device / Protocol Analyzer
- Capture on TAP monitor port

---

### 4️⃣ Filter

tcp.stream eq X


---

### 5️⃣ Measure

Look at:

![Lab Topology](./Delta-time.jpg)


---

Time delta from previous frame
 

---

### 6️⃣ Validate

Check:

- Does Δt scale with 1/R?
- Are frames continuous?
- Are there gaps?

---

## ⚠️ Measurement Validity

> TAP aggregation does NOT affect serialization measurement.

Because:

- Serialization happens **before TAP**
- TAP only mirrors traffic
- Timing remains intact

---

## 🧭 What Changes After This Lab

Before:
- You see packets

After:
- You see timing
- You see gaps
- You see TCP rhythm
- You see queue buildup

---

## 🧠 One-Line Summary

> **Bandwidth tells you capacity.  
> Timing tells you reality.**

---

## ⭐ Final Thought

> Most engineers measure throughput.  
> Few measure time.  
> **Fewer understand that throughput is time.**

---

## 📦 Future Work

- ACK Clock visualization  
- CUBIC behavior  
- BDP limits  
- Queue dynamics  

---

## 📎 License

MIT

---

## 🙌 Author

25+ years in Network Performance Monitoring  
Finally decided to *look at L/R seriously*

## 📸 Image Attribution

- Serialization vs Throughput diagram: generated for this project
- Lab topology diagram: original work by the author
- Packet analysis screenshots: obtained using Wireshark (open-source tool)


