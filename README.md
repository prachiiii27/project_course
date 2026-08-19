# AI-Powered Robotic Tutor for Circuit Learning

An interactive robotic tutoring system that combines **Computer Vision, Large Language Models (LLMs), Speech Interaction, and Robotic Arm Gestures** to provide students with an engaging way to learn basic electronics.

The current implementation focuses on **voltage divider circuits**. The system can observe a circuit through a camera, identify the circuit, provide an explanation through speech, and use robotic-arm gestures to visually demonstrate the explanation.

---

## 📌 Project Overview

The project integrates three major modules:

1. **LLM-Based Tutor** – generates explanations and conversational responses.
2. **Robotic Arm Gesture Module** – converts predefined teaching actions into physical arm movements.
3. **Computer Vision Module** – observes and identifies the target circuit configuration.

These modules are integrated into a single tutoring pipeline:

```text
                ┌──────────────────┐
                │      Student     │
                │ Voice / Circuit  │
                └────────┬─────────┘
                         │
             ┌───────────▼───────────┐
             │   Computer Vision     │
             │  Circuit Detection    │
             └───────────┬───────────┘
                         │
                         ▼
             ┌───────────────────────┐
             │   Tutor / LLM Logic  │
             │ Explanation & Decision│
             └───────────┬───────────┘
                         │
              ┌──────────┴──────────┐
              ▼                     ▼
       ┌─────────────┐       ┌─────────────┐
       │    Speech   │       │ Robotic Arm │
       │    Output   │       │   Gestures  │
       └─────────────┘       └─────────────┘
```

---

## 🎯 Objectives

* Develop an interactive robotic tutor for electronics education.
* Detect a voltage divider circuit using computer vision.
* Provide concept explanations using an LLM.
* Convert explanations into speech for the student.
* Use robotic-arm gestures to reinforce important concepts visually.
* Integrate independent software modules into a single real-time system.

---

## 🧠 System Modules

### 1. Computer Vision / Circuit Detection

The vision module processes the camera input and determines whether the required circuit configuration is present.

Current target:

* Voltage divider circuit
* Resistor arrangement
* Circuit configuration

Typical pipeline:

```text
Camera
   ↓
Image Acquisition
   ↓
Pre-processing
   ↓
Feature / Component Detection
   ↓
Circuit Identification
   ↓
Result → Tutor Module
```

The vision system is intended to provide the tutoring system with information about the physical circuit rather than relying only on verbal input.

---

### 2. LLM Tutor

The LLM acts as the reasoning and tutoring layer of the system.

It is responsible for:

* Understanding the student's question.
* Explaining circuit concepts.
* Providing step-by-step guidance.
* Generating natural-language responses.
* Selecting appropriate tutoring responses based on the detected circuit.

The intended interaction is:

```text
Student Question
      ↓
Speech / Text Input
      ↓
Tutor Logic
      ↓
LLM
      ↓
Generated Explanation
      ↓
Speech Output + Gesture
```

---

### 3. Speech Interaction

Speech provides the natural interface between the student and the tutor.

```text
Student Voice
     ↓
Speech-to-Text
     ↓
Tutor / LLM
     ↓
Text Response
     ↓
Text-to-Speech
     ↓
Robot Voice
```

This allows the system to function as a conversational tutor rather than only displaying information on a screen.

---

### 4. Robotic Arm Gesture Module

The robotic arm is used as a **physical teaching interface**.

Instead of only verbally explaining a concept, the robot can perform predefined gestures corresponding to different tutoring actions.

Examples include:

* Pointing toward a circuit/component
* Demonstrating a teaching action
* Moving to predefined presentation poses
* Returning to a safe/rest position

The project uses the Elephant Robotics robotic platform. The manufacturer's documentation provides Python interfaces for joint and coordinate control, along with separate arm/waist control capabilities.

The available documentation also includes Python interfaces for joint control, coordinate control, IO control, gripper control, and TCP/IP communication.

---

## 🔗 Integrated Workflow

The complete tutoring sequence is:

```text
1. Student presents circuit
              ↓
2. Camera captures circuit
              ↓
3. Vision module detects circuit
              ↓
4. Circuit information sent to tutor
              ↓
5. LLM determines appropriate explanation
              ↓
6. Explanation converted to speech
              ↓
7. Appropriate robotic gesture selected
              ↓
8. Robot speaks + performs gesture
              ↓
9. Student receives multimodal explanation
```

The goal is to combine:

**Seeing + Understanding + Speaking + Demonstrating**

into one tutoring system.

---

## ⚡ Example: Voltage Divider

For a voltage divider, the system can identify the circuit and guide the student through concepts such as:

* Input voltage
* Resistors
* Output voltage
* Voltage division
* Relationship between resistor values and output voltage

The standard voltage-divider relationship is:

```text
Vout = Vin × R2 / (R1 + R2)
```

The robot can accompany the explanation with a predefined gesture to make the explanation more intuitive.

---


## 🛠️ Technologies

| Component       | Technology                      |
| --------------- | ------------------------------- |
| Programming     | Python                          |
| Computer Vision | OpenCV                          |
| AI Tutor        | LLM                             |
| Speech          | Speech-to-Text / Text-to-Speech |
| Robotics        | Elephant Robotics platform      |
| Robot Control   | Python robot interface          |
| Version Control | Git / GitHub                    |

The robotic platform documentation states that myBuddy provides Python control interfaces and visual-development support, including an OpenCV development environment.

---


## 🤖 Robot Setup

Connect the robotic system to the computer and verify the communication interface.

The exact robot configuration depends on the hardware version being used.

The Elephant Robotics documentation provides separate interfaces for joint control and coordinate control, which can be used as the basis for implementing predefined teaching gestures.

Before running the complete system:

1. Verify robot power.
2. Establish communication with the robot.
3. Test individual arm movements.
4. Test predefined gestures.
5. Test the vision module.
6. Test speech independently.
7. Run the integrated tutor.

---

## ▶️ Running the Project

After completing the setup:

```bash
python main.py
```

If the project uses separate modules during development, they can be tested independently before running the integrated system.

---

## 🧪 Development and Testing

The system should be tested at three levels:

### Module-Level Testing

Each subsystem is tested independently:

```text
Vision ────────→ Circuit Detection
LLM ───────────→ Response Generation
Speech ────────→ Audio Input/Output
Robot ─────────→ Gesture Execution
```

### Integration Testing

The modules are tested together:

```text
Vision → Tutor → Speech
              ↓
            Robot
```

### End-to-End Testing

The complete interaction is tested:

```text
Student
   ↓
Circuit
   ↓
Camera
   ↓
Detection
   ↓
Tutor
   ↓
Speech + Gesture
```

---

## ⚠️ Current Limitations

* Current circuit recognition is focused on a limited set of circuit configurations.
* Vision performance can depend on camera position, lighting, background, and circuit arrangement.
* Robotic gestures are currently predefined rather than dynamically generated.
* LLM-generated explanations depend on the quality of prompts and available model capabilities.
* The complete system depends on reliable communication between independent modules.
* Real-time performance may vary depending on hardware and network/API latency.

---

## 🚀 Future Scope

### Computer Vision

* Expand recognition to multiple circuit types.
* Detect individual electronic components.
* Identify incorrect connections.
* Estimate component values from visual information.
* Improve robustness under different lighting and circuit layouts.

### Robotic Interaction

* Generate context-dependent gestures automatically.
* Add more teaching gestures.
* Improve gesture timing and synchronization with speech.
* Introduce more advanced robot motion planning.

### AI Tutor

* Develop a structured electronics knowledge base.
* Improve context retention during tutoring sessions.
* Adapt explanations to the student's level.
* Add interactive questioning and assessment.

### System Integration

* Support more electronics experiments.
* Develop a complete laboratory tutoring workflow.
* Add student progress tracking.
* Enable multimodal interaction using voice, vision, and physical demonstration.

---

## 📚 Hardware Reference

The robotic platform used in this project is based on the Elephant Robotics **myBuddy** platform.

The manufacturer's documentation describes myBuddy as an open robotic platform with Python control interfaces, separate control of the left/right arms and waist, camera support, and visual development capabilities.

---

## 👥 Project Contributions

| Module      | Contribution                                                        |
| ----------- | ------------------------------------------------------------------- |
| LLM & Tutor | LLM integration, prompting, tutoring logic and speech interaction   |
| Robotic Arm | Gesture design, arm control and gesture execution                   |
| Vision      | Circuit detection, image processing and voltage-divider recognition |
| Integration | Communication between modules and complete end-to-end workflow      |

---

## 📌 Project Status

**Current prototype:** Integrated robotic tutor capable of detecting a target voltage-divider circuit and providing a multimodal tutoring response through speech and robotic-arm gestures.

Further development is focused on increasing circuit-recognition capabilities, improving adaptive tutoring, and expanding robotic teaching gestures.

---


---

## 🙏 Acknowledgements

* Elephant Robotics for the robotic platform and documentation.
* Open-source Python and computer-vision libraries used in the project.
* LLM and speech technologies used to implement the tutoring interface.
