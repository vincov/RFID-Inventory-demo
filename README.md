# RFID-Inventory-demo

Dimostrazione di integrazione dello Zebra SDK in un'applicazione Android per la scansione simultanea di tag RFID e barcode.

Per la demo sono stati utlizzati due tag e un barcode:
* `Tag ID finale 50B60, sfondo blu ("Ingranaggio")`
* `Tag ID finale 30B60, sfondo rosso ("Motore")`
* `BARCODE #1234`

L'app ha un suo database interno nel quale i due tag ID sono stati mappati assegnando loro nomi arbitrari (Ingranaggio e Motore).

L'app è composta da due funzionalità: Inventory e Single tag.
# Inventory

Questa funzione esegue una scansione continua dei tag RFID, fintanto che il trigger viene tenuto premuto. Al termine della raccolta dati sarà possibile effettuare una qualsiasi azione, ad esempio inviare l'elenco dei tag letti ad un servizio che li utilizzerà per aggiornare l'inventario.

Oltre all'antenna RFID, l'app integra il servizio [Zebra DataWedge](https://www.zebra.com/it/it/software/mobile-computer-software/datawedge.html) attraverso il quale è anche possibile leggere un barcode.
# Single tag

Lo scopo di questa funzione è leggere con la maggior accuratezza possibile un singolo tag RFID, ad esempio per registrare l'entrata o l'uscita in magazzino di un singolo pezzo.

L'antenna RFID catturerà sempre diversi tag, specialmente in un ambiente dove questi sono presenti in gran numero, come ad esempio un magazzino. Per ovviare a questa eventualità l'applicazione realizzata utilizza l'RSSI (Received Signal Strength Indication) per determinare quale tag tra i diversi catturati è quello più vicino all'antenna.

La potenza del segnale indicata dall'RSSI è tanto maggiore quanto più il valore è vicino a zero, nella demo questo valore appare tra parentesi accanto al nome del tag rilevato.

In uno scenario in cui un'operatore dovesse scansionare un singolo tag per segnalare l'entrata/uscita a magazzino, se la scansione rilevasse più di un elemento, sarebbe possibile proporre all'utente un elenco di risultati ordinati dal più vicino al meno vicino, permettendogli di scegliere il tag corretto.

Puntare l'antenna direttamente sul tag migliora notevolmente la precisione di questo sistema, tuttavia come sistema di "sicurezza" è sempre presente la funzione di scansione barcode, che in questo scenario resta la più indicata. Le due funzioni potrebbero coesistere, associando ad ogni RFID un barcode.

# Demo

https://github.com/user-attachments/assets/b66887bd-f61d-40d4-8a9d-291efe6981ee
