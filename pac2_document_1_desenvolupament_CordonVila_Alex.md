<link rel="stylesheet" type="text/css" href="styles.css">

<div style="text-align: center; padding-top: 80px; padding-bottom: 50px;">

# PAC 2 - implementació d'una web en Drupal 10/11 <!-- omit in toc -->
## Desenvolupament back-end (UOC) <!-- omit in toc -->
<br>

### **Nom i Cognoms:** Àlex Cordón Vila <!-- omit in toc -->
### **Professor:** Daniel Julià Lundgren <!-- omit in toc -->
### **Data:** 11 de Novembre de 2026 <!-- omit in toc -->

</div>

---
>Cal explicar detalladament com s'ha realitzat l'activitat, incloent-hi els errors trobats (si n'hi hagués) i les solucions aplicades. 
>Es poden incloure captures de pantalla per il·lustrar el procés.
>L'extensió màxima permesa és 1 pàgina per tasca. No s'estableixen restriccions de format (interlineat, mida de font, etc.), però l'incompliment del límit d'extensió serà penalitzat.
--- 


<div style="page-break-after: always;"></div>

## Índex <!-- omit in toc -->
- [Activitat 1. Instal·lació de Drupal](#activitat-1-installació-de-drupal)
- [Activitat 2. Creació de continguts](#activitat-2-creació-de-continguts)
- [Activitat 3. Catàleg filtrable](#activitat-3-catàleg-filtrable)
- [Activitat 4. Catàleg filtrable](#activitat-4-catàleg-filtrable)
  - [4.1. Disseny i maquetació de la fitxa de contingut](#41-disseny-i-maquetació-de-la-fitxa-de-contingut)
  - [4.2. Bloc de "Tres tecnologies web similars" (R4)](#42-bloc-de-tres-tecnologies-web-similars-r4)
- [Activitat 5. Catàleg filtrable](#activitat-5-catàleg-filtrable)
  - [5.1. Crear el rol de Col·laborador](#51-crear-el-rol-de-collaborador)
  - [5.2. Continguts "Pendents de moderació"](#52-continguts-pendents-de-moderació)
  - [5.3. Creació d'usuari de prova](#53-creació-dusuari-de-prova)
- [Activitat 6. Catàleg filtrable](#activitat-6-catàleg-filtrable)
- [Activitat 7. Continguts destacats](#activitat-7-continguts-destacats)
  - [7.1 Creació de la vista](#71-creació-de-la-vista)
  - [7.2 Configurar els Camps i ordre aleatori](#72-configurar-els-camps-i-ordre-aleatori)
  - [7.3 Col·locar el Bloc a la Portada i Afegir el Footer](#73-collocar-el-bloc-a-la-portada-i-afegir-el-footer)
+

<div style="page-break-after: always;"></div>


## Activitat 1. Instal·lació de Drupal 
Per instal·lar Drupal CMS amb DDEV hem seguit la documentació [Drupal CMS User Guide - Install with DDEV](https://project.pages.drupalcode.org/drupal_cms/get-started/ddev/).
En primer lloc s'ha creat un nou directori de projecte Drupal dins l'entorn Linux amb la següent comanda:

```bash
cd ~/projectes
mkdir ~/projectes/pac2 && cd ~/projectes/pac2
```

Un cop creada la carpeta podem usar Composer per crear el projecte de Drupal 11 amb el següent codi:

```bash
cd ~/projectes/pac2
ddev config --project-type=drupal11 --docroot=web
ddev composer create-project drupal/cms
```

Això descarrega els fitxers necessaris i configura l'entorn del CMS Drupal.

> **Nota:** Abans d'executar el bloc de codi anterior cal que tinguem en compte que, en el nostre cas, hem de tenir Docker Desktop executant-se a Windows.


Per comprobar que tot ha anat bé podem usar ``ddev drush status`` i ``ddev drush status-report`` :

```bash
Drupal version   : 11.4.10                                    
Site URI         : https://pac2.ddev.site                     
DB driver        : mysql                                      
DB hostname      : db                                         
DB port          : 3306                                       
DB username      : db                                         
DB name          : db                                         
Database         : Connected                                  
Drupal bootstrap : Successful                                 
Default theme    : forma_theme                                
Admin theme      : gin                                        
PHP binary       : /usr/bin/php8.4                            
PHP config       : /etc/php/8.4/cli/php.ini                   
PHP OS           : Linux                                      
PHP version      : 8.4.24                                     
Drush script     : /var/www/html/vendor/bin/drush.php         
Drush version    : 13.8.0.0                                   
Drush temp       : /tmp                                       
Drush configs    : /var/www/html/vendor/drush/drush/drush.yml 
Install profile  :                                            
Drupal root      : /var/www/html/web                          
Site path        : sites/default                              
Files, Public    : sites/default/files                        
Files, Temp      : /tmp                                       
Drupal config    : sites/default/files/sync     

```

Finalment, un cop verificat que tot ha anat bé, podem anar a la configuració de Drupal des del navegador. 
Per obrir l'entorn web cal executar el següent bloc:

```bash
ddev start
ddev launch
```


> **Nota:** Per arrencar el projecte cada vegada cal seguir aquests passos:
> 1. Obrir Docker Desktop
> 2. Anar a la terminal de Linux amb `wsl -d DDEV` i entrar a la carpeta `cd ~/projectes/pac2`
> 3. Executar `ddev start` i `ddev launch`
> 4. Com a usuari administrador hem posat: **acordonv@uoc.edu**
> 5. Coma password hem usat: **Pepa123!**

Les URL que cal que tinguem en compte son les següents:
  1.  Project Url: https://pac2.ddev.site 
  2.  http: 127.0.0.1:51698
  3.  https: 127.0.0.1:51699
  4.  mailpit (mail de test): https://pac2.ddev.site:8026 o 127.0.0.1:51697
  5.  db: 127.0.0.1:51700
  6.  phpmyadmin: https://pac2.ddev.site:8037 

<div style="page-break-after: always;"></div>

## Activitat 2. Creació de continguts

L'objectiu principal d'aquest punt és generar contingut seguint una estructura determinada. Per fe-ho cal tenir present que a Drupal podem definir estructures anomenades Tipus de contingut personalitzat. Per crear aquest contingut hem anat a ``admin/structure/types`` i allà hem fet click a **Add content type** i l'hem anomenat Webtech.

![Nou Tipus de contingut](tipus_contingut_custom.png)

L'estructura creada és la seguent:
```bash
Title -> Tipus: String (Short text)
Open Source -> Tipus: Boolean
Categories -> Tipus: Entity reference > Taxonomy term,  Vocabulari: Categories
Última versió -> Tipus: Text plain
Any de publicació darrera versió -> Tipus: Number integer
Creador -> Tipus: Text plain
Llenguatge de programació -> Tipus: Text plain
Logotip -> Tipus: Image
```
>Nota: Per crear la taxonomia del camp de Categories hem creat previament la taxonomia de Categories creant el vocabulari nou. La taxonomia és el sistema d'organització i classificació per etiquetes que ens permet agrupar continguts que tenen coses en comú. Hem anat a ``admin/structure/taxonomy``, hem creat una Categoria Webtech i hem afegit aquests termes: Frontend, Backend, Fullstack, HTML, CSS, PHP, CMS, DevOps, Base de dades.  

Un cop tenim definit el tipus de contingut propi hem pogut crear manualment les 5 tecnologies reals. Per crear el contigut fictici s'ha usat el mòdul de Drupal anomenat ``Devel`` que previament s'ha instalat amb Composer. Per crear aquest contingut cal anar a ``/admin/config/development/generate/content`` i seleccionar el tipus de contigut Webtech.

![Devel](Devel_generate.png)

Si anem a ``admin/content`` podrem veure la llista de Content creat manualment (recuadre vermell) i la resta creat amb Devel:

![Contingut generat](contingut_creat.png)

Usant Devel hem trobat un error per no haver configurat correctament els camps del tipus de contingut. Aquest és un exemple de la primera prova de generació de contingut on podem veure que els camps que s'han omplert no tenen el format esperat:

![Devel error](Devel_error.png)

Per millorar-ho hem afegit les labels al camp de "Open Source" amb Si/No. En els camps de "Última versió", "Creador" i "Llenguatge de programació" ha generat paràgrafs llargs de text Lorem Ipsum així que hem reduit els caracters acceptats en aquests camps.
<div style="page-break-after: always;"></div>

## Activitat 3. Catàleg filtrable 

L'objectiu d'aquest exercici és crear una pàgina amb un catàleg per al tipus de contingut Webtech que permeti filtrar les tecnologíes per Categoria, Open Source i Any de publicació de la darrera versió.

Per fer-ho hem usar el modul de Vista anant a ``Structure > Views`` i hem afegit una nova Vista que hem anomenat Cataleg Webtech. 
Per a configurar la vista hem afegit els seguents punts:
  1. **Format**: Unordered list mostrant **Fields**.
  2. **Camps (Fields)**: Títol, Categories, Open Souce, Any de publicació, creador.
  3. **Filtres Exposats**: 
     - **Categoria**: De tipus taxonomia i exposat amb operador "Is one of", amb Reduce duplicates per evitar entrades duplicades i amb valor per defecte "Any" per poder veure tot el cataleg inicialment.
     - **Open Source**: De tipus booleà amb operador "is equal to" i amb valor per defecte "Any" per poder veure tot el cataleg inicialment.
     - **Any de publicació**: De tipus enter i exposat amb operador "Is equal to", valor per defecte buit i un placeholder amb un exemple "Ex: 2024".

Un cop hem configurat cada filtre podem veure el cataleg a aquesta url: ``https://pac2.ddev.site/cataleg-webtech``

![Vista cataleg filtrable](cataleg_filtrable.png)

## Activitat 4. Catàleg filtrable 

### 4.1. Disseny i maquetació de la fitxa de contingut
- **Estructura en columnes:** S'ha activat el mòdul **Layout Builder** al tipus de contingut *Webtech* per organitzar la informació en una disposició de dues columnes.
- **Optimització visual:**
  - Columna esquerra: Ajust de la mida del logotip (formatador *Medium*) i visualització de les categories.
  - Columna dreta: Disposició dels camps en línia (*Inline*) per a metadades com *Open Source*, *Última versió*, *Any de publicació*, *Creador* i *Llenguatge de programació*.
- **Neteja d'interfície:** S'han amagat les etiquetes redundants (com el nom del logotip) i s'ha desactivat la informació d'autor i data de publicació des de la configuració del tipus de contingut.

### 4.2. Bloc de "Tres tecnologies web similars" (R4)
Per afegir la secció de les 3 tecnologies similars hem creat una vista de nom ``Tecnologies similars`` amb el check de "Create a block" seleccionat. Per als View Settings hem seleccionat ``Show Content of type Webtech sorted by Title``. Per a configurar el block hem introduit un titol ``Tecnologies similars`` i ``Display format Unformated list output as fields``. 

- **Filtres contextuals (Contextual Filters):**
  1. **Exclusió del node actual:** S'ha configurat un filtre per `Content: ID` que obté l'ID de la URL i l'exclou (`Exclude`), evitant que la tecnologia que s'està consultant es recomani a si mateixa.
  2. **Coincidència per Categoria:** S'ha afegit el filtre `Has taxonomy term ID` configurat per carregar els termes des de la pàgina del node (`Load default filter from node page`) i filtrar continguts que comparteixin qualsevol categoria (`Filter to items that share any term`).
- **Integració:** S'ha afegit el bloc directament a la part inferior de la plantilla de maquetació de *Layout Builder*.

Podem veure el resultat final en aquesta captura:

TODO: Fer la foto que toca:
![Vista cataleg filtrable](activitat4_final.png)

## Activitat 5. Catàleg filtrable 

### 5.1. Crear el rol de Col·laborador
Per crear el rol de **Col·laborador** hem anat a ``/admin/people/roles``. I s'ha afegit el nou rol amb "Add role".  

A aquest rol se li han asignat els permisos pertinents per a webtech des de ``/admin/people/permissions > Webtech``: Crear contingut nou,Editar contingut propi, eliminar contingut propi. També ens ha fet falta afegir la capacitat de ``Basic workflow: Use Create new draft transition``. Per a que pugui pujar imatges com la de Logotip cal que també li afegitm els permisos de ``Image: Create new media`` 

![Permisos col·laborador webtech](permisos_col·laborador.png)

### 5.2. Continguts "Pendents de moderació"
Aquest rol de col·laborador només ha de poder crear contingut en estat pendent fins que el rol admin el marqui com a publicat.
Per fer-ho s'ha configurat des de ``/admin/structure/types/manage/webtech > Edit`` i a Publishing options desmarquem Published.

### 5.3. Creació d'usuari de prova
Per crear l'usuari de prova hem anat a ``/admin/people/create``. 

![Nou usuari de prova](usuari_prova.png)

Per finalitzar aquest punt s'han creat les dues tecnologies web associades a l'usuari creat. Per comprovar l'experiència d'usuari editor ans'ha iniciat sessió amb aquest usuari. L'usuari editor veu l'entorn de creació com es mostra a la següent captura:

![Nou usuari de prova](usuari_editor.png)

Si ara entrem com a administrador podem veure que l'usuari editor ha creat dos continguts en estat Unpublished i fa falta que l'admin els publiqui:

![Permisos col·laborador webtech](usuari_prova_contingut.png)

## Activitat 6. Catàleg filtrable 

Per començar aquesta activitat hem despublicat les pagines que venen per defecte amb el tema instal·lat a Drupal.
Llavors hem creat una pagina nova anomenada Inici com a pàgina pricipal i hem afegit un títol i una llista d'enllaços amb cada un dels requeriments de R8.

Per a la pagina dels Col·laboradors hem creat una vista nova anant a ``/admin/structure/menu/manage/main`` i afegint un nou enllaç anomenat /col-laboradors com podem veure a la següent captura: 
![Crear Vista Col·laboradors](vista_de_colaboradors.png)

Perquè a la taula només surtin els col·laboradors i no l'usuari administrador hem seleccionat **Filter Criteria > Roles > Is one of > Col·laborador** com podem veure a la següent captura:
![Configurar el filtre per Rols](vista_colaboradors_Roles.png)

Per evitar que aquest vista demani login als usuaris que entren a la web cal que configurem a ``/admin/structure/views/view/col_laboradors > Page settings`` i posar que l'accés sigui ``Unrestricted``.

Ara al fer click a l'enllaç de la pagina d'inici ja ens carrega correctament el llistat d'usuaris col·laboradors:
![Vista col·laboradors final](vista_colaboradors_final.png)

Per a poder veure l'Api JSON hem hagut d'activar el JSONAPI. Per fer-ho ho podem fer amb drush amb ``ddev drush en jsonapi -y`` o bé des de ``extend > /admin/modules > JSON:API`` :

![Vista col·laboradors final](vista_API.png)


## Activitat 7. Continguts destacats

### 7.1 Creació de la vista
En aquest punt, s'ha creat una nova vista anomenada **Tecnologies destacades** des de ``/admin/structure/views/add``. Aquesta vista és de contingut ``Webtech``, no genera una pagina nova i crea un bloc nou homònim amb format ``Unformatted list`` de camps amb 5 items per mostrar. 
### 7.2 Configurar els Camps i ordre aleatori
A la vista, dins la secció de Fields s'ha afegit el camp Open Source amb (Si/No) i el camp Logotip.
Per fer que el criteri d'ordenació sigui aleatori, a la secció de Sort Criteria s'ha afegit ``Random``. 

![Vista configurada](activitat7_final.png)

### 7.3 Col·locar el Bloc a la Portada i Afegir el Footer

