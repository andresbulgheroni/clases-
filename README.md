clima(soleado,cordoba,14).
clima(nublado,cordoba,15).
clima(nublado,bsas,14).
clima(nublado,rosario,14).
clima(lluvia,rosario,14).

%voyDeVacaciones(Dia,Lugar):-clima(soleado,Lugar,Dia).




diaValido(Dia):-between(1,50,Dia).
destino(cataratas).
destino(cordoba).
destino(hawai).

voyDeVacaciones(Dia,Lugar):-destino(Lugar),diaValido(Dia),not(clima(lluvia,Lugar,Dia)).

llueveAFinDeMes(Lugar):-clima(lluvia,Lugar,Dia),Dia>29.

diasEntreLluvias(Lugar,D):-clima(lluvia,Lugar,Dia1),
                           clima(lluvia,Lugar,Dia2),
                           D is Dia1-Dia2,
                           Dia1>Dia2.


lugaresVisitados(cordoba).

lugaresNuevos(Lugar):-destino(Lugar),
                      not(lugaresVisitados(Lugar)).

diasComplicados(Dia):-between(13,15,Dia).

goles(morgan,5).
goles(cristine,4).
goles(galli,2).


/*noGoleadora(X):-goles(Otra,GolesOtra),
                goles(Jugadores,Goles),GolesOtras>Goles.


goleadora(Jugadora):-goles(Jugador a,_),
                     not(noGoleadora(Jugadora)).

%a que valor existe que no se supere.
gooleadora(Jugadora):-goles(Juga,Goles),
                      not(otraHizoMasGoles(Goles)).
otraHizoMasGoles(G):-goles(_,otrosGoles),otrosGoles>G.*/


goleadora(Jugo):-goles(Jugo,Goles), 
                 forall(goles(_,OtrosGoles),Goles>=OtrosGoles).
