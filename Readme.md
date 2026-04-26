\# Auth Service \- AirPure Hub

Microserviciu responsabil pentru gestionarea utilizatorilor si securitatea platformei.

\#\# Status Etapa 2: Implementat (40%)  
\- \[x\] Configurare mediu Node.js cu Express.  
\- \[x\] Implementare schelet ruta \`/login\` pentru autentificare.  
\- \[x\] Integrare librarie \`jsonwebtoken\` pentru generarea de token-uri JWT.  
\- \[x\] Dockerfile optimizat pentru mediul de productie.

\*\*Responsabil:\*\* Cojocaru Dragos

\# Logic Service \- AirPure Hub

Nucleul de procesare al datelor care calculeaza indicii de poluare.

\#\# Status Etapa 2: Implementat (40%)  
\- \[x\] Setup proiect Python 3.9 cu Flask.  
\- \[x\] Definire algoritm de baza pentru calculul AQI (PM2.5, CO2).  
\- \[x\] Endpoint REST pentru primirea datelor de la senzori.  
\- \[x\] Containerizare folosind Docker (python-slim).

\*\*Responsabil:\*\* Bicoiu Ionut

\# IO Service \- AirPure Hub

Microserviciu dezvoltat in Go pentru gestionarea fluxurilor de date catre bazele de date.

\#\# Status Etapa 2: Implementat (40%)  
\- \[x\] Configurare structura proiect in limbajul Go.  
\- \[x\] Definire conexiuni catre PostgreSQL (utilizatori) si InfluxDB (date senzori).  
\- \[x\] Implementare logica de baza pentru scrierea datelor de tip Time-Series.  
\- \[x\] Dockerfile multi-stage pentru eficienta.

\*\*Responsabil:\*\* Bicoiu Ionut

\# Infrastructure Configuration \- AirPure Hub

Acest repository contine configuratia de orchestrare si deployment pentru intreg ecosistemul AirPure Hub.

\#\# Arhitectura Etapa 2  
In aceasta etapa, am pus accent pe \*\*interconectivitate\*\* si \*\*izolarea retelelor\*\*:

\#\#\# Componente implementate:  
1\. \*\*Orchestrare:\*\* Fisier \`docker-compose.yml\` care ridica tot stack-ul.  
2\. \*\*Retele:\*\* \- \`frontend\_net\`: Pentru comunicarea intre Gateway si servicii publice.  
   \- \`backend\_net\`: Pentru izolarea bazelor de date de accesul extern.  
3\. \*\*Gateway:\*\* Integrare Kong pentru rutarea securizata.  
4\. \*\*Persistenta:\*\* Configurare containere PostgreSQL si InfluxDB.

\*\*Responsabil:\*\* Cojocaru Dragos

