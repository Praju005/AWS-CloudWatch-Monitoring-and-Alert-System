# ☁️ AWS CloudWatch Monitoring and Alert System  
---
## 📘 Project Overview  
This project demonstrates **real-time EC2 instance monitoring using Amazon CloudWatch**, integrated with **SNS notifications** for instant alerts.  
It simulates a real-world **Cloud Operations** scenario where engineers proactively monitor server performance and receive automated alerts when CPU usage exceeds a set threshold.
---
## 🎯 Objective  
> Automatically monitor CPU utilization of an EC2 instance and send an SMS/Email alert when CPU usage exceeds a specified threshold (e.g., 70%).

---

## 🧩 AWS Services Used  

| Service | Purpose |
|----------|----------|
| **Amazon EC2** | Hosts the virtual server workload |
| **Amazon CloudWatch** | Monitors and visualizes performance metrics like CPU usage |
| **Amazon SNS (Simple Notification Service)** | Sends alerts via SMS or Email when alarm thresholds are breached |

---

## 🏗️ Architecture  

┌────────────────┐
│ EC2 Server │
│ (Monitored Node)│
└──────┬──────────┘
│ CPU Metrics
▼
┌────────────────┐
│ CloudWatch │
│ (Monitoring) │
└──────┬──────────┘
│ Alarm Trigger
▼
┌────────────────┐
│ SNS Topic │
│ (SMS / Email) │
└────────────────┘

---

## ⚙️ Step-by-Step Implementation  

### 1️⃣ Launch an EC2 Instance  
- Go to **AWS Console → EC2 → Launch Instance**  
- Select **Amazon Linux 2 AMI**  
- Choose **t2.micro (Free Tier)**  
- Name the instance: `CloudWatchDemoInstance`

---

### 2️⃣ Create an SNS Topic  
- Go to **SNS → Topics → Create topic**  
- Name it: `HighCPUAlerts`  
- Create a subscription (SMS or Email)  
- Confirm your subscription (check your inbox or phone)

---

### 3️⃣ Create a CloudWatch Alarm  
- Go to **CloudWatch → Alarms → Create alarm**  
- Choose metric: `EC2 → Per-Instance Metrics → CPUUtilization`  
- Set condition: **Threshold ≥ 70%**  
- Period: **1 minute**  
- Action: **Send notification to → HighCPUAlerts**  
- Name the alarm: `High_CPU_Alarm`

---

### 4️⃣ Test the Alarm  
Connect to EC2 using **EC2 Instance Connect** or **SSH**, then run:
```bash
dd if=/dev/zero of=/dev/null &
This command simulates high CPU usage.
Wait 2–3 minutes — your CloudWatch alarm will turn In Alarm, and you’ll receive a notification (SMS or Email).
-----
5️⃣ Stop the Load
To stop the CPU load:

bash
Copy code
killall dd
The alarm will return to OK status when CPU usage drops.
------
📊 Output
Feature	Result
✅ Alarm Trigger	CloudWatch Alarm triggered when CPU > 70%
📩 Notification	SNS SMS/Email notification received
📈 Visualization	CloudWatch dashboard displayed CPU metrics
------
🧠 Learning Outcomes
Hands-on with AWS monitoring and alerting

Understanding CloudWatch metrics, alarms, and dashboards

Integration of SNS notifications for real-time alerts

Simulates a Cloud Operations Engineer workflow
-------
🧰 Tools & Technologies
AWS Management Console

Amazon EC2

Amazon CloudWatch

Amazon SNS

