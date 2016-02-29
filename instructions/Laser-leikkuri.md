---
layout: page
title: Laser-leikkuri
navigation: True
logo: 'assets/images/alien_pink.svg'
category: instructions
---

_(Documentation written by Vaasa Hacklab, https://vaasa.hacklab.fi/)_

25 W CO<sub>2</sub> tube laser cutter with a working area of 70 mm by 120 mm capable of cutting paper, cardboard, acrylic up to 6 mm and wood and plywood (~ 4 mm).

**Preparations**

- **You need to have qualification for the cutter**, ask someone for help</span>
- Make sure the cooling water is flowing and there is enough of it
- Make sure the fume exhaust is routed outside (might be at the IT-rack every now and then)
- Make sure you are not cutting material that is on the list of forbidden materials. (PVC, carbon fibre, ..)
- Do not look at the invisible laser as it is not good for you – use the camera

**Other notes**

- Disable laser by popping up the “Enable laser” button when ever the cover is open.
- Enable laser only when you are cutting
- When mounting and dismounting the workpiece from the spring loaded tray squeeze the spring and do not move the carriage. Do not pull only the handle as it will result in carriage pulleys to break eventually


## CUPS Printing to Laser Engraver

Laser engraver is equipped with printing server and is announced in LAN as a network printer **Laser on Engrave** and **LaserNoRot on Engrave**. The print server is the “broken” laptop on top of the laser engraver. The display is connected to that and does automatically on start up start the server and show the image from the camera on the screen. The laptop boots on power on e.g. when the laser main switch is turned on from the extension cord.

Engrave (https://10.10.0.21:631/printers/Laser)

If the laptop for some reason does not boot the original power button is on top of the laptop on a separate circuit board. The button is the one furthest away from the joining connector. The power led is blue.

When the system is up and running you can print Generic Postscript to the laser. Known to work is Microsoft Publisher (imaging) driver.

Tulostettaessa kaivertimelle kannattaa ilmeisesti käyttää custom-paperikokoa ja määritellä kooksi 120 x 70mm.

Ainakin Inkscapen kanssa on hieman ongelmia, kun Inkscape havaitsee paperin olevan leveämpi kuin korkea ja määrittelee paperin Landscapeksi. Tulostaessa tuo sitten kääntyy 90 astetta. Tällä hetkellä ongelma on korjattu tulostinpalvelimelta kiertämällä kuvaa vielä 270 astetta lisää. Tuo vaatii vielä lisää perehtymistä, koska lienee jossain määrin ohjelma- tai käyttöjärjestelmäkohtaista.

Tuloste osuu parin millin tarkkuudella työstöalueelle tällä hetkellä.

Tulostettavien tiedostojen on oltava viivamuotoisia vektoritiedostoja. Tekstit eivät tulostu, ellei niitä ole ensin muunnettu poluiksi (Object to path).

Jos alat tulostamaan etänä jotain infernaalista kuten testisivua, etkä saa tulostustoimintaa loppumaan, niin loggaa roottina sisään ja tapa prosessi: `cat /tmp/plot-xxxxxxxx.hpgl2`

## CUPS-säätö

Tulostuspalvelimella postscript-tiedosto käsitellään `/usr/lib/cups/backend/plot` -skriptillä, joka tällä hetkellä kääntää kuvan, kohdistaa kuvan ja muuntaa ps:n hpgl-komennoiksi.

## Ongelmanratkaisua

_Kaiverrin junnaa nurkassa pienellä alueella_

Mikäli tulostus tuntuu muuten toimivan hyvin, mutta kaiverrin liikuttaa työstökappaletta ainoastaan muutaman millin liikealueella jossain nurkassa ja kuvittelee kaivertavansa ihan oikein on tulostimelle mennyt out of range eli siis työstöalueen ulkopuolisiin koordinaatteihin viittaava hpgl-tiedosto.

- Työasemassa määritelty paperikoko väärin. Parhaiten toimii custom kokoisella 120mm * 70mm paperilla, joka on samalla työstöalueen koko
- Työaseman ps-tulostinajuri ei tarjoa plot-skriptin tarjoamaa postscriptiä, kokeile vaihtoehtoista ps-ajuria

Periaatteessa kaiverruspalvelimen asetuksissakin voi olla jotain vialla, mutta tuo ei varsinaisesti sisällä mitään säädettäviä muuttujia.

## Tulostus komentoriviltä

Kun olet lisännyt tulostimen koneeseen (onnistuu ihan kivasti normityökaluilla), voit tulostaa mitä tahansa kaivertimelle sanomalla:

`lpr -H 192.168.42.33 -P Laser tiedosto.hpgl`

## Plot-skript and other hacks

```
#!/bin/bash
#
# /usr/lib/cups/backend/plot
#
# (c) D. Czechowski 2010
#
# Based on email dated June 2003 to printing.cups.devel
# (c) Kurt Pfeifle, Danka Deutschland GmbH
# [ this is not really a copyright ; - ) Use and modify freely as you like,
# but don't complain to me...]
#
# 2012 kengu
# mods for 5wlaser


JOBID=$1
USER=$2
TITLE=$3
COPIES=$4
OPTIONS=$5
PID=$$
FILE=$6

# if there are no arguments: print the accepted URI
if [ $# -eq 0 ]; then
echo "direct plot "Unknown" "Send print job as HPGL to port specified in device-
URI""
exit 0
fi
# in case of wrong number of arguments: print usage hint
if [ $# -ne 5 -a $# -ne 6 ]; then
echo ""
echo "Usage: plot job-id user title copies options [file]"
echo " example for device-URI: 'plot:/dev/port'"
echo "(this converts the printfile to HPGL then sends outputs it to specified device file)"
echo ""
echo "Install a printqueue with 'lpadmin -p -v plot:/ -E"
echo ""
exit 1
fi

# get location of plotter port from device URI
# establish temp file for converting
PLOTTER=${DEVICE_URI#plot:}
TMPFILE="/tmp/plot-"`date +%Y%m%d%H%M%S`

# but check "accepting" status first...
GREPSTRING="not accepting" ;
if lpstat -a $PLOTTER | grep "$GREPSTRING" &> /dev/null ; then
echo "ERROR: printer $PLOTTER not accepting jobs"
exit 1
fi

# check temp file status second...
GREPSTRING="not accepting" ;
if lpstat -a $TMPFILE | grep "$GREPSTRING" &> /dev/null ; then
echo "ERROR: printer $TMPFILE not accepting jobs"
exit 1
fi

# output the postscript data
cat $FILE > $TMPFILE".ps"

#sed -e 's/Orientation: Landscape/Orientation: Portrait/' $TMPFILE".ps2" | sed -e 's/ViewingOrientation: 0 1 -1 0/ViewingOrientation: 1 0 0 1/' > $TMPFILE".ps"

# convert postscript file to hpgl and distill it

/usr/bin/pstoedit -rotate 270 -xshift -250 -yshift 30 -xscale 1.42 -yscale 1.42 -f "hpgl" $TMPFILE".ps" $TMPFILE".hpgl"
#/usr/bin/pstoedit -f hpgl $TMPFILE".ps" $TMPFILE".hpgl"
/usr/local/bin/hpgl-distiller -i $TMPFILE".hpgl" -o $TMPFILE".hpgl2"

# output HPGL file
echo "VS1" > $PLOTTER
cat $TMPFILE".hpgl2" > $PLOTTER

# remove temp files
#rm $TMPFILE".ps" $TMPFILE".hpgl" $TMPFILE".hpgl2"

exit 0
/etc/cups/printers.conf:

# Printer configuration file for CUPS v1.4.4
# Written by cupsd
# DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING
<Printer Laser>
Info Laser
MakeModel Foo 5w Laserkaiverrin, 1.0
DeviceURI plot:/dev/lp0
State Idle
StateTime 1353803245
Type 8392772
Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-command 0 commandtops
Filter application/vnd.cups-postscript 0 -
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>
```

:octocat:
