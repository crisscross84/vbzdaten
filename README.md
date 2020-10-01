# vbzdaten

Aufgabe 6:

![Aufgabe 6](vbzdaten/Bookmarks/assets/a6.png)



Aufgabe 7:

````sql
SELECT
fsi.linie, 
fsi.richtung, 
fsi.fahrzeug,
fsi.kurs,
fsi.seq_von, 
fsi.halt_id_von, 
fsi.halt_id_nach, 
fsi.halt_punkt_id_von, 
fsi.halt_punkt_id_nach, 
fsi.fahrt_id, 
fsi.fahrweg_id, 
fsi.fw_no,
fsi.fw_typ,
fsi.fw_kurz,
fsi.fw_lang, 
fsi.betriebs_datum, 
fsi.datumzeit_soll_an_von, 
fsi.datumzeit_ist_an_von, 
fsi.datumzeit_soll_ab_von, 
fsi.datumzeit_ist_ab_von, 
fsi.datum__nach,
TIMEDIFF (datumzeit_soll_an_von, datumzeit_ist_an_von) as timediff_an,
TIMESTAMPDIFF (SECOND, datumzeit_soll_an_von, datumzeit_ist_an_von) as timediff_an_seconds, 
TIMEDIFF (datumzeit_soll_ab_von, datumzeit_ist_ab_von) as timediff_ab,
TIMESTAMPDIFF (SECOND, datumzeit_soll_ab_von, datumzeit_ist_ab_von) as timediff_ab_seconds, 
TIMESTAMPDIFF (SECOND, datumzeit_soll_an_von, datumzeit_soll_ab_von) as halt_soll_time_seconds, 
TIMESTAMPDIFF (SECOND, datumzeit_ist_an_von, datumzeit_ist_ab_von) as halt_ist_time_seconds
FROM
fahrzeiten_soll_ist_20191229_20200104 fsi
WHERE datum_von = '03.01.20' AND fahrt_id = 63898
LIMIT 40000;
\````

