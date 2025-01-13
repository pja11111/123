<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2D Array Table</title>
    <style>
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            border: 1px solid black;
            padding: 8px;
            text-align: center;
        }
        th {
            background-color: #f2f2f2;
        }
    </style>
</head>
<body>

<h2>2D Array Table</h2>

<table id="arrayTable"></table>

<script>
    const data = [66, 44, 23, 78, 90, 34, 89, 23, 90, 35];  // ข้อมูลต้นทางที่ต้องการสร้างตาราง

    const result = create2DArray(data);  // เรียกฟังก์ชันเพื่อสร้างตาราง 2D จากข้อมูลใน data

    // ฟังก์ชันที่ใช้สร้างตาราง 2D
    function create2DArray(arr) {
        let result = [];  // ตัวแปร result สำหรับเก็บผลลัพธ์สุดท้ายเป็นตาราง 2D

        // ลูปภายนอกเพื่อสร้างแถวของตาราง
        for (let x = 0; x < arr.length; x++) {
            let row = [];  // แถวใหม่ที่ใช้เก็บข้อมูลในแต่ละตำแหน่งของแถว

            // ลูปภายในเพื่อสร้างเซลล์ในแต่ละแถว
            for (let y = 0; y < arr.length; y++) {
                row.push(`[${arr[y]}]`);  // เพิ่มค่าจาก data ในเซลล์
            }
            result.push(row);  // เพิ่มแถวที่สร้างเสร็จแล้วลงในตาราง result
        }
        return result;  // คืนค่าตาราง 2D ที่สร้างเสร็จแล้ว
    }

    // ฟังก์ชันเพื่อแสดงตาราง HTML
    function renderTable(array) {
        const table = document.getElementById("arrayTable");
        let htmlContent = "<tr><th>Index</th><th>Values</th></tr>";  // เพิ่มหัวตาราง

        // ลูปผ่านข้อมูลใน array 2D เพื่อสร้างแถวและเซลล์ในตาราง
        array.forEach((row, index) => {
            htmlContent += `<tr><td>${index}</td><td>${row.join(' ')}</td></tr>`;
        });

        table.innerHTML = htmlContent;  // แสดงผลในตาราง HTML
    }

    renderTable(result);  // เรียกฟังก์ชันเพื่อแสดงตาราง
</script>





const result = create2DArray(data);  // เรียกฟังก์ชันเพื่อสร้างตาราง 2D จากข้อมูลใน data

function create2DArray(arr) {
    let result = [];  // ตัวแปร result สำหรับเก็บผลลัพธ์สุดท้ายเป็นตาราง 2D

    // ลูปภายนอกเพื่อสร้างแถวของตาราง
    for (let x = 0; x < arr.length; x++) {
        let row = [];  // แถวใหม่ที่ใช้เก็บข้อมูลในแต่ละตำแหน่งของแถว
        
        // ลูปภายในเพื่อสร้างเซลล์ในแต่ละแถว
        for (let y = 0; y < arr.length; y++) {
            const index = x * arr.length + y;
            const value = index < arr.length ? `[${arr[index]}]` : `[${x}, ${y}]`;
            row.push(value); // เพิ่มค่าในแถว
        }
        result.push(row);  // เพิ่มแถวที่สร้างเสร็จแล้วลงในตาราง result
    }

    // กลับหัวแต่ละแถว (reverse) ของเซลล์
    for (let i = 0; i < result.length; i++) {
        result[i] = result[i].reverse();
    }

    return result;
}

console.table(result);  // แสดงผลตารางในคอนโซลในรูปแบบตาราง


</body>
</html>
