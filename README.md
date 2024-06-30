<div align="left">
  <img src="https://github.com/Dalageo/TwinCAT-VirtualAGV/assets/153513781/498163f4-35a1-45b9-a442-9889c5e9966e" alt="Bechoff TwinCat" width="700"/>
</div>

<div align="left">
  <a href="https://www.beckhoff.com/en-en/products/automation/twincat/" target="_blank">
    <img src="https://img.shields.io/badge/TwinCAT-3.1.4024.55-blue" alt="TwinCAT 3.1.4024.55"></a>
  <a href="https://github.com/Dalageo/TwinCAT-VirtualAGV/blob/main/LICENSE" target="_blank">
    <img src="https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey" alt="License: CC BY-NC-SA 4.0"></a>
  <img src="https://img.shields.io/github/stars/Dalageo/TwinCat-VirtualAGV?style=social" alt="GitHub stars">
</div>

# Simulating an Automatic Guided Vehicle (AGV) with Handshake Communication Protocol Using TwinCAT PLC Programming

This repository contains a simulation project for an Automatic Guided Vehicle (AGV), developed within the <a href="https://www.beckhoff.com/en-en/products/automation/twincat/"> TwinCAT </a> environment as part of a master's course assignment <a href="https://www.hv.se/en/">University West</a>. The assignment involves developing a Human-Machine Interface (HMI) that controls the operation of the AGV by following the specified handshake protocol between the PLC and the AGV. In this project, `AGVSimulator.TcVIS` visualization, `AGV.TcPOU` Function Block, and `Process.TcPOU` were provided by the university. The designed Virtual AGV includes the following functionalities:

- **Target Selection and Start**: The target location is selected from a drop-down menu on the HMI (PosA, PosB, PosC, PosD, and HOME), and movement is initiated by pressing the Start button. During AGV movement, the target selection is locked and the Start button is disabled to prevent changes or reinitiations.
- **Indicator Lamps**: The Ready Lamp lights up when the AGV is ready for its next movement, the Stop Lamp lights up when the AGV is stopped, and the Moving Lamp blinks during AGV movement.
- **Position Display**: The AGV's current position is shown on the HMI while it is stationary at a target location, whereas the display is invisible when the AGV is moving.
- **Stop and Reset Functionality**: The AGV's movement can be stopped by pressing the Stop button on the HMI. To resume operation after a stop, the Reset button must be pressed, which will return the AGV to its HOME position.

| AGV | HMI |
|-----|-----|
| ![AGV](https://github.com/Dalageo/TwinCAT-VirtualAGV/assets/153513781/330c0a75-f7f4-4bd9-9569-b344b3bb36ab) | ![HMI](https://github.com/Dalageo/TwinCAT-VirtualAGV/assets/153513781/77c44aff-69eb-4aa5-99f0-79cd7a449320) |


## AGV Communication Protocol
The AGV movement is enabled by a specific handshake protocol between the PLC and the AGV, as shown in the following diagram:
<div align="left">
  <img src="https://github.com/Dalageo/TwinCAT-VirtualElevator/assets/153513781/6bff5260-af2c-4dde-8354-e4f227e98b29" alt="HandshakeProtocol" width="700"/>
</div>

1. **Order Sending**: The PLC sets the target position and raises the PLC strobe signal to send an order to the AGV.
2. **Order Received**: The AGV reads the order and acknowledges receipt by raising the AGV strobe signal and setting the answer to 0.
3. **Send Ready Signal**: The PLC lowers the PLC strobe signal, indicating that it is ready for the AGV to proceed.
4. **AGV Movement Initiation**: The AGV lowers the AGV strobe signal (acknowledge strobe) and starts moving to the target position.
5. **Answer Ready**: Once the AGV reaches the target position, it raises the AGV strobe signal again and sets the answer to indicate its current position.
6. **Answer Received**: The PLC acknowledges receipt of the answer by raising the PLC strobe signal and setting the order to 0.
7. **Order Completion**: The AGV completes the handshake by lowering the AGV strobe signal (answer end) and waits for the next order.

## Setup Instructions

1. **Download and Install:**
   [TwinCAT 3 download | eXtended Automation Engineering (XAE)](https://www.beckhoff.com/en-en/support/download-finder/search-result/?download_group=97028248&download_item=650023470)
   
2. **Clone the repository:**
   ```sh
   git clone https://github.com/Dalageo/TwinCAT-VirtualAGV.git
   
3. **Navigate to the cloned directory and execute the `TwinCAT Virtual AGV.sln` solution file.**

4. **Navigate to TwinCAT directory and execute Start.bat**:
   ```sh
   C:/TwinCAT/3.1/Runtimes/UmRT_Default/Start.bat

5. **Change the Target System in TwinCAT to UmRT_Default.**
   
6. **Visualization Image Pool Setup**:
    - In the Solution Explorer of `TwinCAT Virtual AGV.sln`, navigate to PLCStudent's VISUs and click on the `Display.TcIPO` Image Pool.
    - Set the correct file path for the image ID by navigating to the cloned directory: TwinCAT-VirtualAGV/Image Pool/Display.png.
       
7. **Activate Configuration.**
   
8. **Login and Start both 'PLCSim' and 'PLCStudent'.**
  
## Contributions

This project was part of a master course assignment at [University West](https://www.hv.se/en/), which provided the `AGVSimulator.TcVIS` visualization, `AGV.TcPOU Function Block`, and `Process.TcPOU`. Special thanks to the professors at University West who contributed to its development.

## License

This work is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-nc-sa/4.0/). It was chosen to prevent commercial use and to promote free access and open collaboration, ensuring any adaptations remain freely available to everyone.

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg

## Citation

```bibtex
@software{Dalageorgos_TwinCAT-VirtualAGV_2024,
author = {Dalageorgos, Konstantinos},
license = {CC-BY-NC-SA-4.0},
month = jun,
title = {{TwinCAT-VirtualAGV}},
url = {https://github.com/Dalageo/TwinCAT-VirtualAGV},
version = {1.0.0},
year = {2024}
}
