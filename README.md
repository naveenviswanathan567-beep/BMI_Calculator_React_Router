# Ex06 BMI Calculator
### NAME : NAVEEN.V 
### REGISTER NO: 212225240098

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
App.css
```
* {
  box-sizing: border-box;
}

body {
  margin: 0;

  font-family:
    Arial,
    Helvetica,
    sans-serif;

  background:
    linear-gradient(
      135deg,
      #e8f5e9,
      #e3f2fd
    );

  color: #222;
}

/* Main page */

.bmi-page {
  min-height: 100vh;

  display: flex;

  flex-direction: column;

  align-items: center;

  justify-content: center;

  padding: 30px 20px;
}

/* Card */

.bmi-card {
  width: 430px;

  max-width: 100%;

  padding: 35px;

  background: white;

  border-radius: 22px;

  box-shadow:
    0 15px 45px
    rgba(0, 0, 0, 0.12);

  animation:
    cardAppear 0.6s ease;
}

@keyframes cardAppear {

  from {
    opacity: 0;

    transform:
      translateY(25px);
  }

  to {
    opacity: 1;

    transform:
      translateY(0);
  }
}

/* Header */

.header {
  text-align: center;

  margin-bottom: 30px;
}

.icon {
  width: 60px;
  height: 60px;

  margin: 0 auto 15px;

  display: flex;

  align-items: center;
  justify-content: center;

  border-radius: 50%;

  background: #e8f5e9;

  font-size: 30px;
}

.header h1 {
  margin: 0;

  font-size: 30px;

  color: #222;
}

.header p {
  margin-top: 8px;

  color: #777;

  font-size: 14px;
}

/* Input */

.input-group {
  margin-bottom: 20px;
}

.input-group label {
  display: block;

  margin-bottom: 8px;

  font-size: 14px;

  font-weight: bold;

  color: #444;
}

.input-box {
  display: flex;

  align-items: center;

  border: 1px solid #ddd;

  border-radius: 10px;

  overflow: hidden;

  transition:
    border-color 0.3s,
    box-shadow 0.3s;
}

.input-box:focus-within {
  border-color: #4caf50;

  box-shadow:
    0 0 0 3px
    rgba(76, 175, 80, 0.12);
}

.input-box input {
  flex: 1;

  padding: 14px;

  border: none;

  outline: none;

  font-size: 16px;
}

.input-box input::placeholder {
  color: #aaa;
}

.input-box span {
  padding: 0 15px;

  color: #777;

  font-size: 14px;
}

/* Remove number arrows */

input::-webkit-inner-spin-button,
input::-webkit-outer-spin-button {
  -webkit-appearance: none;

  margin: 0;
}

input[type="number"] {
  appearance: textfield;
}

/* Buttons */

.button-group {
  display: flex;

  gap: 10px;

  margin-top: 10px;
}

.calculate-btn,
.reset-btn {
  flex: 1;

  padding: 14px;

  border: none;

  border-radius: 10px;

  font-size: 15px;

  font-weight: bold;

  cursor: pointer;

  transition:
    transform 0.2s,
    box-shadow 0.2s;
}

.calculate-btn {
  background: #4caf50;

  color: white;
}

.calculate-btn:hover {
  background: #43a047;

  transform: translateY(-2px);

  box-shadow:
    0 7px 18px
    rgba(76, 175, 80, 0.3);
}

.reset-btn {
  background: #eeeeee;

  color: #444;
}

.reset-btn:hover {
  background: #e0e0e0;

  transform: translateY(-2px);
}

/* Result */

.result {
  margin-top: 25px;

  padding: 25px;

  text-align: center;

  background: #f8fff8;

  border-radius: 15px;

  animation:
    resultAppear 0.5s ease;
}

@keyframes resultAppear {

  from {
    opacity: 0;

    transform: scale(0.9);
  }

  to {
    opacity: 1;

    transform: scale(1);
  }
}

.result-title {
  margin: 0;

  color: #777;

  font-size: 14px;
}

.bmi-value {
  margin: 8px 0;

  font-size: 48px;

  font-weight: bold;

  color: #222;
}

.category {
  display: inline-block;

  padding: 8px 18px;

  border-radius: 20px;

  font-size: 14px;

  font-weight: bold;
}

/* Category colors */

.category.underweight {
  background: #e3f2fd;

  color: #1976d2;
}

.category.normal-weight {
  background: #e8f5e9;

  color: #2e7d32;
}

.category.overweight {
  background: #fff3e0;

  color: #ef6c00;
}

.category.obese {
  background: #ffebee;

  color: #c62828;
}

/* Information */

.info {
  margin-top: 25px;

  padding-top: 20px;

  border-top: 1px solid #eee;
}

.info h2 {
  margin: 0 0 15px;

  font-size: 17px;

  color: #333;
}

.category-row {
  display: flex;

  justify-content: space-between;

  padding: 9px 0;

  border-bottom: 1px solid #f0f0f0;

  color: #666;

  font-size: 13px;
}

.category-row:last-child {
  border-bottom: none;
}

/* Footer */

.footer {
  margin-top: 25px;

  text-align: center;

  color: #777;

  font-size: 12px;
}

.footer p {
  margin: 5px 0;
}

.footer strong {
  color: #444;
}

/* Mobile */

@media (max-width: 500px) {

  .bmi-page {
    padding: 20px 15px;
  }

  .bmi-card {
    padding: 25px 20px;
  }

  .header h1 {
    font-size: 26px;
  }

  .button-group {
    flex-direction: column;
  }

  .calculate-btn,
  .reset-btn {
    width: 100%;
  }
}
```
App.jsx
```
import { useState } from "react";
import "./App.css";

function App() {
  const [height, setHeight] = useState("");
  const [weight, setWeight] = useState("");
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState("");

  const calculateBMI = () => {
    const heightInCm = parseFloat(height);
    const weightInKg = parseFloat(weight);

    if (
      !heightInCm ||
      !weightInKg ||
      heightInCm <= 0 ||
      weightInKg <= 0
    ) {
      setBmi(null);
      setCategory("");
      alert("Please enter a valid height and weight.");
      return;
    }

    const heightInMeters = heightInCm / 100;

    const bmiValue =
      weightInKg /
      (heightInMeters * heightInMeters);

    const roundedBMI = bmiValue.toFixed(1);

    setBmi(roundedBMI);

    if (bmiValue < 18.5) {
      setCategory("Underweight");
    } else if (bmiValue < 25) {
      setCategory("Normal Weight");
    } else if (bmiValue < 30) {
      setCategory("Overweight");
    } else {
      setCategory("Obese");
    }
  };

  const resetCalculator = () => {
    setHeight("");
    setWeight("");
    setBmi(null);
    setCategory("");
  };

  return (
    <div className="bmi-page">

      <div className="bmi-card">

        <div className="header">
          <div className="icon">⚖</div>

          <h1>BMI Calculator</h1>

          <p>
            Calculate your Body Mass Index
          </p>
        </div>

        {/* Height */}

        <div className="input-group">

          <label htmlFor="height">
            Height
          </label>

          <div className="input-box">

            <input
              id="height"
              type="number"
              placeholder="Enter your height"
              value={height}
              onChange={(e) =>
                setHeight(e.target.value)
              }
              min="1"
            />

            <span>cm</span>

          </div>

        </div>

        {/* Weight */}

        <div className="input-group">

          <label htmlFor="weight">
            Weight
          </label>

          <div className="input-box">

            <input
              id="weight"
              type="number"
              placeholder="Enter your weight"
              value={weight}
              onChange={(e) =>
                setWeight(e.target.value)
              }
              min="1"
            />

            <span>kg</span>

          </div>

        </div>

        {/* Buttons */}

        <div className="button-group">

          <button
            className="calculate-btn"
            onClick={calculateBMI}
          >
            Calculate BMI
          </button>

          <button
            className="reset-btn"
            onClick={resetCalculator}
          >
            Reset
          </button>

        </div>

        {/* Result */}

        {bmi !== null && (

          <div className="result">

            <p className="result-title">
              Your BMI
            </p>

            <div className="bmi-value">
              {bmi}
            </div>

            <div
              className={`category ${category
                .toLowerCase()
                .replace(" ", "-")}`}
            >
              {category}
            </div>

          </div>

        )}

        {/* BMI Information */}

        <div className="info">

          <h2>BMI Categories</h2>

          <div className="category-row">
            <span>Underweight</span>
            <span>Below 18.5</span>
          </div>

          <div className="category-row">
            <span>Normal Weight</span>
            <span>18.5 – 24.9</span>
          </div>

          <div className="category-row">
            <span>Overweight</span>
            <span>25 – 29.9</span>
          </div>

          <div className="category-row">
            <span>Obese</span>
            <span>30 or above</span>
          </div>

        </div>

      </div>

      {/* Footer */}

      <footer className="footer">

        <p>
          Designed by:
          <strong> ANISE KINSELLA A.</strong>
        </p>

        <p>
          Register Number:
          <strong> 212225040021</strong>
        </p>

      </footer>

    </div>
  );
}

export default App;
```
main.jsx
```
import React from "react";
import ReactDOM from "react-dom/client";

import App from "./App";

import "./index.css";

ReactDOM.createRoot(
  document.getElementById("root")
).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```
index.css
```
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html,
body,
#root {
  min-height: 100%;
  width: 100%;
}
```

## OUTPUT


<img width="1046" height="692" alt="Screenshot 2026-09-14 182553" src="https://github.com/user-attachments/assets/a463eb37-744a-4173-9ea1-dda2355b7d8e" />


## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.
