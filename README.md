# Polling Place Bottleneck Simulation

An interactive 2D simulation built with HTML5 Canvas and JavaScript to model, demonstrate, and solve process flow bottlenecks at voting locations. 

This model was specifically designed to visualize the stark contrast between early voting days and the Election Day rush, focusing on the flow dynamics between Electronic Ballot Markers (EBM) and Ballot On Demand (BOD) printers.

## 🎯 Purpose of the Model

During peak demand (such as the 5:00 PM to 7:45 PM rush), queues rapidly build if the arrival rate exceeds processing time at any specific node. This simulation addresses a specific process flow flaw involving the manual hand-off of the "Ballot Form" (a printed receipt carrying the voter's precinct and language choice). 

The model demonstrates mathematically and visually why treating a serial process (1 BOD printer) the same as a parallel process (7 independent EBM machines) causes the entire check-in system to collapse, and proves how a simple routing change resolves it.

## ⚙️ The Two Workflows

### 1. Original Mode: The "Coupled" Flow (The Flaw)
* **The Process:** Poll Pad Workers (PPW) take the Ballot Form directly to the BOD station and wait for the ballot to print, blocking their own input queue. 
* **The Flaw:** This creates a "synchronous block." By waiting for the high-latency BOD printer, the PPW is essentially neutralized, artificially capping the check-in speed. The line backs up out the front door, and stacked, anonymous receipts at the printer risk getting scrambled.

### 2. Proposed Mode: The "Decoupled" Flow (The Solution)
* **The Process:** The system is decoupled by shifting the physical token (the Ballot Form) from the worker to the voter. The voter takes their form and queues directly at the BOD station.
* **The Result:** The PPW desk instantly frees up to process the next person, maximizing check-in throughput. While a queue still forms at the BOD due to its serial nature, the wait becomes transparent to the voter, and the risk of scrambled, anonymous receipts is entirely eliminated.

## 📊 Features & Controls

* **Workflow Mode Toggle:** Switch between the "Coupled" (Original) and "Decoupled" (Proposed) routing methods in real-time.
* **Arrival Rate Slider:** Adjust the volume of voters from 10 to 150 per simulated hour to simulate sudden bursts of demand.
* **Paper Routing Ratio (%):** Adjust the percentage of voters routed to the BOD. This demonstrates the catastrophic bottleneck that occurs if poll workers attempt to "sell" the paper ballot to EBM-bound voters during a rush.
* **Manual Chronometer:** A Start/Stop/Clear timer displaying whole "Simulated Minutes" allows users to benchmark exactly how long it takes queues to clear under different conditions.

## ⏱️ Technical Timing Parameters
The simulation runs on a scaled engine where 60 animation frames equal 1 simulated minute. 
* **Check-in:** 1 simulated minute
* **BOD Print:** 4 simulated minutes
* **EBM Vote:** Randomized between 5 to 20 simulated minutes per voter to account for real-world variance

## 🚀 How to Run

Since this is a self-contained vanilla HTML/JS file, no build tools or installations are required. 

1. Simply open the `PollQ.html` file in any modern web browser (Chrome, Safari, Edge, Firefox).
2. Alternatively, view the live model via the direct URL: `https://wandroid.github.io/homepage/PollQ.html`
