# vbzdaten

Aufgabe 6:

![Bild bei Daten](file:/vbzdaten/Bookmarks/assets/a6.png)



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


Aufgabe 8:

````sql
CREATE Table `linie`  (
	`fahrweg_id` int NOT NULL,
	`linie` int DEFAULT NULL,
	`richtung` int DEFAULT NULL,
	`fw_no` int DEFAULT NULL,
	`fw_lang` varchar(100) DEFAULT NULL,
	PRIMARY KEY (`fahrweg_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8
\````
````sql
SELECT 
	l.fahrweg_id,
	l.linie,
	l.richtung,
	l.fw_no,
	l.fw_lang
FROM 
	vbzdat.linie 6
WHERE
	l.line = 6;
\````	
````sql
ALTER TABLE fahrzeiten_soll_ist_20191229_20200104 ADD datumzeit_soll_nach_von DATETIME NULL;
ALTER TABLE fahrzeiten_soll_ist_20191229_20200104 ADD datumzeit_ist_an_nach DATETIME NULL;
ALTER TABLE fahrzeiten_soll_ist_20191229_20200104 ADD datumzeit_soll_ab_nach DATETIME NULL;
ALTER TABLE fahrzeiten_soll_ist_20191229_20200104 ADD datumzeit_ist_ab_nach DATETIME NULL;
UPDATE fahrzeiten_soll_ist_20191229_20200104 SET datumzeit_soll_an_nach = DATE_ADD(STR_TO_DATE(datum_nach,'%d.%m.%Y'), INTERVAL soll_an_nach SECOND);
UPDATE fahrzeiten_soll_ist_20191229_20200104 SET datumzeit_ist_an_nach = DATE_ADD(STR_TO_DATE(datum_nach,'%d.%m.%Y'), INTERVAL ist_an_nach SECOND);
UPDATE fahrzeiten_soll_ist_20191229_20200104 SET datumzeit_soll_ab_nach = DATE_ADD(STR_TO_DATE(datum_nach,'%d.%m.%Y'), INTERVAL soll_ab_nach SECOND);
UPDATE fahrzeiten_soll_ist_20191229_20200104 SET datumzeit_ist_ab_nach = DATE_ADD(STR_TO_DATE(datum_nach,'%d.%m.%Y'), INTERVAL ist_ab_nach SECOND);
\````	
