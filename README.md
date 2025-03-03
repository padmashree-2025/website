<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Personal Information Form with Photo Upload</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f9;
        }
        .container {
            width: 50%;
            margin: 50px auto;
            padding: 20px;
            background-color: white;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }
        h1 {
            text-align: center;
            color: #333;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            margin-bottom: 5px;
            color: #333;
        }
        input[type="text"], input[type="email"], input[type="number"], textarea, select {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            box-sizing: border-box;
        }
        input[type="file"] {
            display: block;
            margin-top: 10px;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: #5c6bc0;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #3f51b5;
        }
        #photoPreview {
            width: 200px;
            height: 200px;
            background-color: #e0e0e0;
            margin-top: 10px;
            position: relative;
        }
        #photoPreview img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        #photoPreview::after {
            content: "Image Preview (No right-click allowed)";
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            color: white;
            font-size: 14px;
            background-color: rgba(0, 0, 0, 0.5);
            padding: 5px;
            display: none;
        }
        #photoPreview:hover::after {
            display: block;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>Personal Information Form</h1>
    <form id="personalInfoForm">
        <!-- Name Field -->
        <div class="form-group">
            <label for="name">Full Name:</label>
            <input type="text" id="name" name="name" required>
        </div>

        <!-- Qualification Field -->
        <div class="form-group">
            <label for="qualification">Qualification:</label>
            <input type="text" id="qualification" name="qualification" required>
        </div>

        <!-- Gender Field -->
        <div class="form-group">
            <label for="gender">Gender:</label>
            <select id="gender" name="gender" required>
                <option value="">Select Gender</option>
                <option value="Male">Male</option>
                <option value="Female">Female</option>
                <option value="Other">Other</option>
            </select>
        </div>

        <!-- Educational Background Field -->
        <div class="form-group">
            <label for="education">Educational Background:</label>
            <textarea id="education" name="education" rows="4" required></textarea>
        </div>

        <!-- Age Field -->
        <div class="form-group">
            <label for="age">Age:</label>
            <input type="number" id="age" name="age" required min="0">
        </div>

        <!-- Photo Upload -->
        <div class="form-group">
            <label for="photo">Upload Your Photo:</label>
            <input type="file" id="photo" name="photo" accept="image/*" required>
            <div id="photoPreview"></div>
        </div>

        <button type="submit">Submit Information</button>
    </form>
</div>

<script>
    document.getElementById('personalInfoForm').addEventListener('submit', function(event) {
        event.preventDefault();  // Prevent the default form submission
        
        const name = document.getElementById('name').value;
        const qualification = document.getElementById('qualification').value;
        const gender = document.getElementById('gender').value;
        const education = document.getElementById('education').value;
        const age = document.getElementById('age').value;

        // Here you would send the data to a server or store it as needed
        console.log('Personal Information Submitted:');
        console.log('Name:', name);
        console.log('Qualification:', qualification);
        console.log('Gender:', gender);
        console.log('Educational Background:', education);
        console.log('Age:', age);

        // Clear the form
        document.getElementById('personalInfoForm').reset();

        alert('Information submitted successfully!');
    });

    document.getElementById('photo').addEventListener('change', function(event) {
        const file = event.target.files[0];
        if (file) {
            const reader = new FileReader();
            reader.onload = function(e) {
                const photoPreview = document.getElementById('photoPreview');
                photoPreview.innerHTML = `<img src="${e.target.result}" alt="Photo Preview">`;
            };
            reader.readAsDataURL(file);
        }
    });
</script>

</body>
</html>


![Screenshot 2025-03-03 105412](https://github.com/user-attachments/assets/fa4b273a-8af1-4196-9d12-edd855d313db)

