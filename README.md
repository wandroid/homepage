# Polling Place Bottleneck Simulation

An interactive 2D simulation built with HTML5 Canvas and JavaScript to model, demonstrate, and solve process flow bottlenecks at voting locations. 

[cite_start]This model was specifically designed to visualize the stark contrast between early voting days and the Election Day rush [cite: 6][cite_start], focusing on the flow dynamics between Electronic Ballot Markers (EBM) and Ballot On Demand (BOD) printers[cite: 9, 10, 11].

## 🎯 Purpose of the Model

[cite_start]During peak demand (such as the 5:00 PM to 7:45 PM rush), queues rapidly build if the arrival rate exceeds processing time at any specific node[cite: 7, 12]. [cite_start]This simulation addresses a specific process flow flaw involving the manual hand-off of the "Ballot Form" (a printed receipt carrying the voter's precinct and language choice)[cite: 50]. 

[cite_start]The model demonstrates mathematically and visually why treating a serial process (1 BOD printer) the same as a parallel process (7 independent EBM machines) causes the entire check-in system to collapse, and proves how a simple routing change resolves it[cite: 120].

## ⚙️ The Two Workflows

### 1. Original Mode: The "Coupled" Flow (The Flaw)
* [cite_start]**The Process:** Poll Pad Workers (PPW) take the Ballot Form directly to the BOD station and wait for the ballot to print, blocking their own input queue[cite: 64]. 
* **The Flaw:** This creates a "synchronous block." [cite_start]By waiting for the high-latency BOD printer, the PPW is essentially neutralized, artificially capping the check-in speed[cite: 73, 74]. [cite_start]The line backs up out the front door, and stacked, anonymous receipts at the printer risk getting scrambled[cite: 76].

### 2. Proposed Mode: The "Decoupled" Flow (The Solution)
* [cite_start]**The Process:** The system is decoupled by shifting the physical token (the Ballot Form) from the worker to the voter[cite: 87]. [cite_start]The voter takes their form and queues directly at the BOD station[cite: 88].
* [cite_start]**The Result:** The PPW desk instantly frees up to process the next person, maximizing check-in throughput[cite: 90, 91]. [cite_start]While a queue still forms at the BOD due to its serial nature, the wait becomes transparent to the voter, and the risk of scrambled, anonymous receipts is entirely eliminated[cite: 93, 96, 109].

## 📊 Features & Controls

* **Workflow Mode Toggle:** Switch between the "Coupled" (Original) and "Decoupled" (Proposed) routing methods in real-time.
* [cite_start]**Arrival Rate Slider:** Adjust the volume of voters from 10 to 150 per simulated hour to simulate sudden bursts of demand[cite: 261].
* **Paper Routing Ratio (%):** Adjust the percentage of voters routed to the BOD. [cite_start]This demonstrates the catastrophic bottleneck that occurs if poll workers attempt to "sell" the paper ballot to EBM-bound voters during a rush[cite: 117, 119].
* [cite_start]**Manual Chronometer:** A Start/Stop/Clear timer displaying whole "Simulated Minutes" allows users to benchmark exactly how long it takes queues to clear under different conditions[cite: 280, 296].

## ⏱️ Technical Timing Parameters
[cite_start]The simulation runs on a scaled engine where 60 animation frames equal 1 simulated minute[cite: 271]. 
* [cite_start]**Check-in:** 1 simulated minute [cite: 251]
* [cite_start]**BOD Print:** 4 simulated minutes [cite: 251]
* [cite_start]**EBM Vote:** Randomized between 5 to 20 simulated minutes per voter to account for real-world variance [cite: 251]

## 🚀 How to Run

Since this is a self-contained vanilla HTML/JS file, no build tools or installations are required. 

1. Simply open the `PollQ.html` file in any modern web browser (Chrome, Safari, Edge, Firefox).
2. Alternatively, view the live model via the direct URL: `[Insert Your GitHub Pages or Raw URL Here]`
