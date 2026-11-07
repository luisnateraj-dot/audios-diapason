# audios-diapason

Grabaciones del profesor Luis Natera de cada nota del cuatro venezolano, para el Centro de Enseñanza Musical (CEM).

- `cuerda_{la|re|fa_sos|si}_tNN.mp3`: cada cuerda en cada espacio, de `t00` (al aire) a `t17`. MP3 mono, 48 kHz, 128 kb/s.
- `trasteo/cuerda_{…}_tNN_trasteo.mp3`: otra versión de las notas pisadas, espacios 1 a 14.
- `largas/cuerda_{…}_tNN.mp3`: **notas largas**, que se dejan sonar hasta que se apagan solas (4 s cada archivo). Para la actividad «Afina con el sonido de tu cuatro» del Afinador. Ver abajo.
- `fallo.mp3` y `partes/fanfarria.mp3`: sonidos de los módulos.

Las usan el Entrenador del Diapasón, Partes del cuatro, Acordes básicos, los visores de acordes (pieza compartida `SonidoAcorde`) y el Afinador.

## Afinación

Referencia: temperamento igual con La = 440 Hz. Medida el 6-nov-2026 con `pruebas/medir_afinacion.py` del proyecto CEM (mediana de 0,30 a 1,20 s tras el ataque, armónicos 1 a 4). Después de la corrección de abajo, **todas las notas están a ±5 cents** y la gran mayoría a ±3.

## Correcciones

### 6-nov-2026 · Afinación de La al aire, Si al aire y La espacio 2

Tres notas estaban bajas de afinación, y son las que sirven de referencia para afinar (las cuerdas al aire y la pareja La espacio 2 = Si al aire de la afinación relativa). Se corrigieron digitalmente, con el permiso del profesor, para que coincidan con un La exacto de 440 Hz.

| Archivo | Antes | Corrección | Después |
|---|---|---|---|
| `cuerda_la_t00.mp3` (La3) | −7,9 cents | +7,9 cents | 0,0 |
| `cuerda_si_t00.mp3` (Si3) | −8,8 cents | +8,8 cents | 0,0 |
| `cuerda_la_t02.mp3` (Si3) | −8,0 cents | +8,0 cents | 0,0 |
| `trasteo/cuerda_la_t02_trasteo.mp3` (Si3) | −8,4 cents | +8,4 cents | 0,0 |

**Cómo se hizo:** cambio de velocidad de reproducción (factor 2^(cents/1200), entre 1,0046 y 1,0051) con remuestreo de alta calidad (soxr) de vuelta a 48 kHz, y nueva codificación en MP3 mono a 128 kb/s, igual que los originales. Un cambio así de pequeño no altera el timbre. El volumen se compensó (+0,45 dB) para que el nivel RMS quede igual al original.

**Efectos secundarios, comprobados:** la duración se acorta unos 9 ms (≈ 0,5 %); el inicio del sonido se mueve menos de 0,2 ms; el pico queda en el mismo nivel (≈ −1 dBFS; el de `trasteo` en −8,3 dBFS, como antes).

**Ligeramente bajas, sin corregir** (dentro de ±5 cents): `cuerda_la_t08` (−4,7), `cuerda_la_t11` (−4,8), `trasteo/cuerda_la_t08_trasteo` (−4,8) y `trasteo/cuerda_la_t11_trasteo` (−5,0).

**Originales:** están en el historial del repositorio, en el commit `579de74` («Add files via upload»).

### 6-nov-2026 · Si espacio 3

Estaba dentro de la tolerancia (−3,2 cents), pero el Afinador la usa en pareja con Re al aire (+1,4) para la afinación relativa («Si espacio 3 = Re al aire»): la diferencia, 4,6 cents, daba un temblor lento (casi uno por segundo) al sonar juntas. Se corrigió con el permiso del profesor, con el mismo método de arriba. La otra versión, la de `trasteo/`, también estaba a −3,3 y se corrigió igual, para que las dos digan lo mismo.

| Archivo | Antes | Corrección | Después |
|---|---|---|---|
| `cuerda_si_t03.mp3` (Re4) | −3,2 cents | +3,2 cents | 0,0 |
| `trasteo/cuerda_si_t03_trasteo.mp3` (Re4) | −3,3 cents | +3,3 cents | 0,0 |

Volumen compensado (+0,45 dB, RMS igual al original); duración −3 ms; pico igual (≈ −1,2 dBFS; el de `trasteo` en −7,8 dBFS). La pareja Si espacio 3 / Re al aire queda a 1,4 cents. **Originales:** en el commit `8b3d3d0` (antes de esta corrección).

## Notas largas (`largas/`)

Grabadas por el profesor el 7-nov-2026 para la actividad «Afina con el sonido de tu cuatro» del Afinador, que compara dos notas sonando juntas y necesita que la nota se oiga el mayor tiempo posible. Las grabaciones de la carpeta principal no cambian (las usan el Entrenador, Partes del cuatro, Acordes básicos y los visores).

**Cómo se grabaron:** cada nota pulsada una vez y sin apagar, con las otras tres cuerdas apagadas con tela (para que no vibren por simpatía) y sin vibrato; tres tomas por nota (cinco en Si espacio 3, cuatro en La espacio 2). WAV mono, 24 bits, 44,1 kHz.

**Cómo se prepararon:** la toma más limpia y que más suena de cada nota; desde 30 ms antes del ataque, 4,0 s, con una salida de 0,4 s al final; remuestreo a 48 kHz (soxr); pico a −1 dBFS, como las demás; MP3 mono, 128 kb/s. Sin corrección de afinación (todas dentro de ±5 cents).

| Archivo | Nota | Afinación (cents, de 0,9 a 2,3 s) | Baja 40 dB en | Baja 50 dB en |
|---|---|---|---|---|
| `cuerda_la_t00.mp3` | La al aire (La3) | −0,2 | 1,64 s | 2,61 s |
| `cuerda_la_t02.mp3` | La espacio 2 (Si3) | −1,1 | 1,63 s | 2,90 s |
| `cuerda_si_t00.mp3` | Si al aire (Si3) | −3,0 | 1,69 s | 2,57 s |
| `cuerda_si_t03.mp3` | Si espacio 3 (Re4) | −1,6 | 1,41 s | 2,13 s |
| `cuerda_re_t00.mp3` | Re al aire (Re4) | −3,7 | 1,71 s | 2,29 s |
| `cuerda_re_t04.mp3` | Re espacio 4 (Fa♯4) | +3,8 | 2,05 s | 2,81 s |
| `cuerda_fa_sos_t00.mp3` | Fa♯ al aire (Fa♯4) | +0,7 | 2,35 s | 3,17 s |
| `cuerda_fa_sos_t03.mp3` | Fa♯ espacio 3 (La4) | +3,4 | 1,95 s | 2,74 s |
| `cuerda_la_arm12.mp3` | Armónico del traste 12 de la cuerda La (La4) | +0,1 | 2,34 s | 3,33 s |

Para comparar: en la carpeta principal, La al aire baja 40 dB en 0,75 s y Fa♯ al aire en 1,37 s. En los primeros 0,3–0,7 s, la afinación de La al aire y de Re al aire se mueve unos cents antes de asentarse (normal al pulsar); por eso se mide de 0,9 a 2,3 s. **Armónico del traste 12 de La** (agregado el 7-nov-2026): rozando la cuerda La encima del traste 12 y pulsando cerca del puente; cuatro tomas, la tercera elegida (la más larga y la más limpia: el La grave de la cuerda quedó 55 dB por debajo). Da el La4 exacto, sin el error de pisar; sirve para comparar con Fa♯ espacio 3 en la afinación repartida del profesor. Los originales WAV los conserva el profesor.
