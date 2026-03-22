# Ex06 BMI Calculator
## Date: 19.03.26

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

# App.js
```
import { useState } from "react";
import "./App.css";

function App() {
  const [height, setHeight] = useState("");
  const [weight, setWeight] = useState("");
  const [bmi, setBmi] = useState(null);
  const [message, setMessage] = useState("");

  const calculateBMI = () => {
    if (height === "" || weight === "") {
      alert("Please enter both height and weight");
      return;
    }

    const h = height / 100;
    const calc = weight / (h * h);
    setBmi(calc.toFixed(2));

    if (calc < 18.5) setMessage("Underweight");
    else if (calc >= 18.5 && calc < 24.9) setMessage("Normal weight");
    else if (calc >= 25 && calc < 29.9) setMessage("Overweight");
    else setMessage("Obesity");
  };

  return (
    <div className="container">
      <h1>BMI Calculator</h1>

      <div className="input-group">
        <label>Height (cm)</label>
        <input
          type="number"
          placeholder="Enter height"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
        />
      </div>

      <div className="input-group">
        <label>Weight (kg)</label>
        <input
          type="number"
          placeholder="Enter weight"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
        />
      </div>

      <button onClick={calculateBMI}>Calculate BMI</button>

      {bmi && (
        <div className="result">
          <h2>Your BMI: {bmi}</h2>
          <p>{message}</p>
        </div>
      )}

      <footer>
        <p>Created by: YOUR NAME – REGISTER NUMBER</p>
      </footer>
    </div>
  );
}

export default App;
```

# App.css

```
body {
  background: #f2f2f2;
  font-family: Arial, Helvetica, sans-serif;
}

.container {
  max-width: 400px;
  margin: 50px auto;
  padding: 25px;
  background: #fff;
  border-radius: 10px;
  box-shadow: 0px 0px 10px #ccc;
  text-align: center;
}

.input-group {
  margin-bottom: 20px;
  text-align: left;
}

label {
  font-weight: bold;
}

input {
  width: 100%;
  padding: 10px;
  margin-top: 8px;
  border: 1px solid #999;
  border-radius: 5px;
}

button {
  width: 100%;
  padding: 12px;
  background: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
}

button:hover {
  background: #0056b3;
}

.result {
  margin-top: 20px;
  background: #e9ffe9;
  padding: 15px;
  border-radius: 5px;
}

footer {
  margin-top: 30px;
  font-size: 14px;
  color: #555;
}
```

## OUTPUT

<img width="1004" height="780" alt="exp6" src="https://github.com/user-attachments/assets/021fac40-cc07-44b1-8838-a2b8d77ce06c" />

## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.
