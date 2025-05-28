## Helm Chart Erstellung & Management: Kurzbeschreibung

Das Erstellen und Managen eines Helm Charts für Kubernetes-Anwendungen folgt einem typischen Zyklus:

1.  **Chart erstellen:**
    *   Mit `helm create <chart-name>` wird eine grundlegende Chart-Struktur generiert. Diese beinhaltet:
        *   `Chart.yaml`: Metadaten des Charts (Version, Name, Beschreibung).
        *   `values.yaml`: Standardkonfigurationswerte für das Chart.
        *   `templates/`: Verzeichnis mit Kubernetes-Manifest-Vorlagen (z.B. `deployment.yaml`, `service.yaml`), die Variablen aus `values.yaml` verwenden (z.B. `{{ .Values.replicaCount }}`).

2.  **Chart installieren (Release):**
    *   Das Chart wird mit `helm install <release-name> ./<chart-name>/` als "Release" im Kubernetes-Cluster installiert. Helm rendert die Templates mit den Werten aus `values.yaml` (oder überschriebenen Werten) zu gültigen Kubernetes-Manifesten und wendet diese an.

3.  **Release überprüfen:**
    *   Mit `helm list` wird der Status aller installierten Releases angezeigt.
    *   `kubectl get all -l app.kubernetes.io/instance=<release-name>` (oder ähnliche Selektoren basierend auf den Chart-Labels) zeigt die von Helm erstellten Kubernetes-Objekte (Pods, Services, Deployments etc.).

4.  **Release aktualisieren (Upgrade):**
    *   Änderungen an den Chart-Templates oder in der `values.yaml` (z.B. eine neue Image-Version oder eine andere Anzahl an Replikaten) werden mit `helm upgrade <release-name> ./<chart-name>/` auf den laufenden Release angewendet. Helm ermittelt die Unterschiede und aktualisiert nur die notwendigen Kubernetes-Ressourcen.

5.  **Release deinstallieren:**
    *   Mit `helm uninstall <release-name>` werden der Release und alle zugehörigen Kubernetes-Ressourcen, die durch diesen Release erstellt wurden, sauber aus dem Cluster entfernt.

Dieser Prozess ermöglicht eine versionierte, konfigurierbare und wiederholbare Bereitstellung von Anwendungen auf Kubernetes.

![alt text](<Screenshot 2025-05-27 170456-1.png>)
![alt text](<Screenshot 2025-05-28 135726.png>)
![alt text](<Screenshot 2025-05-28 140346.png>)
![alt text](<Screenshot 2025-05-28 140432.png>)
![alt text](<Screenshot 2025-05-28 140515.png>)
![alt text](<Screenshot 2025-05-28 140643.png>)
![alt text](<Screenshot 2025-05-28 141303.png>)
![alt text](<Screenshot 2025-05-28 141845.png>)
![alt text](<Screenshot 2025-05-28 141927.png>)
![alt text](<Screenshot 2025-05-28 141953.png>)
![alt text](<Screenshot 2025-05-28 142018.png>)
![alt text](<Screenshot 2025-05-28 142052.png>)
![alt text](<Screenshot (3993).png>)
