# Título del Trabajo
Análisis del efecto de varios productos en la calidad de agua de piscinas camaroneras al largo de 37 días de cultivo


# Autor
João Reis



# Descripción del problema
Evaluación de la evolución de niveles de oxígeno disuelto y compuestos nitrogenados en el agua trás aplicación de distintos tratamientos (aditivos).

#Presentación y resúmen de la base de datos
library(readxl)
Datos_Proyecto <- read_excel("Datos_Proyecto.xlsx")
View(Datos_Proyecto)

#Descripción de EDA
#El caso del experimento realizado, el análises debe ser la evolución temporal por lo que cada estanque representa una réplica de cada tratamiento. Como tal, aún que numerados, esta variable debe ser leída como un factor.

Datos_Proyecto$Tank=as.factor(Datos_Proyecto$Tank)

#En un análisis muy superficial, es posible observar la normalidad de los datos de cada una de las variables de interés al largo de los 37 días de prueba.

TAN_plot=ggplot(data=Datos_Proyecto,aes(x=Day,y=TAN,group=Treatment,colour=Treatment),geom_point(),labs(y="Amonia en Nitrogeno Total",x="Día de Prueba"))
TAN_plot

NH3_plot=ggplot(data=Datos_Proyecto,aes(x=Day,y=NH3,group=Treatment,colour=Treatment),geom_point(),labs(y="Nitrito (ppm)",x="Día de Prueba"))
NH3_plot

NO2_plot=ggplot(data=Datos_Proyecto,aes(x=Day,y=NO2,group=Treatment,colour=Treatment),geom_point(),labs(y="Nitrato (ppm)",x="Día de Prueba"))
NO2_plot

DO_plot=ggplot(data=Datos_Proyecto,aes(x=Day,y=DO,group=Treatment,colour=Treatment),geom_point(),labs(y="Oxígeno (mg/L)",x="Día de Prueba"))
DO_plot
