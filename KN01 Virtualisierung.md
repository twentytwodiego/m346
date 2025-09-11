## Hypervisor Typ 1 und Typ 2

Ein Hypervisor ist eine Software, die ermöglicht, mehrere VMs auf der gleichen Hardware auszuführen. Jede VM kann ihr eigenes Betriebssystem und eigene Anwendungen haben, während die Hardwareressourcen gemeinsam genutzt werden.  

### Typ 1 - Bare-Metal Hypervisor
Es läuft direkt auf der Hardware (ohne ein Host-Betriebssystem) und es ist sehr effizient und performant. 
<br> Beispiele: VMware ESXi, Microsoft Hyper-V, Xen.  

### Typ 2 - Hosted Hypervisor
Es läuft auf einem bestehenden Betriebssystem wie ein normales Programm, es ist einfach zu installieren, aber weniger performant, da ein zusätzliches Host-OS dazwischen liegt.  
<br> Beispiele: Oracle VirtualBox, VMware Workstation.  

**Unterschied:**  
- Typ 1: Direkt auf der Hardware, für Server und produktive Umgebungen geeignet.  
- Typ 2: Läuft auf einem Host-OS, eher für Test- und Entwicklungszwecke gedacht.  

## Vermutung zur Virtualisierungssoftware

Ich verwende VirtualBox als Virtualisierungssoftware.  
Da VirtualBox auf einem bestehenden Betriebssystem installiert wird und dort wie ein normales Programm läuft, vermute ich, dass es sich um einen Hypervisor Typ 2 (Hosted Hypervisor) handelt.  

Begründung: Ein Typ-2-Hypervisor benötigt ein Host-Betriebssystem als Zwischenschicht, während ein Typ-1-Hypervisor direkt auf der Hardware läuft. Da VirtualBox ohne ein Host-OS nicht funktioniert, ist es höchstwahrscheinlich Typ 2.  

Auf meinem Host-System habe ich folgende Hardware festgestellt:

- Logische Prozessoren: 12  
- Arbeitsspeicher (RAM): 16 GB

Diese Werte dienen als Grundlage für den Test mit der Virtualisierungssoftware.

### CPU-Test
In den Einstellungen der VM konnten wir die Anzahl der Prozessoren sogar auf **20 erhöhen**, obwohl das Host-System nur 12 logische Prozessoren hat.  
→ Beim Starten der VM kam es jedoch zu einem Fehler, sodass die VM nicht gestartet werden konnte.  

![ProzessorScreenshot](/Bilder/ProzessorScreenshot.png)

### RAM-Test
Bei der Zuweisung von RAM hat VirtualBox eine Grenze gesetzt.  
Es war nicht möglich, mehr als 16 GB (16384 MB) einzustellen, da es dem Host-RAM entspricht.  

![RAMScreenshot](/Bilder/RAMScreenshot.png)

### Ergebnis
- CPUs: Über 12 einstellbar aber VM startet nicht  
- RAM: Über 16 GB gar nicht möglich, es hat eine Blockade direkt in den Einstellungen.  

## Begründung und Fazit

Ich habe vermutet, dass es sich bei VirtualBox um einen Hypervisor Typ 2 handelt da die Software auf einem bestehenden Betriebssystem installiert wird und ohne Host-OS nicht funktioniert.

### Erklärung zu den Tests
- CPU: In den Einstellungen konnten wir mehr Prozessoren zuweisen, als das Host-System physisch besitzt (z. B. 20 statt 12). Das liegt daran, dass VirtualBox die Anzahl der virtuellen CPUs flexibel simulieren kann. Allerdings kann die VM mit diesen Einstellungen nicht starten, da die tatsächliche Hardware dafür nicht ausreicht.
- RAM: Es ist nicht möglich, mehr RAM zuzuweisen, als im Host verfügbar ist (16 GB). Dadurch wird verhindert, dass die VM überhaupt starten könnte und das Host-System instabil wird.  

### Fazit
Diese Beobachtungen bestätigen meine Vermutung: VirtualBox ist ein Hypervisor Typ 2.  
- Software läuft abhängig vom Host-Betriebssystem.  
- Ressourcen können nur innerhalb der physisch vorhandenen Hardware genutzt werden.  

