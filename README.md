<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Student Pagination Table</title>

<style>
    body {
        font-family: Arial, sans-serif;
        background: #f0f2f5;
        padding: 20px;
        display: flex;
        justify-content: center;
    }
    .container {
        width: 600px;
        background: white;
        padding: 20px;
        border-radius: 10px;
        box-shadow: 0 0 10px rgba(0,0,0,0.2);
    }
    table {
        width: 100%;
        border-collapse: collapse;
        margin-top: 15px;
    }
    th, td {
        padding: 10px;
        text-align: center;
        border-bottom: 1px solid #ddd;
    }
    th {
        background: #007bff;
        color: white;
    }
    .pagination {
        display: flex;
        justify-content: space-between;
        margin-top: 15px;
    }
    button {
        padding: 10px 15px;
        border: none;
        background: #007bff;
        color: white;
        border-radius: 6px;
        cursor: pointer;
        font-weight: bold;
    }
    button:disabled {
        background: #ccc;
        cursor: not-allowed;
    }
    #pageNumber {
        font-weight: bold;
        margin-top: 10px;
    }
</style>

</head>
<body>

<div class="container">
    <h2 style="text-align:center;">Student Details</h2>

    <table>
        <thead>
            <tr>
                <th>Student ID</th>
                <th>Student Name</th>
                <th>Marks</th>
            </tr>
        </thead>
        <tbody id="tableBody"></tbody>
    </table>

    <div class="pagination">
        <button id="prevBtn">Previous</button>
        <span id="pageNumber"></span>
        <button id="nextBtn">Next</button>
    </div>
</div>

<script>
    const students = [
        {id: 2400080021, name: "Suresh", marks: 88},
        {id: 2400080022, name: "Raju", marks: 92},
        {id: 2400080023, name: "Praveen", marks: 80},
        {id: 2400080024, name: "Imran", marks: 75},
        {id: 2400080025, name: "Kiran", marks: 90},
        {id: 2400080026, name: "Rahul", marks: 85},
        {id: 2400080027, name: "Varun", marks: 70},
        {id: 2400080028, name: "Shiva", marks: 95},
        {id: 2400080029, name: "Tarun", marks: 93},
        {id: 2400080030, name: "Ajay", marks: 89},
        {id: 2400080031, name: "Akhil", marks: 78},
        {id: 2400080032, name: "Mahesh", marks: 82},
        {id: 2400080033, name: "Harsha", marks: 88},
        {id: 2400080034, name: "Rohit", marks: 91},
        {id: 2400080035, name: "Sunil", marks: 67},
        {id: 2400080036, name: "Aman", marks: 74},
        {id: 2400080037, name: "Lokesh", marks: 96},
        {id: 2400080038, name: "Sanjay", marks: 83},
        {id: 2400080039, name: "Sameer", marks: 79},
        {id: 2400080040, name: "Naveen", marks: 88}
    ];

    const studentsPerPage = 10;
    let currentPage = 1;

    function displayStudents() {
        const tableBody = document.getElementById("tableBody");
        tableBody.innerHTML = "";

        const start = (currentPage - 1) * studentsPerPage;
        const end = start + studentsPerPage;
        const currentData = students.slice(start, end);

        currentData.forEach(s => {
            const row = `
                <tr>
                    <td>${s.id}</td>
                    <td>${s.name}</td>
                    <td>${s.marks}</td>
                </tr>`;
            tableBody.innerHTML += row;
        });

        document.getElementById("pageNumber").innerText = `Page ${currentPage}`;
        document.getElementById("prevBtn").disabled = currentPage === 1;
        document.getElementById("nextBtn").disabled = end >= students.length;
    }

    document.getElementById("nextBtn").addEventListener("click", () => {
        currentPage++;
        displayStudents();
    });

    document.getElementById("prevBtn").addEventListener("click", () => {
        currentPage--;
        displayStudents();
    });

    displayStudents();
</script>

</body>
</html>
