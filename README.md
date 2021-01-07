# Progetto-Giro-del-Mondo
Il progetto ha lo scopo di definire il percorso minimo partendo e arrivando dalla stessa città in un qualsiasi punto della Terra spostandosi però sempre e solo verso Est e considerando le seguenti regole:
•	Ci si può spostare solo verso le tre città più vicine a quella in cui siamo
•	Il costo di raggiungimento di ogni città è così definito: 2 ore per la città più vicina, 4 per la seconda, tre per la terza. Inoltre vanno aggiunte altre 2 ore se la città di destinazione ha più di 200000 abitanti e ulteriori 2 se le città di partenza e destinazione si trovano in due stati diversi.
Per raggiungere questo scopo è stato utilizzato l’algoritmo di Dijkstra, analizzato e studiato al seguente indirizzo: https://it.wikipedia.org/wiki/Algoritmo_di_Dijkstra.
Implementando tale algoritmo in un caso più semplice se ne è capito il funzionamento e poi si è cercato di adattarlo al progetto.
Per prima cosa sono state definite le città all’interno del database come nodi del grafo, ogni nodo è stato caratterizzato dai seguenti attributi:
•	Numero: utile per aggiornare l’indice alla fine di ogni ciclo, e spostarsi correttamente all’interno del grafo
•	Identificativo: corrisponde all’identificativo di ogni città, è univoco, utilizzato per ricercare i nodi all’interno del grafo
•	Nome: corrisponde al nome della città, non è utilizzato nell’algoritmo in quanto non univoco, è utilizzato solo per la stampa del risultato
•	Potenziale: è il costo per raggiungere ogni nodo dato dalla somma del costo per raggiungere il nodo successivo e dal potenziale del nodo in cui siamo (all’inizio dell’algoritmo il potenziale di tutti i nodi è infinito)
•	Def: è un flag impostato a True o False utilizzato per rendere definitivo un nodo (all’inizio tutti i Nodi sono impostati su True quindi non ancora definitivi)
•	Precedente: è il nodo che abbiamo visitato precedentemente rispetto a quello dove siamo adesso
•	Pesi: è una lista di dizionari, ogni nodo ha il suo dizionario con all’interno le tre città più vicine con relativo peso (costo di raggiungimento), ogni dizionario è così strutturato: chiave -> id_città, valore -> peso (espresso in termini di ore necessarie per raggiungerla da dove siamo noi)
Questi attributi, per la maggior parte, sono già definiti all’interno del database e prima di essere utilizzati sono stati puliti: eliminando record con informazioni errate, riempiendo i dati mancanti se fondamentali per l’algoritmo ed eliminando invece informazioni non utili al raggiungimento dello scopo.
Una volta verificata la bontà dei dati presenti nel database è stato calcolato l’unico dato mancante utile al raggiungimento dello scopo del progetto: la distanza tra le città.
E’ stata perciò definita una funzione che prende in ingresso i valori di longitudine e latitudine di una coppia di città restituendo il valore kilometrico della distanza tra esse (utilizzando la formula per il calcolo della distanza su piano sferico consultabile alla pagina https://it.wikipedia.org/wiki/Distanza_di_cerchio_massimo) includendo anche gli opportuni controlli visto che ci si può muovere solo verso Est.
I nodi definiti come sopra descritto sono stati inseriti in una lista data in input all’algoritmo di Dijkstra che al suo termine stampa il percorso minimo di viaggio con tutte le tappe effettuate e il tempo impiegato (espresso in ore e giorni).
