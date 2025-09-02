
# Changelog Shottt.it

Ce document répertorie les changements significatifs apportés à l'application. La numérotation des versions suivra le standard [Semantic Versioning](https://semver.org/lang/fr/) après la sortie de la dernière bêta.

## v0.3.0 bêta - 02/09/2025

### 🚀 **Nouvelles fonctionnalités**
* **Upload de vidéos** : Upload de vidéo possible !
    * `[Limite]` : 200MB par vidéo.
    * `[Limite]` : Jusqu'à 30 médias (photos et-ou vidéos) par batch d'upload.
    * `[Limite]` : Vidéos non téléchargeables à ce stade.
---

## v0.2.1 bêta - 01/09/2025

### 🐛 **Corrections de bugs**
* `[Administrateur]` : Correction d'un bug critique où les évènements affichées étaient globales, sans disctinction de compte. Aujourd'hui, l'utilisateur connecté est pris en compte.

---

## v0.2 bêta - 01/09/2025

### ✨ **Améliorations**
* **Implémentation d'un système de monitoring** 
    * Non visible pour l'utilisateur, un système permettant de surveiller :
       * les performances, "métriques" (CPU, RAM) avec OpenObserver
       * les logs au détail (couche applicative) avec Seq

---

## v0.11 bêta - 31/08/2025

### ✨ **Améliorations**
* **Ajout de Matomo pour le tracking** 
    * Permet de suivre l'activité des visiteurs sur l'application, dans le but d'améliorer l'outil.

---

## v0.10 bêta - 30/08/2025

### 🚀 **Nouvelles fonctionnalités**
* **Suppression des images** : L'image supprimée par l'administrateur.
    * `[Invité]` : Elle n'apparaît plus pour les invités. Nécessite une actualisation si l'invité est sur la grille d'affichage.
    * `[Administrateur]` : Peut supprimer une, ou plusieurs images par lot.
    * Les images sont complètement supprimées des serveurs.
    * ⚠️ : Le cache de Cloudflare R2 peut néanmoins toujours afficher l'image grâce à l'URL jusqu'à la fin du TTL. Une purge du cache de R2 peut aider, mais le mécanisme de purge n'a pas été implémenté. 

### ✨ **Améliorations**
* **Format des images et téléchargements** : Images adaptées et optimisées.
    * `[Administrateur]` : Le téléchargement de la photo est fait sur l'original, sans compression ou transformation. Auparavant, la photo téléchargée était seulement la version réduite en largeur sur 1200px.
    * `[Invité]` : Le téléchargement de la photo est fait sur une version à réduite et croppée (width=1600px, qualité=80). Pensé pour mobiles, tablettes et faibles connexions si l'image originale est lourde.
    * `[Miniatures dans les galeries]` : Une version croppée et réduite en qualité est chargée pour un affichage rapide et optimisé (width=800px, qualité=75).
    * `[Visualisation de la photo]` : Une version croppée et réduite en qualité est chargée pour un affichage rapide et optimisé (width=1600px, qualité=80).        
* **Changement libellé et logo de téléversement** pour l'invité.
    * Le logo de téléversement devient un `+` .
    * Le texte du menu de téléversement devient `ajouter` au lieu de `téléverser` en français.
    * Aucun changement en anglais. 
    
* **Suppression des paramètres non utilisés**.
    * Les paramètres n'étant pas utilisés ont été supprimés :
      * Notifications depuis le navigateur
      * Téléchargement de toutes les photos
      * Partage de l'évènement
      * Quitter l'évènement
      * Eléments par page
      * Mode d'affichage par défaut

* **Rebranding léger pour Shottt.it** : Bye-bye "PicManager", bonjour `Shottt.it` !
    * Suppression de toutes les références à PicManager

### 🐛 **Corrections de bugs**
* Sur les boîtes de visualisation des images : 
    * Champ "Date de téléversement"/"Upload date" (ENG) est renommé juste "Date".
    * Ce champ "Date" affiche la date de prise de vue, ou la date d'upload le cas échéant. Ancienmment, affichait la date d'upload.



---



## v0.02 bêta - 30/08/2025

### ♻️ **Modifications**
* **[Migration Cloudinary+S3 → R2 Fullstack]** : Migration du service de stockage et de CDN pour les médias.
    * `[Stockage]` : Migration vers Cloudflare R2
       * Suspension des connexions avec AWS S3 Bucket pour l'archivage
       * Suspension des connexions avec Cloudinary
       * Mise en place de Cloudflare R2 pour stockage et transformations des images
       * Mise en place du CDN sur img.shottt-media.com pour servir les images
       * Gain en rapport quotas/coûts, gain en qualité de service et disponibilité  

---
