# CPS Test — Geometry Dash

Un test de clicks-per-second care numără și **tastele**, nu doar mouse-ul: `W`, `Space`, `↑` și **click stânga**.
Exact input-urile folosite în Geometry Dash — util când vrei să vezi cât scoate un macro sau un SayoDevice.

Un singur fișier, zero dependențe, zero build.

## Ce face

- **4 input-uri**, activabile independent: LMB, W, Space, ↑ (Arrow Up)
- **Durate**: 1s, 2s, 5s, 10s, 30s, 60s și `∞` (freeplay, până apeși `R`)
- **Peak CPS** pe fereastră glisantă de 1 secundă, nu doar media
- **Interval mediu / cel mai scurt / jitter σ** în ms — arată cât de constant e spam-ul
  (un macro are σ aproape 0, o mână umană nu)
- **Grafic CPS în timp**, cu readout la hover
- **Breakdown pe input** — câte apăsări a dat fiecare tastă
- **Record salvat local** pentru fiecare durată

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

## Licență

MIT
