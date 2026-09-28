<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Performance Prediction Portal</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            background: #f2f5f9;
            color: #333;
        }

        header {
            background: #2563eb;
            color: white;
            padding: 20px;
            text-align: center;
        }

        nav {
            background: #1e40af;
            padding: 12px;
            text-align: center;
        }

        nav a {
            color: white;
            text-decoration: none;
            margin: 0 15px;
            font-weight: bold;
        }

        .container {
            width: 90%;
            max-width: 900px;
            margin: 30px auto;
        }

        .welcome {
            background: white;
            padding: 25px;
            border-radius: 10px;
            margin-bottom: 20px;
            box-shadow: 0 2px 8px #ccc;
        }

        .prediction-box {
            background: white;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 2px 8px #ccc;
        }

        h2 {
            margin-bottom: 20px;
            color: #1e40af;
        }

        label {
            display: block;
            margin-top: 15px;
            font-weight: bold;
        }

        input, select {
            width: 100%;
            padding: 12px;
            margin-top: 6px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        button {
            width: 100%;
            padding: 13px;
            margin-top: 25px;
            background: #2563eb;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
        }

        button:hover {
            background: #1e40af;
        }

        #result {
            margin-top: 20px;
            padding: 15px;
            background: #e0f2fe;
            border-radius: 5px;
            display: none;
            text-align: center;
            font-weight: bold;
        }

        footer {
            margin-top: 40px;
            background: #1e40af;
            color: white;
            text-align: center;
            padding: 15px;
        }
    </style>
</head>

<body>

    <header>
        <h1>Student Portal</h1>
        <p>Student Performance Prediction System</p>
    </header>

    <nav>
        <a href="#">Home</a>
        <a href="#">Profile</a>
        <a href="#">Prediction</a>
        <a href="#">Contact</a>
    </nav>

    <div class="container">

        <div class="welcome">
            <h2>Welcome Student</h2>
            <p>Enter your academic details below to predict your performance.</p>
        </div>

        <div class="prediction-box">
            <h2>Performance Prediction</h2>

            <form id="predictionForm">

                <label for="name">Student Name</label>
                <input type="text" id="name" placeholder="Enter your name" required>

                <label for="attendance">Attendance (%)</label>
                <input type="number" id="attendance"
                       placeholder="Enter attendance"
                       min="0" max="100" required>

                <label for="marks">Previous Exam Marks (%)</label>
                <input type="number" id="marks"
                       placeholder="Enter marks"
                       min="0" max="100" required>

                <label for="study">Daily Study Hours</label>
                <input type="number" id="study"
                       placeholder="Enter study hours"
                       min="0" max="24" step="0.5" required>

                <label for="assignments">Assignment Completion (%)</label>
                <input type="number" id="assignments"
                       placeholder="Enter completion percentage"
                       min="0" max="100" required>

                <button type="submit">Predict Performance</button>

            </form>

            <div id="result"></div>
        </div>

    </div>

    <footer>
        <p>© 2026 Student Performance Prediction Portal</p>
    </footer>

    <script>
        document.getElementById("predictionForm").addEventListener("submit", function(event) {

            event.preventDefault();

            let name = document.getElementById("name").value;
            let attendance = Number(document.getElementById("attendance").value);
            let marks = Number(document.getElementById("marks").value);
            let study = Number(document.getElementById("study").value);
            let assignments = Number(document.getElementById("assignments").value);

            // Simple demonstration prediction formula
            let score =
                (attendance * 0.25) +
                (marks * 0.40) +
                (Math.min(study * 10, 100) * 0.15) +
                (assignments * 0.20);

            let prediction;

            if (score >= 75) {
                prediction = "Excellent Performance";
            } else if (score >= 60) {
                prediction = "Good Performance";
            } else if (score >= 40) {
                prediction = "Average Performance";
            } else {
                prediction = "Needs Improvement";
            }

            let result = document.getElementById("result");

            result.style.display = "block";

            result.innerHTML =
                "Student: " + name +
                "<br>Predicted Score: " + score.toFixed(2) +
                "<br>Prediction: " + prediction;
        });
    </script>

</body>
</html>
