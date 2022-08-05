# Cargar librerias

library(dplyr)
library(tidyverse)
library(igraph)
library(tidygraph)
library(ggraph)
library(data.table)


# leo mis datos "enlaces"

# paso 1 ) metabolitos de G. glauca 
# paso 2 ) metabolitos - targets | swisstarget ### donde estan estos datos? 
# paso 3 ) targets - otras proteinas | string, valores experimentales 

# Paso 1) Metabolitos de G. glauca

# La busqueda de la estructura de los metebolitos fue en PubChem "National Center for Biotechnology Information (2022). PubChem Compound Summary for CID 21578020, Galphimine A. Retrieved July 21, 2022 from https://pubchem.ncbi.nlm.nih.gov/compound/Galphimine-A".
# Por medio de los nombres y tomando "Canonical SMILES"
# Ingresando esos datos en SwissTarget para cada compuesto.


# Paso 2) Union de Metabolitos - Targets | SwissTarget


A <- read.csv("SwissTarget_A.csv")
A <- cbind(A, Compuesto=c("A"))

B <- read.csv("SwissTarget_B.csv")
B <- cbind(B, Compuesto=c("B"))

C <- read.csv("SwissTarget_C.csv")
C <- cbind(C, Compuesto=c("C"))

D <- read.csv("SwissTarget_D.csv")
D <- cbind(D, Compuesto=c("D"))

E <- read.csv("SwissTarget_E.csv")
E <- cbind(E, Compuesto=c("E"))

F1 <- read.csv("SwissTarget_F.csv")
F1 <- cbind(F1, Compuesto=c("F"))

G <- read.csv("SwissTarget_G.csv")
G <- cbind(G, Compuesto=c("G"))

H <- read.csv("SwissTarget_H.csv")
H <- cbind(H, Compuesto=c("H"))

I <- read.csv("SwissTarget_I.csv")
I <- cbind(I, Compuesto=c("I"))

Target_SwissTarget <- rbind(A, B, C, D, E, F1, G, H, I)
Target_SwissTarget %>% select(Common.name) -> Target_CommonName 

# Target_CommonName son los targets extraidos de SwissTarget como lista solo los nombres comunes, este archivo se hizo para introducir los targets en StringDB -> "Target.csv"
# Target_swissTarget es la union de todos los archivos con el nombre comun y el real, tambien agregando la columna de Compuesto se diferencia cada proteina del compuesto que hizo match se guardo como archivo en "Targets_Compuesto.csv "

names(Target_CommonName) = NULL

fwrite(Target_CommonName, "Target.csv")
fwrite(Target_SwissTarget, "Targets_Compuesto.csv")



Target_SwissTarget %>% as_tibble() %>% 
  as_tbl_graph()

plot(Target_SwissTarget)



# Paso 3) Targets - otras proteinas | string; Valores experimentales, Capturas de patalla Settings 21/07/22


g_proteinas <- read_csv("String_Interactions.csv")

g_proteinas <- g_proteinas %>% as_tibble()

g_proteinas <- 
  g_proteinas %>%
  filter(experimental > 0)



