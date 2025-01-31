<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Result Portal</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Student Result Portal</h1>
        
        <!-- Student Result Check Section -->
        <div class="student-section">
            <h2>Check Your Result</h2>
            <label for="rollNumber">Enter Roll Number:</label>
            <input type="text" id="rollNumber" placeholder="Enter Roll Number">
            <button onclick="checkResult()">Check Result</button>
            
            <div id="result" class="result">
                <h2>Result: <span id="resultMessage"></span></h2>
            </div>
            <div id="errorMessage" class="error"></div>
        </div>

        <!-- Admin Panel to Add Results -->
        <div class="admin-section">
            <h2>Admin Panel</h2>
            <label for="adminRollNumber">Roll Number:</label>
            <input type="text" id="adminRollNumber" placeholder="Enter Roll Number">
            <label for="adminResult">Result (Pass/Fail):</label>
            <input type="text" id="adminResult" placeholder="Enter Result">
            <button onclick="addResult()">Add Result</button>
        </div>
    </div>

    <script>
        // Object to store the results
        let results = {};

        // Function to check result for students
        function checkResult() {
            const rollNumber = document.getElementById('rollNumber').value;
            const resultMessage = document.getElementById('resultMessage');
            const resultDiv = document.getElementById('result');
            const errorMessage = document.getElementById('errorMessage');

            // Clear previous result or error
            errorMessage.innerHTML = '';
            resultDiv.style.display = 'none';

            // Check if the roll number exists in the results object
            if (results[rollNumber]) {
                resultMessage.innerText = results[rollNumber];
                resultDiv.style.display = 'block';
            } else {
                errorMessage.innerHTML = 'Roll number not found. Please try again.';
            }
        }

        // Function to add results from the admin panel
        function addResult() {
            const rollNumber = document.getElementById('adminRollNumber').value;
            const result = document.getElementById('adminResult').value;

            // Validate input
            if (rollNumber && result) {
                results[rollNumber] = result;
                alert('Result added successfully!');

                // Clear the admin input fields
                document.getElementById('adminRollNumber').value = '';
                document.getElementById('adminResult').value = '';
            } else {
                alert('Please enter both roll number and result.');
            }
        }
    </script>
</body>
</html>
