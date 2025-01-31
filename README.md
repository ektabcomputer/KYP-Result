<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Student Result Portal allows students to check their exam results by entering their roll number. Admin can also update results through the admin panel.">
    <title>Student Result Portal</title>
    <style>
        /* Styles for the description section */
        .description {
            background-color: #f9f9f9;
            padding: 20px;
            margin: 20px 0;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        .description h2 {
            color: #333;
        }

        .description p {
            font-size: 1.2rem;
            color: #666;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Student Result Portal</h1>

        <!-- Description Section -->
        <div class="description">
            <h2>About This Portal</h2>
            <p>This Student Result Portal is designed to provide students with a platform to check their exam results by simply entering their roll number. Admins can add and update results for students through an easy-to-use admin panel.</p>
        </div>
        
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
        let results = {}; // This will hold student results

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
