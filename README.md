# Flask Deployment-Labor

Die Anwendung verwendet dieselbe Begrüßungsfunktion über zwei Schnittstellen:

- `main.py`: Kommandozeilenprogramm mit Typer
- `app.py`: Webanwendung mit Flask

## Lokal starten

Die folgenden Befehle werden in diesem Verzeichnis ausgeführt:

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m flask --app app run --debug
```

Anschließend ist die Anwendung unter <http://127.0.0.1:5000> erreichbar.
