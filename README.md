# Reentry

**Live:** https://reentry-nu.vercel.app · Built by Tribhuvan Joshi · Sunshine 001

A human heart simulated live on the GPU. Nothing is animated: the ECG, the T wave,
the compensatory pause, and the loss of pulse in VF all come out of the equations.

Open `index.html` through any static server, or deploy the folder to Vercel as is.
It is one file with no dependencies.

    python -m http.server 4173

## Measured from the running simulation

| Check | Result | Normal or expected |
| --- | --- | --- |
| PR interval | 141 ms | 120-200 ms |
| Lead II P / R / T | 0.13 / 1.11 / 0.41 mV (gain calibrated) | small P, tall R, T about a third of R |
| T wave | upright in I, II, V5, inverted in V1 | same |
| QT at 72 bpm | 353 ms | under 440 ms |
| PVC | RR 836, 675, 985 | sum equals two cycles (full compensatory pause) |
| Mobitz I | PR 232, 337, 406, 486, then drop | progressive PR, dropped QRS |
| Complete block | ventricle 43 bpm, PR 12-641 ms | AV dissociation |
| AF | RR 601-879 ms, no P waves | irregularly irregular |
| VF | 5 of 5 live inductions, ART falls to about 14 | pulseless |

## Known limits

The About screen in the app lists these for students. In short: 2D slice, wavelength
exaggerated under ischaemia, QRS slightly wide, V5 R wave too small (0.53 mV, with T almost as tall), AV node and Purkinje are timed rules,
AF has too few wavelets and runs slower than real AF, and shock always succeeds.
For learning only. Not a clinical tool.

`?test=1` skips the intro and exposes `window.__r` for scripted checks.
