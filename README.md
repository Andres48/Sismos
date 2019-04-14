# Sismos
realizar un programa que se encarge de plotear las coordenadas de los sismos

import csv
import simplekml

inputfile = csv.reader(open('Catalogo.csv','r'))
kml=simplekml.Kml()

for row in inputfile:
  f=kml.newpoint(name=row[2],coords=[(row[4],row[3])])
  if float(row[2])<6.50:
      f.style.iconstyle.icon.href = 'http://maps.google.com/mapfiles/kml/pushpin/grn-pushpin.png'
  elif float(row[2])<7.50:
           f.style.iconstyle.icon.href = 'http://maps.google.com/mapfiles/kml/pushpin/ylw-pushpin.png'
  else:
            f.style.iconstyle.icon.href = 'http://maps.google.com/mapfiles/kml/pushpin/red-pushpin.png'
kml.save('battleplaces.kml')
