# audios-diapason

Grabaciones del profesor Luis Natera de cada nota del cuatro venezolano, para el Centro de Enseñanza Musical (CEM).

- `cuerda_{la|re|fa_sos|si}_tNN.mp3`: cada cuerda en cada espacio, de `t00` (al aire) a `t17`. MP3 mono, 48 kHz, 128 kb/s.
- `trasteo/cuerda_{…}_tNN_trasteo.mp3`: otra versión de las notas pisadas, espacios 1 a 14.
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
