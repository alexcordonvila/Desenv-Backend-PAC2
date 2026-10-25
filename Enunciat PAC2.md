# Enunciat de l'activitat R2

Per a aquesta PAC realitzarem un cas pràctic d'implementació d'una web en Drupal 10/11. S'haurà de realitzar en un servidor local, per posteriorment publicar-lo en el servidor al qual teniu accés.

La pràctica servirà per provar el desenvolupament d'un lloc web bàsic en Drupal, incloent la creació de l'estructura de continguts, la gestió de les vistes i la publicació en el servidor.

## Cas d'estudi. Blog de Tecnologies Web

El repte consisteix a desenvolupar un lloc web a Drupal 10/11 per crear un bloc de tecnologies web filtrable per diferents conceptes.

La implementació es basarà en un tipus de contingut personalitzat a Drupal anomenat "Webtech" descrit amb diferents camps. A partir d'aquest tipus de contingut s'haurà de crear un web interactiu amb opcions de cerca avançada que permetin als usuaris trobar tecnologies web segons les seves preferències.

El lloc complementarà aquest nucli de funcionalitats amb altres auxiliars com un sistema de destacats.

## Requisits del repte

* **R1. Tipus de contingut personalitzat:** Crear un tipus de contingut "Webtech" amb els camps següents: el nom de la tecnologia web, si és una tecnologia web Open Source, la/les categoria/es de la tecnologia (es podrà assignar més d'una categoria de, entre d'altres: frontend, backend, fullstack, HTML, CSS, PHP, CMS, DevOps, Base de dades, etc), última versió, any de publicació de la darrera versió, creador (Desenvolupament comunitari, com seria el cas de Vue.js, o bé el nom de l'organització, per exemple Meta per a React, Google per a Angular, etc), llenguatge de programació (si s'aplica) i logotip de la tecnologia web. Opcionalment es poden afegir camps addicionals per complementar la descripció de la tecnologia.

* **R2. Cerca i filtratge avançat:** Configurar filtres per als camps Open Source, categoria i any de publicació de la darrera versió. Utilitzar el mòdul Vistes per crear una pàgina de catàleg amb un sistema de filtratge intuïtiu.

* **R3. Possibilitat d'afegir tecnologies web:** Els usuaris que es registrin per defecte adquiriran el rol col·laborador. Aquests usuaris podran afegir continguts (tecnologies web amb tots els detalls), que quedaran pendents de moderació fins que un administrador els aprovi. A més, cada usuari tindrà una opció de menú “Les meves tecnologies web” que permetrà llistar les seves aportacions.

* **R4. Tecnologies web similars:** A la pàgina de cada tecnologia es mostraran altres 3 tecnologies web similars (si n'hi ha), basats en coincidència d'Open Source i/o categoria/es.

* **R5. Pàgines informatives:** Crear dues pàgines addicionals anomenades "Sobre nosaltres" i "Preguntes freqüents", que apareixeran al menú principal.

* **R6. Destacats a la portada:** Mostra 5 tecnologies web destacades a la pàgina d'inici, amb rotació aleatòria. Cal mostrar almenys el nom i el logotip de la tecnologia.

* **R7. API REST:** Crear una API REST de només lectura que permeti consultar tot el catàleg en format JSON, amb paginació. De cada tecnologia es mostraran tots els camps.

* **R8. Menú principal:** Inclourem les opcions:

  * **Inici:** es mostraran les tecnologies destacades

  * **Catàleg:** llistat de tecnologies filtrable

  * **Col·laboradors:** llistat d'usuaris que han contribuït a afegir tecnologies web al catàleg

  * **Les meves tecnologies web:** les tecnologies publicades de l'usuari actual; opció només visible quan un usuari està loguejat

  * **Sobre nosaltres:** pàgina genèrica lliure

  * **Preguntes freqüents:** pàgina genèrica lliure

  * **API:** obre l'URL de l'API en una pestanya nova

## Tasques

Basant-nos en els requisits del projecte i, tenint en compte els documents a lliurar (secció “Format de lliurament”), realitzarem i documentarem les activitats següents. Es podran utilitzar mòduls contribuïts de Drupal, o fins i tot mòduls programats a mida, sempre que se'n justifiqui l'ús.

### Activitat 1. Instal·lació de Drupal (1 punt)

Instal·larem Drupal a la màquina local i comprovarem el seu funcionament. Es pot reutilitzar una instal·lació prèvia, però en aquest cas cal actualitzar el nucli i els mòduls. Cal indicar l'usuari/contrasenya de l'usuari "admin" en aquest apartat i també al formulari de lliurament.

### Activitat 2. Creació de continguts (1 punt)

Crearem un tipus de contingut personalitzat anomenat Webtech amb els camps descrits al requisit R1. Justificarem l'ús de taxonomies o camps simples segons convingui per poder implementar la cerca/filtratge de l'activitat 3.
Afegirem almenys 5 tecnologies web reals i 10 tecnologies web fictícies. Per a la generació automàtica de continguts ficticis, es pot fer servir un mòdul contribuït de Drupal.

### Activitat 3. Catàleg filtrable (1 punt)

Segons R2, crearem una vista en forma de pàgina que permeti filtrar les tecnologies web per:

* Categoria

* Open Source

* Any de publicació de la darrera versió

Es recomana crear aquesta vista amb el mòdul Vistes.

### Activitat 4. Pàgina de contingut (1 punt)

Crearem la pàgina de cada tecnologia web mostrant tots els seus camps de manera atractiva. A més, d'acord amb el requisit R4, inclourem una secció de "Tres tecnologies web similars" basada en els camps Open Source i/o categoria/s. Es recomana fer servir una vista amb filtre contextual.

### Activitat 5. Creació de rols (1 punt)

Segons el requisit R3, crearem un rol col·laborador amb permisos per crear i editar únicament les pròpies tecnologies. Els continguts creats quedaran pendents de publicació fins que l'administrador els aprovi. A més, crearem un usuari de prova per a aquest rol i hi afegirem dues tecnologies web associades a aquest usuari. L'usuari i la contrasenya han de ser “editor” i “uoc-2627” respectivament.

### Activitat 6. Menú i pàgines informatives (1 punt)

En base als requisits R8 i R5, crearem el menú principal i dues pàgines informatives (Sobre nosaltres i Preguntes freqüents).

### Activitat 7. Continguts destacats (1 punt)

Segons R6, a la pàgina inicial mostrarem únicament 5 tecnologies web destacades, sense paginació. L'ordre ha de canviar de forma aleatòria en recarregar. Mostrarem només els camps següents: nom de la tecnologia, si és (o no) Open Source, el logotip i un enllaç a la pàgina de detalls de la tecnologia web.
A més, a la pàgina inicial afegirem un footer que mostri el nostre nom i cognoms.

### Activitat 8. API (1 punt)

D'acord amb R7, crearem una API REST de consulta que retorni en format JSON tot el catàleg de tecnologies web. La URL serà `/api/webtechs`. L'API ha de permetre la paginació de 10 resultats per pàgina. Es pot implementar amb una vista en format REST exportable.

### Activitat 9. Publicació (2 punts)

Publicarem el lloc web al servidor de la UOC, verificant-ne el funcionament correcte.

## Format de lliurament

Es lliuraran dos documents en format `.pdf` (que inclogui el nom d'alumne/a). El lliurament es realitzarà a través del apartat corresponent de l'aula virtual.
Es valorarà el funcionament del resultat al servidor i la documentació adequada del procés.

### Entregables

S'hauran de lliurar dos documents en format PDF i emplenar un formulari amb les dades d'accés. Cada document tindrà una portada i un índex.

1. **Explicació del desenvolupament de l'activitat**

   * Nom de l'arxiu: `pac2_document_1_desenvolupament_Cognoms_Nom.pdf`

   * Cal explicar detalladament com s'ha realitzat l'activitat, incloent-hi els errors trobats (si n'hi hagués) i les solucions aplicades.

   * Es poden incloure captures de pantalla per il·lustrar el procés.

   * L'extensió màxima permesa és 1 pàgina per tasca. No s'estableixen restriccions de format (interlineat, mida de font, etc.), però l'incompliment del límit d'extensió serà penalitzat.

2. **Documentació de proves**

   * Nom del fitxer: `pac2_document_2_proves_Cognoms_Nom.pdf`

   * S'han de documentar les proves realitzades per verificar que l'activitat compleix els requisits establerts a cada apartat.

   * S'han d'incloure captures de pantalla que evidenciïn el funcionament correcte.

   * Cal acompanyar cada prova amb una explicació breu dels passos seguits.

   * No hi ha límit d'extensió, ja que el contingut principal consistirà en captures de pantalla.

3. **Codi i base de dades**

   * Per poder superar el repte, és condició indispensable compartir tant la carpeta del projecte com la base de dades. Per això, pujarem un únic fitxer comprimit (`.zip`) a Google Drive que contingui el projecte i la base de dades. Al formulari del següent pas afegirem l'enllaç de descàrrega.

   * **IMPORTANT:** cal assegurar-se que el zip s'ha compartit correctament perquè els professors es puguin descarregar el projecte i la base de dades.

4. **Dades d'accés al projecte**

   * Cal emplenar el següent formulari amb les dades d'accés al Drupal i a la màquina virtual:

   * [Formulari d'accés](https://docs.google.com/forms/d/1tX-CTvG8K0_o8GYD8ThMn4GYHHcsHDSQ8RwaTT1cYgo/edit)

## Avaluació

Les activitats d’aquest repte s’avaluaran de la manera indicada en cada tasca.
La nota d'aquest repte constitueix un **30% sobre la nota final** de l'assignatura.

Recorda que per acollir-te a l'avaluació continuada de l'assignatura, i superar-la, hauràs de superar tots els reptes. Un repte es considera superat si n'obtens una nota igual o superior a 3 punts.

## Propietat intel·lectual i plagi

La Normativa acadèmica de la UOC disposa que el procés d'avaluació es fonamenta en el treball personal de l'estudiant i pressuposa l'autenticitat de l'autoria i l'originalitat dels exercicis realitzats.

L'absència d'originalitat a l'autoria o el mal ús de les condicions en què es realitza l'avaluació de l'assignatura és una infracció que pot tenir conseqüències acadèmiques greus.

Et recomanem llegir la guia sobre el plagi acadèmic i com evitar-ho. Recorda que sempre que reutilitzis contingut de tercers has de citar la font.

L'estudiant serà qualificat amb un suspens (D/0) si es detecta manca d'originalitat a l'autoria d'alguna prova d'avaluació continuada (PEC) o final (PEF), sigui perquè hagi utilitzat material o dispositius no autoritzats, sigui perquè ha copiat textualment d'internet, o ha copiat apunts, de PAC, de materials, manuals o articles (sense la cita corresponent) o d'un altre.