# 🔄 Using a File for Additional Swap Space in Linux:


## 📌 What is Swap?

Swap is **virtual memory** located on disk that the operating system uses when physical **RAM is full**.  

- When the system runs out of RAM, **inactive memory pages** are moved to swap space.  
- This frees up RAM for **active processes**.  
- Since **disk is slower than RAM**, swap is only a **fallback mechanism** and not a substitute for physical memory.  

---

## 👉 Recommended Swap Size:

- **If RAM < 2 GB** → Swap = `2 × RAM`  
- **If RAM ≥ 2 GB** → Swap = `RAM + 2 GB`  

> Example: If you have **4 GB RAM**, recommended swap = `4 GB + 2 GB = 6 GB`.  

---

## 🛠 Steps to Create a Swap File:


### 1️⃣ Create a Swap File
Use the `dd` command to create a swap file of the desired size.  

Example: Create a **2 GB swap file** at `/newswap`:  

```
sudo dd if=/dev/zero of=/newswap bs=1M count=2048
```

**Explanation:**

- `if=/dev/zero` → Input file providing zeros.  
- `of=/newswap` → Output file (path of swap file).  
- `bs=1M` → Block size = 1 MB per write.  
- `count=2048` → Number of blocks (1 MB × 2048 = 2 GB).  

---

### 2️⃣ Set Correct Permissions:

Swap files should **only** be accessible by root:  

```
sudo chmod 600 /newswap
```

### 3️⃣ Format File as Swap:

Convert the file into swap space:  

```
sudo mkswap /newswap
```



### 4️⃣ Enable Swap File:

Turn on the swap file immediately:  

```
sudo swapon /newswap
```

✅ Verify active swap:  

```
swapon --show
free -h
```

### 5️⃣ Make Swap Permanent:

## To enable swap at **every reboot**, edit `/etc/fstab` and add:  

```
/newswap swap swap defaults 0 0
```

---

### 6️⃣ Test Swap Configuration:

## Without rebooting, test the configuration:  

## disables all swap:
```
sudo swapoff -a  
```
## enables all swap from /etc/fstab:

```
sudo swapon -a    
```

## 📊 Verification:

Run:  

```
free -h
```

## You should see something like:  

```
              total        used        free      shared  buff/cache   available
Mem:           2.0G        1.2G        500M        100M        300M        600M
Swap:          1.0G          0B        1.0G
```

## Images:

## 1. Create a swap file:

<img width="981" height="278" alt="Image" src="https://github.com/user-attachments/assets/642d33b8-244c-4ff9-9c03-feae4535ac25" />

## 2. Change Mode permissions:

<img width="770" height="207" alt="Image" src="https://github.com/user-attachments/assets/149310a2-9b23-4fad-9abe-ec00ce2c733a" />

## 3. Format file as swap:

<img width="936" height="117" alt="Image" src="https://github.com/user-attachments/assets/3cec719e-0292-46e1-ad92-d4b6294d4ff2" />

## 4. Swapon:

<img width="677" height="193" alt="Image" src="https://github.com/user-attachments/assets/c10311c8-b5b9-4db0-85be-bf6cd7504724" />

## 5. Free -h swap:

<img width="1081" height="213" alt="Image" src="https://github.com/user-attachments/assets/1ce92241-0093-4800-a025-3e0e1109b902" />

## 6. DF -h :

<img width="787" height="281" alt="Image" src="https://github.com/user-attachments/assets/0297469d-fc99-4ecb-a15d-d39f902fd25d" />


## ⚠️ Important Notes:

- On **cloud servers** (like AWS EC2, GCP, Azure), swap is usually **not enabled by default** (especially on smaller instance types).  
- Using swap on **SSD-based storage (EBS in AWS)** can reduce performance but is still useful for stability.  
- Do not place swap on **network-mounted storage (e.g., NFS, EFS)**.  

---

## ✅ Conclusion:

You have successfully created and enabled swap space using a **swap file** in Linux. This ensures better system stability when your RAM runs low.  

## Author:

**Uday Sairam Kommineni**

**System Administration**

**Mail-Id:** saikommineni5@gmail.com

**Linkedin-URL:** https://www.linkedin.com/in/uday-sai-ram-kommineni-uday-sai-ram/


