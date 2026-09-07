# Insurance Service Delivery & Quality Performance MIS Dashboard

An end-to-end Executive Management Information System (MIS) Dashboard built in Microsoft Excel to track operational productivity, turnaround times (TAT), quality assurance (QA) compliance, and employee training ramp-up trajectories across insurance business process lines.

![Dashboard Preview](docs/dashboard_screenshot.png)

---

## 📌 Executive Summary & Business Context

In high-volume service delivery operations, managing capacity while maintaining quality compliance is critical. This project synthesizes two distinct data feeds—a **Production Tracking Log** and a **Quality Audit Log**—into a unified data model to evaluate team throughput, SLA adherence, and defect rates.

### Key Business Questions Addressed:
* **Productivity & Capacity:** What is the total transaction volume processed, and how does throughput vary by account and task line?
* **Turnaround Time (SLA):** What is the average elapsed processing time per task, and do volume spikes negatively impact delivery speed?
* **Quality & Accuracy:** What is the overall operational accuracy rate, and which processes exhibit high defect counts during QA audits?
* **Training & Ramp-up Efficiency:** How do learning curves (Onboarding, Cross-Training, Replacements) impact team baseline performance compared to standard production?

---

## 📊 Key Performance Indicators (KPIs) Captured

* **Total Volume Processed:** Aggregate completed units (`# Processed`).
* **Average Turnaround Time (TAT):** Elapsed days from assignment to completion (`Complete Date - Assign Date`).
* **Overall Accuracy Rate (%):** Defect-free percentage evaluated as:
  $$\text{Accuracy \%} = 1 - \left(\frac{\text{Total Defect Errors}}{\text{Total Audited Units}}\right)$$
* **QA Audit Coverage %:** Sampling rate calculated against total production volume.
* **Trainee vs. Production Split:** Workload distribution across regular production, cross-training, and new-hire onboarding modes.

---

## 🏗️ Architecture & Data Modeling

Because I wanted the raw source tables to be untouched, the solution uses a decoupled **3-Layer Excel Architecture**:

```text
[Raw Production Data] + [Raw Quality Data]
         │
         ▼
[Calculation_Sheet]  <-- Data modeling, composite keys, multi-criteria SUMIFS lookups
         │
         ▼
[Pivot_Engine]       <-- Dynamic aggregation tables & calculated fields
         │
         ▼
[Dashboard]          <-- Interactive UI (KPI Cards, Pivot Charts, Slicers & Timeline)


### Advanced Excel Features Used:

* **Data Modeling via Multi-Criteria Lookups:** Integrated multi-key mapping using `SUMIFS` across `Complete Date`, `Account`, `Task Name`, and `Processor` to bridge quality audits with production output.
* **Dynamic Helper Columns:** Calculated tracking hours, processing speed (units/hr), turnaround days, and standardized training status flags.
* **Interactive UI/UX Controls:** Implemented Timeline filters and Report-Connected Slicers (`Account`, `Processor`, `Training Status`) that dynamically update all dashboard charts and KPI summary blocks simultaneously.

---

## 🛠️ Dashboard Visual Features

1. **Production Volume & TAT Trend:** Dual-axis Combo Chart mapping volume throughput (bars) against average turnaround time (line) over time.
2. **Account & Service Line Distribution:** Stacked Bar Chart evaluating task distribution across key client accounts.
3. **Quality & Defect Analysis:** Clustered Column Chart visualizing sampled audit units vs. identified defect counts by process type.
4. **Processor Productivity Leaderboard:** Ranked performance matrix evaluating associate volume against tracked work hours.

---

## 💡 Strategic Business Insights

* **Training Ramp-Up Impact:** Isolating `New Team Member Onboarding` and `Cross Training` cases prevents learning-curve duration spikes from skewing regular production performance baselines.
* **Quality Bottleneck Identification:** Cross-analyzing error rates against overall processing speed highlights specific high-complexity tasks that require targeted refresher training or workflow optimization.
* **Capacity Optimization:** Slicer-driven workload filtering enables operations managers to reallocate cross-trained resources to high-volume process queues during peak mid-month windows.

---

## 🚀 How to Run the Project

1. Clone or download this repository to your local computer:
   ```bash
git clone [https://github.com/your-username/insurance-service-delivery-mis-dashboard.git](https://github.com/your-username/insurance-service-delivery-mis-dashboard.git)
```
2. Open ResourcePro_Service_Delivery_MIS.xlsx using Microsoft Excel 2019 or later.
3. Navigate to the Dashboard tab.
4. Use the top Timeline Control or the Slicers on the side panel to dynamically interact with the dataset.

