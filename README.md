# easyhr
A leading page
# Creazione di un archivio zip con i file HTML, CSS e JavaScript del progetto della landing page.

import zipfile
import os

# Directory di destinazione dei file del progetto
project_dir = "/mnt/data/EASY-HR_Landing_Page"
os.makedirs(project_dir, exist_ok=True)

# Creazione dei file del progetto
html_content = """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EASY-HR</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <div class="logo">EASY-HR</div>
        <h1>Gestisci il tuo personale con semplicità</h1>
        <p>Una piattaforma progettata per i ristoratori, per gestire orari, turni, straordinari e molto altro.</p>
        <a href="#features" class="cta-button">Inizia ora</a>
    </header>
    <main>
        <section id="features">
            <h2>Perché scegliere EASY-HR?</h2>
            <div class="features-list">
                <div class="feature-item">
                    <h3>Gestione Turni</h3>
                    <p>Pianifica e assegna turni in pochi clic.</p>
                </div>
                <div class="feature-item">
                    <h3>Monitoraggio Straordinari</h3>
                    <p>Traccia le ore extra dei tuoi dipendenti.</p>
                </div>
                <div class="feature-item">
                    <h3>Ruoli e Assenze</h3>
                    <p>Gestisci ruoli, assenze e cambi turno con facilità.</p>
                </div>
                <div class="feature-item">
                    <h3>Generazione Cedolini</h3>
                    <p>Automatizza il calcolo e la distribuzione dei cedolini.</p>
                </div>
            </div>
        </section>
    </main>
    <footer>
        <p>© 2024 EASY-HR. Tutti i diritti riservati.</p>
    </footer>
</body>
</html>
"""

css_content = """
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    color: #333;
    background-color: #f9f9f9;
}
header {
    background-color: #4CAF50;
    color: white;
    text-align: center;
    padding: 50px 20px;
}
.logo {
    font-size: 30px;
    font-weight: bold;
}
.cta-button {
    display: inline-block;
    background-color: #ff9800;
    color: white;
    padding: 10px 20px;
    text-decoration: none;
    border-radius: 5px;
    margin-top: 20px;
}
.cta-button:hover {
    background-color: #e68900;
}
main {
    padding: 20px;
}
#features {
    text-align: center;
    padding: 50px 20px;
}
.features-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
}
.feature-item {
    background-color: white;
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 20px;
    width: 250px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}
footer {
    text-align: center;
    background-color: #333;
    color: white;
    padding: 10px 0;
}
"""

# Creazione dei file
with open(os.path.join(project_dir, "index.html"), "w") as html_file:
    html_file.write(html_content)

with open(os.path.join(project_dir, "style.css"), "w") as css_file:
    css_file.write(css_content)

# Compressione in un archivio zip
zip_path = "/mnt/data/EASY-HR_Landing_Page.zip"
with zipfile.ZipFile(zip_path, "w") as zipf:
    for foldername, subfolders, filenames in os.walk(project_dir):
        for filename in filenames:
            file_path = os.path.join(foldername, filename)
            zipf.write(file_path, os.path.relpath(file_path, project_dir))

zip_path
