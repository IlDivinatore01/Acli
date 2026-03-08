# Circolo ACLI San Giuseppe - Website

Questo è il repository del sito web ufficiale del **Circolo ACLI San Giuseppe** di Bellinzago Novarese, costruito con [Astro](https://astro.build/).

## 🚀 Come iniziare (Sviluppo Locale)

Per far girare il progetto sul tuo computer, segui questi passaggi:

1. **Clona il repository:**
   ```sh
   git clone https://github.com/IlDivinatore01/Acli.git
   cd Acli
   ```

2. **Installa le dipendenze:**
   Assicurati di avere [Node.js](https://nodejs.org/) installato, poi esegui:
   ```sh
   npm install
   ```

3. **Avvia il server di sviluppo:**
   ```sh
   npm run dev
   ```
   Il sito sarà ora visibile all'indirizzo `http://localhost:4321/Acli`.

## 📝 Gestione dei Contenuti (Come aggiornare il sito)

I dati principali del sito (Eventi, Menù e Team) sono gestiti tramite file JSON molto semplici ed intuitivi che si trovano nella cartella `src/data/`. Modificando questi file, il sito si aggiornerà in automatico.

### 1. Modificare gli Eventi (`src/data/events.json`)
Per aggiungere o modificare un evento, apri `events.json` e aggiungi un blocco come questo:
```json
{
  "name": "Nome Evento",
  "date": "10 Ottobre 2025",
  "month": "Ottobre",
  "icon": "🎉",
  "description": "Descrizione dell'evento...",
  "tags": ["Festa", "Musica"],
  "prices": [
    { "label": "Adulti", "amount": "15€" },
    { "label": "Bambini", "amount": "5€" }
  ],
  "deposit": "10€",
  "registrationStart": "1 Ottobre",
  "registrationEnd": "8 Ottobre",
  "flyers": ["/events/locandina.png"]
}
```
**Immagini:** Inserisci le immagini delle locandine nella cartella `public/events/`. Poi nel JSON inserisci il percorso partendo da `/events/nomefile.estensione`. Puoi anche mettere più di una locandina nello stesso evento (il sito capirà automaticamente di mostrarle separate ma collegate allo stesso evento). Se non ci sono `prices`, `deposit` o date di registrazione, puoi semplicemente omettere la riga.

### 2. Modificare il Menù (`src/data/menu.json`)
Il menù è diviso per categorie.
```json
{
  "name": "Titolo Categoria",
  "icon": "🍔",
  "items": [
    {
      "name": "Nome prodotto",
      "price": "5.00"
    },
    {
      "name": "Birra Media/Piccola",
      "price": {
        "Piccola (30cl)": "3.00",
        "Media (50cl)": "5.00"
      }
    }
  ]
}
```
**Prezzi Multipli:** Come vedi nel secondo esempio, se un prodotto ha più varianti/taglie, puoi sostituire la voce `"price": "5.00"` con un blocco `"price": { ... }` contenente le varie taglie, e il sito impaginerà i prezzi multipli su una singola riga per risparmiare spazio.

### 3. Modificare il Direttivo (`src/data/team.json`)
Per cambiare i membri del team, aggiorna `team.json`:
```json
{
  "name": "Nome Persona",
  "role": "Il suo ruolo (es. Presidente)",
  "description": "Breve descrizione, puoi anche lasciarla vuota"
}
```

## 📦 Build e Produzione
Quando sei pronto per pubblicare gli aggiornamenti in produzione:
```sh
npm run build
```
Questo creerà una cartella `./dist/` con tutti i file statici, pronta per essere caricata sul server web.
