Per abordar la pràctica de manera eficient sense perdre't en la teoria genèrica, la **guia de lectura mínima del PDF *Drupal 10*** està organitzada segons les tasques i activitats que has de resoldre:

---

### 1. Instal·lació i entorn local (Activitat 1)

- [X] **Què llegir:** **Capítol 2: Instal·lació** (pàg. 11-17).


* **On enfocar-se:**
- [X] Secció 2.1.2 (*Instal·lació amb Composer*, pàg. 12-14) o Secció 2.1.3 (*Instal·lació manual*, pàg. 14-15) segons el mètode que triïs per desplegar el projecte.


- [X] Secció 2.2 (*Arxiu de configuració i base de dades*, pàg. 15-17) per entendre com es connecta la BD local i l'estructura de carpetes (`/sites/default/files`, etc.).





---

### 2. Tipus de contingut "Webtech" i taxonomies (Activitats 2 i 6)

- [] **Què llegir:** **Capítol 3.1: Estructura de continguts de Drupal** (pàg. 18-26).


* **On enfocar-se:**
- [] **3.1.1. Tipus de contingut** (pàg. 19-21): Per crear el tipus de contingut *Webtech* (R1) i les pàgines estàtiques *Sobre nosaltres* i *Preguntes freqüents* (R5).


- [] **3.1.2. Camps** (pàg. 22-23): Per afegir els diferents camps sol·licitats a R1 (text, imatge/logotip, any, etc.).


- [] **3.1.3. Taxonomies** (pàg. 23-26): Crucial per entendre la diferència entre un camp senzill i una taxonomia, i com aplicar-ho al camp de *Categories* de la pràctica per poder filtrar posteriorment.


---

### 3. Vistes: Catàleg filtrable, Similars i Destacats (Activitats 3, 4 i 7)

* **Què llegir:** 
- [] **Capítol 3.4: Views** (pàg. 30-34) 
- []**Capítol 3.2: Presentació dels camps** (pàg. 26-27).


* **On enfocar-se:**
- [] **Filtres exposats (Exposed Filters):** Requisit indispensable per al catàleg filtrable de l'Activitat 3 (R2).
- [] **Filtres contextuals (Contextual Filters):** Per configurar el bloc de "Tecnologies web similars" de l'Activitat 4 (R4).


- [] **Display de blocs i ordenació aleatòria:** Per crear el bloc de 5 tecnologies destacades de l'Activitat 7 (R6).


- [] **Modes de visualització (*Teaser* / *Default*):** (Secció 3.2, pàg. 26-27) per triar quins camps es mostren a la vista i quins al detall.


---

### 4. Rols, Permisos i Moderació (Activitat 5)

- [] **Què llegir:** **Capítol 3.7.2: Persones (people) i permisos** (pàg. 42-44).


* **On enfocar-se:**
- [] Creació del rol "Col·laborador" (R3).


- [] Configuració de permisos per permetre crear contingut *Webtech* però sense permís de publicació directe (queda pendents de moderació/aprovació per part de l'administrador).



---

### 5. Menú de navegació (Activitat 6)

* **Què llegir:** **Capítol 3.3.1: Menús** i **Capítol 3.3.2: Blocs** (pàg. 27-30).


* **On enfocar-se:**
* Configuració de les opcions de navegació del *Main Navigation* (Inici, Catàleg, Sobre nosaltres, API, etc.) d'acord amb el requisit R8.


* Gestió de visibilitat d'enllaços segons si l'usuari està autenticat o no ("Les meves tecnologies web").





---

### 6. Creació de l'API REST JSON (Activitat 8)

* **Què llegir:** **Capítol 3.9 del document de suport (*Backend per a aplicacions web.pdf*, pàg. 36-37)** + **Secció 3.4 del PDF Drupal 10 (Display REST Export)**.


* **On enfocar-se:**
* Activar els mòduls del nucli `RESTful Web Services` i `Serialization`.


* Creació d'una **Vista** amb un display de tipus **REST Export** configurant la ruta `/api/webtechs`, el format JSON i la paginació a 10 resultats.


* Donar permisos d'accés GET a l'usuari anònim.





---

### 📄 Seccions del PDF que POTS OMITIR per a aquesta PAC:

* **Capítol 1:** Introducció teòrica general.


* **Capítol 3.5 i 4.1:** Creació i desenvolupament de Temes des de zero / Twig avançat (amb un tema predefinit o bàsic en tens prou).


* **Capítol 3.8:** Multiidioma.


* **Capítol 4.2 i 4.3:** Desenvolupament de mòduls a mida amb PHP / Drush / Drupal Console avançat (la PAC es resol mitjançant configuració de *site building* i mòduls del core/contribuïts).
* **Capítol 5:** Manteniment i actualització de projectes.