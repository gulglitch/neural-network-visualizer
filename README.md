# Neural Network Visualizer

A browser-based tool for visualizing how neural networks work. Built to help understand forward propagation in feedforward neural networks.

## What is this?

This is a simple interactive visualizer that shows you the structure of a neural network and lets you watch data flow through it in real time. You can adjust the network architecture, change activation functions, and see how values propagate from input to output.

The main goal here was to make something that helps people (including myself) get a better intuition for what happens inside a neural network during a forward pass.

## How it works

The visualizer draws a fully connected feedforward network on a canvas. Each circle represents a neuron, and the lines between them are the weighted connections. When you run a forward pass, you can actually watch the signal move through the network layer by layer.

Colors indicate the sign and magnitude of values:
- Green means positive
- Red means negative
- Brighter/thicker lines mean stronger weights

The network takes 4 inputs and produces 2 outputs. You control how many hidden layers sit between them and how many neurons each hidden layer contains.

## Features

**Adjustable Architecture**
- Set anywhere from 1 to 5 hidden layers
- Each hidden layer can have 2 to 12 neurons
- Network rebuilds automatically when you change these

**Activation Functions**
- Tanh
- ReLU
- Sigmoid
- Linear

Pick whichever one you want from the dropdown. The forward pass will use that function at every neuron.

**Animated Forward Pass**
When you click "Run Forward Pass", the visualizer:
1. Sets random binary values (0 or 1) at the input layer
2. Lights up the connections going into each layer
3. Computes the weighted sum plus bias at each neuron
4. Applies the activation function
5. Shows a glow effect as each neuron activates

This happens layer by layer so you can follow the computation.

**Weight Randomization**
Click "Randomize Weights" to get a new set of random weights and biases. Weights are initialized between -1 and 1.

**Hover Tooltips**
Move your mouse over any neuron to see its current value and bias. Hover over a connection line to see its weight.

## How to use it

1. Open `index.html` in a web browser
2. Adjust the sliders to set your network size
3. Pick an activation function
4. Click "Run Forward Pass" to watch the network compute
5. Hover over neurons and connections to inspect values

No installation or build step needed. It runs entirely in the browser.

## Technical details

Everything is in a single HTML file. The visualization uses the Canvas API for drawing. The neural network logic is implemented from scratch in plain JavaScript.

The network is represented as arrays of Neuron and Connection objects. Each neuron stores its value, bias, and position on screen. Each connection stores its weight and references to the neurons it connects.

Forward propagation works by iterating through layers in order. For each neuron in a layer, it sums up (input value * weight) for all incoming connections, adds the bias, and applies the activation function.

The animation loop runs continuously using requestAnimationFrame. Glow effects decay over time to create smooth transitions.

## File structure

```
index.html    - Everything is here (HTML, CSS, JavaScript)
README.md     - This file
```

## Browser support

Tested on Chrome and Firefox. Should work on any modern browser that supports Canvas and ES6 JavaScript.

## Notes

The input and output sizes are fixed at 4 and 2 respectively. This was just a design choice to keep things simple. The hidden layer configuration is where you have flexibility.

The tooltips can be a bit finicky on the connection lines since they are thin. You might need to move slowly to catch them.

## License

Do whatever you want with this code.
