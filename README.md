# KODAM III/SILIWANGI
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8" />
    <title>Peta Kodam III/Siliwangi</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <!-- Leaflet CSS -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', sans-serif;
            background-color: #f5f7fa;
        }

        header {
            background-color: #004085;
            color: white;
            padding: 15px;
            text-align: center;
        }

        #map {
            height: 65vh;
            width: 100%;
        }

        h2 {
            margin: 0;
        }

        table {
            width: 90%;
            margin: 30px auto;
            border-collapse: collapse;
            background-color: white;
            box-shadow: 0 2px 6px rgba(0,0,0,0.1);
        }

        th, td {
            padding: 10px 14px;
            border: 1px solid #ddd;
            text-align: center;
        }

        th {
            background-color: #007BFF;
            color: white;
        }

        tbody tr:hover {
            background-color: #f1f1f1;
        }

        footer {
            text-align: center;
            font-size: 13px;
            padding: 15px;
            color: #555;
        }
    </style>
</head>
<body>
    <header>
        <h2>Peta Korem dan Kodim Kodam III/Siliwangi</h2>
    </header>

    <div id="map"></div>

    <table>
        <thead>
            <tr>
                <th>Satuan</th>
                <th>Kota</th>
                <th>Latitude</th>
                <th>Longitude</th>
            </tr>
        </thead>
        <tbody id="table-body">
            <!-- Diisi via JavaScript -->
        </tbody>
    </table>

    <footer>© 2025 - Peta Kodam III/Siliwangi | Dibuat dengan LeafletJS & OpenStreetMap</footer>

    <!-- Leaflet JS -->
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
    <script>
        const locations = [
            {unit: "Korem 061/SK", kota:"Bogor", lat:-6.595, lng:106.816},
            {unit: "Kodim 0606", kota:"Kota Bogor", lat:-6.595, lng:106.816},
            {unit: "Kodim 0607", kota:"Kota Sukabumi", lat:-6.922, lng:106.927},
            {unit: "Kodim 0608", kota:"Kabupaten Cianjur", lat:-6.823, lng:107.142},
            {unit: "Kodim 0621", kota:"Kabupaten Bogor", lat:-6.485, lng:106.851},
            {unit: "Kodim 0622", kota:"Kabupaten Sukabumi", lat:-6.981, lng:106.564},
            {unit: "Korem 062/TN", kota:"Garut", lat:-7.210, lng:107.905},
            {unit: "Kodim 0609", kota:"Kabupaten Bandung & Cimahi", lat:-6.872, lng:107.542},
            {unit: "Kodim 0610", kota:"Sumedang", lat:-6.861, lng:107.923},
            {unit: "Kodim 0611", kota:"Garut", lat:-7.210, lng:107.905},
            {unit: "Kodim 0612", kota:"Tasikmalaya", lat:-7.327, lng:108.220},
            {unit: "Kodim 0613", kota:"Ciamis", lat:-7.325, lng:108.353},
            {unit: "Korem 063/SGJ", kota:"Cirebon", lat:-6.732, lng:108.552},
            {unit: "Kodim 0604", kota:"Karawang", lat:-6.305, lng:107.310},
            {unit: "Kodim 0605", kota:"Subang", lat:-6.571, lng:107.757},
            {unit: "Kodim 0614", kota:"Kota Cirebon", lat:-6.732, lng:108.552},
            {unit: "Kodim 0615", kota:"Kuningan", lat:-7.016, lng:108.485},
            {unit: "Kodim 0616", kota:"Indramayu", lat:-6.327, lng:108.325},
            {unit: "Kodim 0617", kota:"Majalengka", lat:-6.838, lng:108.227},
            {unit: "Kodim 0619", kota:"Purwakarta", lat:-6.556, lng:107.443},
            {unit: "Kodim 0620", kota:"Kabupaten Cirebon", lat:-6.758, lng:108.478},
            {unit: "Korem 064/MY", kota:"Serang", lat:-6.110, lng:106.163},
            {unit: "Kodim 0601", kota:"Pandeglang", lat:-6.327, lng:106.107},
            {unit: "Kodim 0602", kota:"Serang", lat:-6.110, lng:106.163},
            {unit: "Kodim 0603", kota:"Lebak", lat:-6.359, lng:106.252},
            {unit: "Kodim 0623", kota:"Cilegon", lat:-6.019, lng:106.054},
            {unit: "Kodim 0618", kota:"Kota Bandung", lat:-6.917, lng:107.619}
        ];

        const map = L.map('map').setView([-6.8, 107], 8);

        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            maxZoom: 18,
            attribution: '© OpenStreetMap contributors'
        }).addTo(map);

        const tbody = document.getElementById('table-body');

        locations.forEach(loc => {
            L.marker([loc.lat, loc.lng])
                .addTo(map)
                .bindPopup(`<b>${loc.unit}</b><br>${loc.kota}<br>Lat: ${loc.lat}<br>Lng: ${loc.lng}`);

            const row = document.createElement('tr');
            row.innerHTML = `
                <td>${loc.unit}</td>
                <td>${loc.kota}</td>
                <td>${loc.lat}</td>
                <td>${loc.lng}</td>
            `;
            tbody.appendChild(row);
        });
    </script>
</body>
</html>
