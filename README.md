# Desenv-Backend-PAC2
Desenvolupament d'un lloc web interactiu en Drupal 10/11 per a un catàleg de tecnologies web (Webtech) amb filtratge avançat, continguts destacats, control d'accés per a col·laboradors i API REST JSON.


# PAC 2 - Desenvolupament Backend amb Drupal 10/11: Blog de Tecnologies Web

Projecte de desenvolupament web basat en el CMS **Drupal 10/11** realitzat per a l'assignatura de *Desenvolupament Backend*. Consisteix en la implementació d'un catàleg interactiu de tecnologies web (*Webtech*) amb cercador avançat, sistema de moderació de continguts i API REST.

---

## 🚀 Funcionalitats implementades

* **R1. Tipus de contingut personalitzat (`Webtech`):** Camps personalitzats per a nom, Open Source, categories (taxonomies), versió, any, creador, llenguatge i logotip.
* **R2. Catàleg amb cerca i filtratge avançat:** Vista filtrable per entorn Open Source, categoria i any de publicació.
* **R3. Gestió d'usuaris i moderació:** Rol `col·laborador` amb permisos per afegir contingut pendent de moderació i secció *"Les meves tecnologies web"*.
* **R4. Contingut relacionat:** Secció automàtica de 3 tecnologies similars mitjançant filtres contextuals a la pàgina de detall.
* **R5. Pàgines informatives:** Seccions estàtiques *"Sobre nosaltres"* i *"Preguntes freqüents"*.
* **R6. Destacats a la portada:** Bloc de 5 tecnologies destacades amb rotació aleatòria i peu de pàgina personalitzat.
* **R7. API REST JSON:** Punt d'accés de només lectura a `/api/webtechs` amb paginació (10 resultats/pàgina) en format JSON.
* **R8. Navegació dinàmica:** Menú principal estructurat segons l'estat d'autenticació de l'usuari.

---

## 🛠️ Tecnologies utilitzades

* **CMS:** Drupal 10 / 11
* **Llenguatge:** PHP (Symfony Components, Twig)
* **Base de Dades:** MySQL / MariaDB
* **Eines:** Composer, Views (Core), REST Export (Core)

## Instruccions:


### 1. Què és EXACTAMENT el que cal per poder reconstruir-ho tot de zero?

Si un professor o un company es baixa el teu repositori de GitHub, necessitarà únicament aquests elements per tornar a aixecar la web completa:

1. **`composer.json` i `composer.lock`:** Reconstrueixen el nucli de Drupal 11 (`web/core/`), Symfony i tots els mòduls o temes descarregats executant la comanda `composer install`.
2. **El fitxer `.sql` de la base de dades:** Reconstrueix tota la configuració del lloc web que has fet des del panell d'administració (el tipus de contingut *Webtech*, les Vistes filtrables, els rols d'usuari, les taxonomies i el menú).
3. **`web/sites/default/settings.php`:** Fitxer imprescindible que diu a Drupal com connectar-se a la base de dades.
4. **`web/sites/default/services.yml`:** Conté la configuració dels serveis de Drupal (com el mode *debug* de Twig si l'has activat).
5. **Codi propi (si n'hi ha):** Les carpetes `web/modules/custom/` i `web/themes/custom/` (si heu programat algun tema o mòdul a mida).

---

### 2. Com es reconstrueix la web en un ordinador nou pas a pas?

Si algú descarrega el teu repositori de GitHub per executar-lo en un entorn DDEV nou, el procés de reconstrucció és aquest:

1. **Descarregar el codi:**
```bash
git clone https://github.com/el-teu-usuari/techradar.git
cd techradar

```


2. **Configurar i arrancar l'entorn DDEV:**
```bash
ddev config --project-type=drupal11 --docroot=web
ddev start

```


3. **Reconstruir les dependències i el nucli de Drupal (gràcies al `composer.json`):**
```bash
ddev composer install

```

4. **Restaurar la base de dades (gràcies al fitxer `.sql`):**
```bash
ddev import-db --file=base_de_dades_drupal.sql

```

5. **Netejar memòria cau:**
```bash
ddev drush cache:rebuild

```

Així doncs, mentre tinguis inclosos el **`composer.json`**, el **`composer.lock`**, la carpeta **`web/sites/default/`** (amb el `settings.php`) i el fitxer **`.sql`**, la web es pot tornar a aixecar completament sense cap mena de problema.