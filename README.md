We are building a scalable wireless IoT cleanliness intelligence system using the Arduino UNO Q by Qualcomm as the central edge-processing board.

System Goal:
Create a smart environmental cleanliness monitoring system that can detect and classify room/bus/train cleanliness conditions using multiple wireless sensor nodes. The system should not directly clean but should intelligently determine when and where cleaning attention is required and send actionable insights to users, dashboards, or cleaning systems.

Core Requirements:

1. Main Architecture
- Arduino UNO Q acts as:
  - edge intelligence processor
  - mesh/network gateway
  - node registry manager
  - cloud communication hub
  - sensor fusion engine
- Sensor nodes communicate wirelessly.
- Nodes must be plug-and-play.
- Nodes should automatically discover and connect to the UNO Q.
- New nodes should be addable dynamically without rewiring.

2. Wireless Node Requirements
Each node may contain one or more sensors and an ESP32-based controller.

Possible sensors:
- LD2410 mmWave radar → human detection
- PMS5003 → airborne dust / PM detection
- MQ135 → odor / gas sensing
- VL53L0X ToF sensor → object/paper detection
- moisture sensor → wet floor / wet waste detection
- optional IMU → movement/vibration awareness

3. Detection Goals
The system should intelligently infer:
- human presence
- dust accumulation
- airborne particulate level
- odor / bad smell
- wet floor conditions
- wet waste conditions
- paper/wrapper/object presence
- approximate contamination zones
- cleanliness score

The system does NOT need camera vision.

4. Sensor Fusion Logic
The Arduino UNO Q should combine data from multiple sensors instead of relying on single thresholds.

Examples:
- object detected + no human nearby + persistent presence → possible waste
- moisture + odor rise → possible wet waste
- dust rise + no occupancy → dirty environment
- temporary changes during human activity should be ignored

5. Edge Processing
The UNO Q should process data locally before sending summarized insights to the cloud.

Cloud responsibilities:
- dashboards
- notifications
- historical analytics
- trend analysis

Edge responsibilities:
- sensor fusion
- event detection
- adaptive thresholds
- cleanliness scoring
- anomaly detection

6. Adaptive Calibration
The system should self-calibrate to the environment:
- learn baseline dust levels
- learn odor patterns
- detect anomalies dynamically
- support changing environments

7. Networking Requirements
System should support:
- ESP-NOW and/or ESP-MESH
- dynamic node discovery
- automatic node registration
- optional approval-based joining
- scalable mesh-style communication

8. Node Identity and Location Handling
Each node has:
- fixed hardware device ID
- configurable logical location label

Examples:
- Front of Bus
- Coach S3
- Room Corner A
- Under Bed

Location labels are assigned during provisioning/setup and stored in the UNO Q.

System should:
- detect when a known node changes environment
- allow reassignment/recalibration
- avoid unreliable GPS dependence
- avoid camera-based localization

9. Transport/Indoor Use Cases
System should work in:
- homes
- offices
- hospitals
- hostels
- buses
- trains
- multi-room buildings

For buses/trains:
- nodes are fixed relative to the vehicle
- nodes report logical zones (front/middle/back/coach number)
- no GPS dependency required

10. Scalability Goals
The architecture should support:
- multiple nodes
- distributed sensing
- mesh networking
- future integration with robots/vacuum systems
- cloud analytics
- large-area deployments

11. Desired Technical Themes
The project should strongly demonstrate:
- edge computing
- IoT architecture
- distributed wireless sensing
- sensor fusion
- adaptive intelligence
- mesh networking
- scalable deployment
- environmental monitoring

12. Constraints
- low-cost prototype
- compact nodes
- wireless operation
- no camera dependency
- realistic implementation
- competition-grade architecture
- use Arduino UNO Q meaningfully
