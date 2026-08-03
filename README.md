# CPS Test — Geometry Dash

Un test de clicks-per-second care numără și **tastele**, nu doar mouse-ul: `W`, `Space`, `↑` și **click stânga**.
Exact input-urile folosite în Geometry Dash — util când vrei să vezi cât scoate un macro sau un SayoDevice.

Un singur fișier, zero dependențe, zero build.

## Ce face

- **6 input-uri**, activabile independent: LMB, W, Space, ↑ (Arrow Up), LShift, LCtrl
  (ultimele două sunt oprite din start — sunt acolo pentru layout-uri de Minecraft,
  unde LCtrl e sprint și LShift e sneak)
- **Durate**: 1s, 2s, 5s, 10s, 30s, 60s și `∞` (freeplay, până apeși `R`)
- **Peak CPS** pe fereastră glisantă de 1 secundă, nu doar media
- **Interval mediu / cel mai scurt / jitter σ** în ms — arată cât de constant e spam-ul
  (un macro are σ aproape 0, o mână umană nu)
- **Grafic CPS în timp**, cu readout la hover
- **Breakdown pe input** — câte apăsări a dat fiecare tastă
- **Taste custom** — `+ tastă`, apeși ce vrei, se adaugă. Se salvează între sesiuni,
  o ștergi cu `×` de pe chip.
- **Moduri de tehnică**, fiecare cu metrica lui — o etichetă singură n-ar spune nimic:
  - **Jitter** → *constanță*: σ raportat la intervalul mediu. Viteza vine ușor, ritmul e greu.
  - **Butterfly** → *balans*: două degete alternând lasă pauze pare/impare; 100% = trag la fel,
    sub 70% = unul rămâne în urmă.
  - **Alternate** → *alternanță*: ce procent din apăsări chiar au schimbat butonul.
    Repetările pe același buton îți strică rata.
- **Record salvat local** pentru fiecare durată **și** fiecare tehnică, separat

## Cum îl folosești

Deschide `index.html` în browser. Sau, dacă e pe GitHub Pages, direct linkul.

Apasă orice input activ ca să pornești — cronometrul începe la prima apăsare, nu înainte.
`R` sau `Esc` resetează.

Click-ul stânga contează **doar în zona mare de sus**, ca să nu numeri accidental
apăsările pe butoane.

## Note

- Auto-repeat-ul de la ținutul tastei apăsate e ignorat (`event.repeat`), deci nu poți trișa
  ținând `W` apăsat.
- Browserul livrează apăsările prin bucla de evenimente, deci la rate foarte mari
  (peste ~1000 Hz de la un SayoDevice) cifrele sunt o limită inferioară — sistemul
  poate uni evenimentele. Pentru spam uman și macro-uri normale e exact.
- Nimic nu pleacă de pe calculatorul tău; recordurile stau în `localStorage`.

### Dacă unul din butoane trimite LCtrl

Când butoanele se suprapun câteva milisecunde — inevitabil la spam rapid — browserul
vede `Ctrl+W` și **închide tabul**. Nicio pagină web nu poate bloca asta, e scurtătură
rezervată browserului. Apăsarea tot se numără, dar tabul e dus.

Variante, dacă nu vrei să remapezi butonul:

```
chrome.exe --kiosk "file:///C:/.../cpstest/index.html"     # kiosk chiar dezactiveaza Ctrl+W
```

sau AutoHotkey, cât timp fereastra e activă:

```ahk
#Requires AutoHotkey v2.0
#HotIf WinActive("CPS Test")
^w::return
#HotIf
```

## Licență

MIT
