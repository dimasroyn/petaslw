# petaslw
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8" />
    <title>Peta Korem dan Kodim Kodam III/Siliwangi</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <!-- Leaflet CSS -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
    <style>
        body { margin: 0; padding: 0; font-family: Arial, sans-serif; }
        h2 { text-align: center; margin: 10px 0; }
        #map { height: 60vh; width: 100%; }
        table {
            width: 90%;
            margin: 20px auto;
            border-collapse: collapse;
            box-shadow: 0 0 8px rgba(0,0,0,0.1);
        }
        th, td {
            padding: 8px 12px;
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
    </style>
</head>
<body>
    <h2>Peta Korem dan Kodim Kodam III/Siliwangi</h2>
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
            <!-- Data akan diisi dengan JavaScript -->
        </tbody>
    </table>

    <!-- Leaflet JS -->
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
    <script>
        var locations = [
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

        // Inisialisasi peta
        var map = L.map('map').setView([-6.8, 107.0], 8);

        // Layer peta OpenStreetMap
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            maxZoom: 18,
            attribution: '© OpenStreetMap contributors'
        }).addTo(map);

        // Tambah marker ke peta dan isi tabel
        var tbody = document.getElementById('table-body');

        locations.forEach(function(loc) {
            // Marker di peta
            var marker = L.marker([loc.lat, loc.lng]).addTo(map);
            marker.bindPopup(
                "<b>" + loc.unit + "</b><br/>" +
                loc.kota + "<br/>" +
                "Latitude: " + loc.lat + "<br/>" +
                "Longitude: " + loc.lng
            );

            // Baris tabel
            var row = document.createElement('tr');

            var cellUnit = document.createElement('td');
            cellUnit.textContent = loc.unit;
            row.appendChild(cellUnit);

            var cellKota = document.createElement('td');
            cellKota.textContent = loc.kota;
            row.appendChild(cellKota);

            var cellLat = document.createElement('td');
            cellLat.textContent = loc.lat;
            row.appendChild(cellLat);

            var cellLng = document.createElement('td');
            cellLng.textContent = loc.lng;
            row.appendChild(cellLng);

            tbody.appendChild(row);
        });
    </script>
</body>
</html>
