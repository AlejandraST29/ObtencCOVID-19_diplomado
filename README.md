# ObtencCOVID-19_diplomado

Bienvenidos a mi primera página
Este proyecto se baso en la base de datos de covid19 proporcionada en el curso de “Herramientas de Productividad para Ciencia de Datos”

Se seleccionaron solo datos del estado de sonora

Estadisticos de personas con Diabetes que padecierón covid19 y tuvieron fecha de defunción
Con Diabetes

Mis objetivos a largo plazo son comparar estos datos con otro padecimiento: Hipertensión

y calcular la diferencia de días entre las fechas de síntomas y la fecha de defunción en cada caso

## Bienvenidos
# Tarea Herramientas de productividad para Ciencia de Datos

FROM rocker/Rstudio

LABEL Alejandra Siqueiros <lic.mat.siqueiros@gmail.com>

WORKDIR /root


RUN apt-get install curl unzip git csvkit

COPY datos_abiertos_covid19.zip

RUN unzip datos_abiertos_covid19.zip  (((((curl -O http://datosabiertos.salud.gob.mx/gobmx/salud/datos_abiertos/datos_abiertos_covid19.zip))))

CMD bash

#limpieza de datos 

root@f2570fc5fe13:/# csvcut -c 6,8,12,13,16,21 210421COVID19MEXICO.csv > DatosDiabetSON.csv
root@f2570fc5fe13:/# csvgrep -c ENTIDAD_RES -m "26" DatosDiabetSON.csv | csvgrep -c 1 -r "[123]" > datosdiabsonconf.csv
root@f2570fc5fe13:/# csvgrep -i -c FECHA_DEF -m "9999-99-99" datosdiabsonconf.csv > diabsonconfdef.csv
root@f2570fc5fe13:/# csvgrep -i -c DIABETES -m "2" diabsonconfdef.csv > diab1sonconfdef.csv
 csvgrep -i -c DIABETES -m "98" diabsonconfdef.csv > diab1sonconfdef.csv
csvgrep -i -c DIABETES -m "2" diab1sonconfdef.csv > diabsonconfdefs1.csv
csvstat diabsonconfdefs1.csv
