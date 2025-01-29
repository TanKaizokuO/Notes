Start Software
       |
       v
Initialize Systems:
- Flight controller
- Camera (high-res + FPV)
- Edge computing device
- Sensors (LIDAR/ultrasonic, GPS)
- Explosive release system
       |
       v
Check System Health:
- Battery level
- Sensor connectivity
- GPS signal
- Camera feed
       |
       v
Enter Mode Selection:
- Manual Mode
- Auto Mode (Patrol/Track)
       |
       +-------------------+
       |                   |
       v                   v
Manual Mode           Auto Mode
       |                   |
       v                   v
User sends commands   Select Submode: Patrol or Track
       |                   |
       v                   v
Execute commands      Patrol Mode:
       |               - Follow predefined GPS waypoints
       v               - Continuously monitor sensor readings
FPV feed to base      - Camera feeds video to edge computer
       |               - Edge computer processes video for object detection
       v               - Check for obstacles using LIDAR/ultrasonic
Monitor telemetry     - If obstacle detected: Avoid and reroute
       |               - If threat detected: Send SOS to base
       v               - Continue patrolling
End Manual Mode       |
                      v
                      Track Mode:
                      - Operator selects object to track
                      - Drone uses camera + AI to track object
                      - Continuously monitor sensor readings
                      - If obstacle detected: Avoid and reroute
                      - If object is a threat: Command explosive release
                      - Else: Continue tracking or return to Patrol Mode
                      |
                      v
                      Monitor telemetry data:
                      - Battery level
                      - GPS location
                      - Sensor readings (obstacle, altitude, wind speed)
                      |
                      v
                      Battery low?
                      |
                +-----+-----+
                |           |
              Yes          No
                |           |
                v           v
          Failsafe: Return to base  Continue Auto Mode
                |
                v
          End Auto Mode


#### **Day 1 (Wednesday)**
1. **Handling Missing Data | Part 1**: 25 mins
2. **Handling Missing Data | Part 2**: 32 mins
3. **Handling Missing Data | Part 3**: 13 mins
4. **Handling Missing Data | Part 4**: 37 mins
   - **Total**: 107 mins (under daily target).

---

#### **Day 2 (Thursday)**
1. **KNN Imputer**: 25 mins
2. **Multivariate Imputation by Chained Equations for Missing Value**: 19 mins
3. **What are Outliers**: 17 mins
4. **Outlier Detection and Removal using Z-score Method**: 18 mins
5. **Outlier Detection and Removal using the IQR Method**: 14 mins
   - **Total**: 93 mins (under daily target).

---

#### **Day 3 (Friday)**
1. **Outlier Detection using the Percentile Method**: 16 mins
2. **Feature Construction**: 12 mins
3. **Curse of Dimensionality**: 15 mins
4. **Principle Component Analysis (PCA) | Part 1**: 34 mins
5. **Principle Component Analysis (PCA) | Part 2**: 56 mins
6. **Principle Component Analysis (PCA) | Part 3**: 44 mins
   - **Total**: 177 mins (over daily target, but this is the last day).








Flight Control & Operational Flowchart

This flowchart represents the decision-making process in the drone's flight control system, covering manual and autonomous modes, object detection, and failsafe mechanisms.


---

Flowchart Structure

1. Start Flight (Oval)

→ Decision: "Manual Mode or Autonomous Mode?" (Diamond)

2A. Manual Mode (Rectangle)

→ "Receive User Commands"
→ "Transmit FPV Video to Base Station"
→ Decision: "User Switches to Autonomous Mode?" (Diamond)
    ✔ Yes → Switch to Autonomous Mode
    ✖ No → Continue Manual Flight

2B. Autonomous Mode (Rectangle)

→ "Activate AI Object Detection System"
→ "Follow Predefined Patrol Route"
→ Decision: "Threat Detected?" (Diamond)
    ✔ Yes → Trigger Threat Response System
    ✖ No → Continue Patrolling

3. Threat Response System (Rectangle)

→ "Send SOS Alert to Base Station"
→ Decision: "Operator Allows Tracking & Interception?" (Diamond)
    ✔ Yes → Switch to Track Mode
    ✖ No → Continue Patrolling

4. Track Mode (Rectangle)

→ "Follow Detected Object"
→ Decision: "Engagement Required?" (Diamond)
    ✔ Yes → "Initiate Payload Release" (Rectangle)
    ✖ No → Continue Tracking

5. Failsafe System (Rectangle)

→ Decision: "Battery Below Threshold?" (Diamond)
    ✔ Yes → "Return to Base Station" (Rectangle)
    ✖ No → Continue Mission

6. End Flight (Oval)

→ Drone lands safely, and mission logs are stored.


---

How to Draw This Flowchart

You can create this flowchart using:
✔ Draw.io (diagrams.net) – Free and easy to use
✔ Lucidchart – More advanced features
✔ Microsoft Visio – Professional tool
✔ PowerPoint / Google Slides – Simple shapes for quick diagrams

1. Start with an Oval for “Start Flight.”


2. Use Diamonds for Decisions like mode selection, object detection, and threat response.


3. Use Rectangles for Processes like patrolling, tracking, and failsafe actions.


4. Connect shapes using arrows to indicate the flow of decisions and actions.



Would you like me to generate a detailed digital version of this diagram for you?