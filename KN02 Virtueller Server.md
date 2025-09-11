# KN02: IaaS - Virtuelle Server

### Instanz erstellen

![InstanzZusammenfassung](Bilder/InstanceZusammenfassung.png)

### Einstellungen

#### Diskgrösse: 8GiB
![Diskgrösse](Bilder/VolumeGrösse.png)
#### RAM-Grösse: 1GiB, Anzahl CPUs:1
![InstanzEinstellungen](Bilder/EinstellungenInstance.png)


### Zugriff mit SSH-Key

```ps
ssh -i "C:\Users\diego\.ssh\diego1.pem" ubuntu@52.91.140.105
```
![Proof1](Bilder/ProofSSH1.png)

```ps
ssh -i "C:\Users\diego\.ssh\diego2.pem" ubuntu@52.91.140.105
```

![Proof2](Bilder/ProofSSH2.png)

Verwendeter Schlüssel

![Bih](Bilder/Schlüsselname_diego1.png)
