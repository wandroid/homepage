# Polling Place Bottleneck Simulation

An interactive 2D simulation built with HTML5 Canvas and JavaScript to model, demonstrate, and optimize process flow at voting locations. 

This model was specifically designed to visualize the stark contrast between early voting days and the Election Day rush, focusing on the flow dynamics between Electronic Ballot Markers (EBM) and Ballot On Demand (BOD) printers.

## 🎯 Purpose of the Model

During peak demand (such as the 5:00 PM to 7:45 PM rush), queues rapidly build if the arrival rate exceeds the processing time at any specific node. This simulation explores a workflow challenge involving the manual hand-off of the "Ballot Form" (a printed receipt carrying the voter's precinct and language choice). 

The model demonstrates mathematically and visually how tying a serial process (1 BOD printer) directly to the parallel check-in stations can inadvertently bottleneck the entire system during surges, and illustrates how a simple routing adjustment can keep lines moving smoothly.

## ⚙️ The Two Workflows

### 1. Original Mode: The "Coupled" Flow (Current Setup)
* **The Process:** Poll Pad Officers (PPO) take the Ballot Form directly to the BOD station and wait for the ballot to print, remaining occupied until the printer finishes. 
* **The Challenge:** This creates an unintended "synchronous dependency." By waiting for the high-latency BOD printer, the PPO's check-in speed is temporarily capped to match the printer's output speed. During high volume, the entrance line backs up, and stacked, anonymous receipts at the printer can become difficult to manage if an issue like a paper jam occurs.

### 2. Proposed Mode: The "Decoupled" Flow (The Optimization)
* **The Process:** The system is decoupled by shifting the physical token (the Ballot Form) from the worker to the voter. The voter takes their form and queues directly at the BOD station.
* **The Result:** The PPO desk instantly frees up to process the next person, maximizing check-in throughput. While a queue still naturally forms at the BOD due to its serial nature, the wait becomes transparent to the voter, and the risk of managing anonymous receipts is entirely eliminated.

## 📊 Features & Controls

* **Workflow Mode Toggle:** Switch between the "Coupled" (Original) and "Decoupled" (Proposed) routing methods in real-time.
* **Arrival Rate Slider:** Adjust the volume of voters from 10 to 150 per simulated hour to simulate sudden bursts of demand.
* **Paper Routing Ratio (%):** Adjust the percentage of voters routed to the BOD. This demonstrates the extreme pressure that builds on the single printer if poll workers attempt to "sell" the paper ballot to EBM-bound voters during a rush.
* **Manual Chronometer:** A Start/Stop/Clear timer displaying whole "Simulated Minutes" allows users to benchmark exactly how long it takes queues to clear under different conditions.

## ⏱️ Technical Timing Parameters
The simulation runs on a scaled engine where 60 animation frames equal 1 simulated minute. 
* **Check-in:** 1 simulated minute
* **BOD Print:** 4 simulated minutes
* **EBM Vote:** Randomized between 5 to 20 simulated minutes per voter to account for real-world variance.

## 🚀 How to Run & Usage Tips

Since this is a self-contained HTML/JS file, no build tools or installations are required. 

1. View the live model via the direct URL: `https://wandroid.github.io/homepage/PollQ.html`
2. Alternatively, download and open the `PollQ.html` file in any modern web browser.

**📱 Mobile Viewing Tip:** While you can access and run this simulation on a smartphone out in the field (using swipe to scroll and pinch-to-zoom), it is highly recommended to view it on a larger screen (desktop, laptop, or tablet) first. Seeing the entire layout on a big screen makes it much easier to understand the "big picture" of the floor's process flow before taking it on the go!
