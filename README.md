# Ex06 BMI Calculator
## Date: 29-05-2025

## AIM
To develop a responsive and interactive Body Mass Index (BMI) Calculator using React that allows users to input their height and weight, and calculates their BMI to categorize their health status (e.g., Underweight, Normal, Overweight, Obese).

## DESIGN STEPS

### STEP 1: Initialize React Project

<li>Create a new React app using create-react-app.</li>
<li>Install React Router using:</li>
npm install react-router-dom

### STEP 2: Set Up Routing

Create routing structure with react-router-dom:

<li>Home route (/) – Intro or Navigation</li>

<li>BMI Calculator route (/bmi)</li>

<li>Result route (/result)</li>

### STEP 3: Design the BMI Form Page

<li>Create a form to accept Height (in cm or m) and Weight (in kg).</li>

<li>On form submit, navigate to the result page with entered values via URL query params or context/state.</li>

## STEP 4: Handle Input Validation

<li>Check if height and weight are valid numbers.</li>

<li>Optionally, show error messages for invalid inputs.</li>

### STEP 5: Perform BMI Calculation

<li>In the result component:

<li>Extract height and weight from the route (URL or passed state).</li>

<li>Apply the BMI formula:</li>

![image](https://github.com/user-attachments/assets/ec785506-c96b-489e-8783-fb1a5d36101a)
​
 
<li>Convert height from cm to m if needed.</li></li>

### STEP 6: Display Result

<li>Show calculated BMI.</li>

<li>Show category based on BMI range:

<li>Underweight, Normal, Overweight, Obese, etc.</li></li>

### STEP 7: Navigation Options

<li>Provide a button to go back to the BMI form to calculate again.</li>

### STEP 8: Enhancements

<li>Add styling using CSS or Tailwind.</li>

## PROGRAM

### App.jsx
```
import { useState } from "react";
import "./App.css";

function App() {
  const [height, setHeight] = useState("");
  const [weight, setWeight] = useState("");
  const [bmi, setBmi] = useState("");
  const [status, setStatus] = useState("");

  const calculateBMI = () => {
    const h = height / 100;
    const result = (weight / (h * h)).toFixed(2);

    setBmi(result);

    if (result < 18.5) setStatus("Underweight");
    else if (result < 24.9) setStatus("Normal");
    else if (result < 29.9) setStatus("Overweight");
    else setStatus("Obese");
  };

  return (
    <div className="container">
      <h1>BMI Calculator</h1>

      <input
        type="number"
        placeholder="Enter Height (cm)"
        onChange={(e) => setHeight(e.target.value)}
      />

      <input
        type="number"
        placeholder="Enter Weight (kg)"
        onChange={(e) => setWeight(e.target.value)}
      />

      <button onClick={calculateBMI}>
        Calculate
      </button>

      <h2>BMI: {bmi}</h2>
      <h3>{status}</h3>
    </div>
  );
}

export default App;
```

## App.css
```
body {
  margin: 0;
  font-family: Arial;
  background: #f0f4f8;
}

.container {
  width: 400px;
  margin: 100px auto;
  text-align: center;
  background: white;
  padding: 30px;
  border-radius: 15px;
  box-shadow: 0 0 20px gray;
}

input {
  width: 90%;
  padding: 12px;
  margin: 10px;
}

button {
  padding: 12px 25px;
  background: blue;
  color: white;
  border: none;
  cursor: pointer;
}

h2, h3 {
  margin-top: 20px;
}
```

### index.css
```
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: linear-gradient(135deg, #6a11cb, #2575fc);
  height: 100vh;
}

.container {
  width: 400px;
  margin: 80px auto;
  text-align: center;
  background: white;
  padding: 30px;
  border-radius: 20px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.3);
}

h1 {
  color: #2575fc;
}

input {
  width: 90%;
  padding: 14px;
  margin: 12px;
  border: 2px solid #2575fc;
  border-radius: 10px;
  font-size: 16px;
}

button {
  padding: 14px 30px;
  background: #2575fc;
  color: white;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  font-size: 16px;
}

button:hover {
  background: #6a11cb;
}

h2 {
  color: #222;
}

h3 {
  color: green;
}
```


## OUTPUT

<img width="1289" height="845" alt="image" src="https://github.com/user-attachments/assets/068682e1-9444-4e41-9f2f-e1099150d5a0" />



## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.
