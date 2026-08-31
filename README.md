# WinEQ

Applicazione desktop nativa per **Windows 11**, in un'unica finestra compatta in stile
plugin/synth hardware, sul modello di un programma professionale:

- **Vista principale** (sempre a vista diretta): segue automaticamente l'**uscita audio
  predefinita di Windows** — non c'è una selezione separata da sincronizzare a parte —,
  controlli di riproduzione, **volume master** con un fader verticale in stile mixer e
  misuratore di picco in tempo reale, **equalizzatore a tre bande** — bassi (shelf), medi
  (campana), alti (shelf) — con manopole rotative, un selettore di **preset** subito sotto le
  manopole e parametri avanzati.
- **Impostazioni** (dietro il comando **⚙** nella barra di stato in basso, come nel pannello
  di riferimento): stato e controlli di FxSound (il motore che applica l'equalizzazione),
  aspetto dell'app, **avvio automatico con Windows** e **modalità di sfondo** (finestra
  normale, mini monitor flottante o solo icona nel tray), e — nella scheda **Controller MIDI**
  interna a questa vista — collegamento e **mappatura di un controller** su tutti i
  parametri, con funzione «impara». Lo stesso comando diventa «← Torna a WinEQ» per uscirne.
- **Mini monitor** (facoltativo, vedi Impostazioni → Avvio e secondo piano): una piccola
  finestra flottante, sempre in primo piano e senza voce in barra delle applicazioni, con solo
  il fader del volume master e le tre manopole di Alti/Medi/Bassi impilate in verticale accanto
  ad esso (dall'alto verso il basso) — per tenere sott'occhio e regolare l'ascolto senza la
  finestra intera aperta.

Scritta in C# su **.NET 8 / WPF**, con un solo pacchetto NuGet oltre al framework:
[NAudio](https://github.com/naudio/NAudio). L'icona nell'area di notifica usa
`System.Windows.Forms.NotifyIcon` (interoperabilità WinForms abilitata nel progetto via
`UseWindowsForms`, non un pacchetto aggiuntivo): WPF non ha un proprio wrapper per
Shell_NotifyIcon.
L'aspetto segue Windows 11: barra del titolo scura, angoli arrotondati e, opzionalmente, sfondo Mica.
