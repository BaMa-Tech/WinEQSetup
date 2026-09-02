# WinEQ

> **Branch sperimentale isolato.** Questo branch (`claude/unified-band-mode`) unifica le due
> versioni sviluppate finora — quella in produzione a tre bande
> (`claude/windows-audio-control-midi-6idh00`) e quella sperimentale a sei bande più Preamp
> (`claude/expanded-eq-6bands`) — in un unico programma con un interruttore **Modalità
> equalizzatore** (Tre bande / Sei bande): scelto la prima volta dall'installer, cambiabile in
> qualsiasi momento da Impostazioni → Generali, senza riavviare. Il motore interno resta sempre
> a sei bande; in modalità «Tre bande» Preamp e le tre bande aggiuntive restano semplicemente
> azzerate e fuori dall'interfaccia. Non è pensato per confluire automaticamente nel branch
> principale: resta a sé finché non viene deciso altrimenti.

Applicazione desktop nativa per **Windows 11**, in un'unica finestra compatta in stile
plugin/synth hardware, sul modello di un programma professionale:

- **Vista principale** (sempre a vista diretta): segue automaticamente l'**uscita audio
  predefinita di Windows** — non c'è una selezione separata da sincronizzare a parte —,
  controlli di riproduzione, **volume master** con un fader verticale in stile mixer e
  misuratore di picco in tempo reale, un **equalizzatore** con un selettore di **preset** subito
  sotto le manopole e parametri avanzati. La sua forma dipende dalla **modalità** scelta in
  Impostazioni → Generali:
  - **Tre bande** — Bassi, Medi, Alti (shelf/campana/shelf), il modello classico di WinEQ;
  - **Sei bande** — anche **preamplificazione** (fader a monte del Volume) e una seconda banda
    per Bassi/Medi/Alti (default: 50/200 Hz, 500/1000 Hz, 4/10 kHz), tutte regolabili dai
    Parametri avanzati.
- **Impostazioni** (dietro il comando **⚙** nella barra di stato in basso, come nel pannello
  di riferimento): **modalità equalizzatore**, stato e controlli di FxSound (il motore che
  applica l'equalizzazione), aspetto dell'app, **avvio automatico con Windows** e **modalità di
  sfondo** (finestra normale, mini monitor flottante o solo icona nel tray), e — nella scheda
  **Controller MIDI** interna a questa vista — collegamento e **mappatura di un controller** su
  tutti i parametri raggiungibili nella modalità corrente, con funzione «impara». Lo stesso
  comando diventa «← Torna a WinEQ» per uscirne.
- **Mini monitor** (facoltativo, vedi Impostazioni → Avvio e secondo piano): una piccola
  finestra flottante, sempre in primo piano e senza voce in barra delle applicazioni, che
  rispecchia lo stesso set di controlli della finestra principale nella modalità corrente — solo
  Volume e le tre manopole storiche in modalità Tre bande, anche Preamp e le tre manopole «2» in
  modalità Sei bande — per tenere sott'occhio e regolare l'ascolto senza la finestra intera
  aperta.

Scritta in C# su **.NET 8 / WPF**, con un solo pacchetto NuGet oltre al framework:
[NAudio](https://github.com/naudio/NAudio). L'icona nell'area di notifica usa
`System.Windows.Forms.NotifyIcon` (interoperabilità WinForms abilitata nel progetto via
`UseWindowsForms`, non un pacchetto aggiuntivo): WPF non ha un proprio wrapper per
Shell_NotifyIcon.
L'aspetto segue Windows 11: barra del titolo scura, angoli arrotondati e, opzionalmente, sfondo Mica.

---

## Requisiti

| Componente | Versione |
|---|---|
| Sistema operativo | Windows 10 2004 o successivo; consigliato Windows 11 |
| Runtime di esecuzione | [.NET 8 Desktop Runtime](https://dotnet.microsoft.com/download/dotnet/8.0) |
| Per l'equalizzazione | [FxSound](https://www.fxsound.com/), installato e avviato |
