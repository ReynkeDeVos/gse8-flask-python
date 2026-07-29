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

Unter Windows PowerShell lauten die ersten beiden Befehle:

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
```

Die Tests laufen mit:

```bash
python -m unittest
```

Der Produktionsserver lässt sich lokal so prüfen:

```bash
gunicorn app:app
```

## Einstellungen für Render

| Einstellung | Wert |
| --- | --- |
| Service Type | `Web Service` |
| Language | `Python 3` |
| Root Directory | `bonus/cli-project` |
| Build Command | `pip install -r requirements.txt` |
| Start Command | `gunicorn app:app` |
| Health Check Path | `/health` |

Render lädt den Quellcode aus dem verbundenen Git-Repository. Jeder Push auf
den ausgewählten Branch kann automatisch ein neues Deployment auslösen.

Die Änderungen werden aus dem Repository-Stammverzeichnis veröffentlicht:

```bash
git add bonus/cli-project
git commit -m "Add Flask deployment demo"
git push origin main
```

Für diese Einführung wird bewusst `pip` verwendet. Es gehört zur grundlegenden
Python-Werkzeugkette und macht virtuelle Umgebungen und die Installation aus
einer `requirements.txt` sichtbar. Ein späteres Projekt kann mit `uv`,
`pyproject.toml` und `uv.lock` zeigen, wie ein moderner Projektmanager diese
Schritte schneller und reproduzierbar zusammenfasst.
