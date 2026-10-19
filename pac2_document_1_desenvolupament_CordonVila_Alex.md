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

<div style="page-break-after: always;"></div>

## Activitat 2. Creació de continguts


<div style="page-break-after: always;"></div>

## Activitat 3. Catàleg filtrable 
