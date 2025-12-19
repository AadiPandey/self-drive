# Self-Driving Car Simulation

A JavaScript-based self-driving car simulation using neural networks and genetic algorithms. The project implements a complete AI system with no external libraries, featuring real-time visualization of both the car's behavior and its neural network decision-making process.

## 🚗 Features

- **Neural Network AI**: Cars learn to navigate traffic using a custom-built neural network
- **Genetic Algorithm**: Population of 1000 cars with mutation-based learning
- **Real-time Visualization**: Live display of neural network activity
- **Sensor System**: Ray-casting sensors detect road borders and traffic
- **Collision Detection**: Polygon-based collision detection system
- **Persistent Training**: Save and load the best-performing neural network
- **Traffic System**: Dynamic traffic obstacles with random colors

## 🎮 How It Works

### Neural Network Architecture
- **Input Layer**: Sensor rays detecting obstacles
- **Hidden Layer**: 6 neurons processing sensor data
- **Output Layer**: 4 neurons controlling movement (↑, ←, →, ↓)

### Learning Process
1. 1000 AI-controlled cars start simultaneously
2. Each car uses a neural network to make driving decisions
3. The best-performing car (travels farthest) is tracked
4. Save the best brain to continue training from that point
5. New generations mutate from the saved brain with 10% variation

## 🚀 Getting Started

### Prerequisites
- A modern web browser (Chrome, Firefox, Safari, Edge)
- Local web server (optional, but recommended)

### Installation

1. Clone or download the repository
2. Open `index.html` in your browser, or
3. Use a local server:
   ```bash
   # Using Python 3
   python -m http.server 8000
   
   # Using Node.js (with http-server)
   npx http-server
   ```
4. Navigate to `http://localhost:8000`

## 🎯 Usage

### Controls
- **💾 Save Button**: Save the best-performing neural network to browser storage
- **🗑️ Discard Button**: Delete saved neural network and start fresh

### Training Tips
1. Let the simulation run until most cars crash
2. Save the best brain using the save button
3. Refresh the page - the saved brain will load with mutations
4. Repeat the process to improve performance over time

## 📁 Project Structure

```
self_driver/
├── index.html          # Main HTML file
├── style.css           # Styling for canvas and UI
├── main.js             # Entry point, animation loop
├── car.js              # Car class with physics and rendering
├── controls.js         # Input handling (keyboard/AI)
├── sensor.js           # Ray-casting sensor system
├── network.js          # Neural network implementation
├── visualiser.js       # Neural network visualization
├── road.js             # Road rendering and boundaries
├── utils.js            # Utility functions (lerp, intersection, etc.)
└── car.png             # Car sprite image
```

## 🔧 Technical Details

### Car Physics
- Acceleration: 0.2 units/frame
- Max speed: 3 units/frame (AI cars), 2 units/frame (traffic)
- Friction: 0.05 units/frame
- Steering: 0.03 radians per frame

### Neural Network
- **Type**: Feedforward neural network
- **Activation**: Custom threshold-based activation
- **Mutation Rate**: 10% linear interpolation
- **Training Method**: Parallel genetic algorithm

### Sensor System
- Ray count: Configurable (default in network architecture)
- Ray length: Detects road borders and traffic
- Ray spread: Full frontal arc coverage

## 🎨 Customization

### Adjust Car Population
In `main.js`, change the value of `N`:
```javascript
const N = 1000; // Change to desired number
```

### Modify Mutation Rate
In `main.js`, adjust the mutation parameter:
```javascript
NeuralNetwork.mutate(cars[i].brain, 0.1); // Change 0.1 to desired rate
```

### Change Traffic Patterns
Edit the `traffic` array in `main.js` to add/remove obstacles:
```javascript
const traffic = [
    new Car(road.getLaneCenter(1), -100, 30, 50, "DUMMY", 2, getRandomColor()),
    // Add more traffic cars here
];
```

## 🧠 How the Neural Network Works

1. **Input**: Sensor readings from ray-casting (distances to obstacles)
2. **Processing**: 
   - Inputs are multiplied by weights
   - Biases are added
   - Activation function determines output
3. **Output**: Four control signals (forward, left, right, backward)
4. **Learning**: Genetic algorithm selects best performer and mutates it

## 📊 Performance

- Runs at 60 FPS on modern hardware
- Handles 1000+ simultaneous car instances
- Real-time neural network visualization
- Efficient collision detection using polygon intersection

## 📝 License

This project is open source and available for educational purposes.