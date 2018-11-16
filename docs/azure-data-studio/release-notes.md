---
title: Notes de publication Data Studio Azure | Microsoft Docs
description: Notes de publication Azure Data Studio
ms.custom: tools|sos
ms.date: 11/06/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9723a51154d0098271f8d3206c7f7a7470598422
ms.sourcegitcommit: 8cc38f14ec72f6f420479dc1b15eba64b1a58041
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51289919"
---
# <a name="azure-data-studio-release-notes"></a>Notes de publication Azure Data Studio

**[Téléchargez la version de novembre !](download.md)**

## <a name="november-2018-november-release"></a>Novembre 2018 (version de novembre)

date de publication : 6 novembre 2018  
version : 1.2.4

- Mettre à jour vers la [extension de la version préliminaire de SQL Server 2019](https://docs.microsoft.com/sql/azure-data-studio/sql-server-2019-extension?view=sql-server-ver15)
- Présentation de coller l’extension de Plan
- Présentation des extensions de requêtes de couleur haute, y compris de thème de l’éditeur SSMS
- Correctifs inclus dans les extensions de l’Agent SQL Server Profiler et importation
- Corriger les.Net Core à l’origine du problème Socket KeepAlive supprimé des connexions inactives sur macOS
- Service des outils SQL mise à niveau vers.Net Core 2,2 Preview 3 (pour une éventuelle prise en charge AAD)

### <a name="bug-fixes"></a>Correctifs de bogues
- Corriger [émettre #2933](https://github.com/Microsoft/azuredatastudio/issues/2933): perte de la connexion à la base de données SQL Azure
- Corriger [émettre #2914](https://github.com/Microsoft/azuredatastudio/issues/2914): exception de « Argument non valide » développant le nœud de base de données de l’Explorateur d’objets
- Corriger [émettre #2935](https://github.com/Microsoft/azuredatastudio/pull/2935): messages de plusieurs lignes s’affichent correctement dans les résultats de la requête
- Corriger [émettre #2906](https://github.com/Microsoft/azuredatastudio/pull/2906): nom du document de corriger la modification des données lorsque le nom de la table contient des caractères spéciaux
- Corriger [émettre #2929](https://github.com/Microsoft/azuredatastudio/issues/2929): créé dans l’extension de journal des modifications indique que vérifier les Notes de publication de VSCode pour les modifications
- Corriger [émettre #2719](https://github.com/Microsoft/azuredatastudio/issues/2719): thème à contraste élevé doubles/triplets icônes
- Corriger [émettre #3047](https://github.com/Microsoft/azuredatastudio/pull/3047): ajouter une interface de ligne de commande pour la connexion à un serveur SQL Server
- Corriger [émettre #3031](https://github.com/Microsoft/azuredatastudio/pull/3031): ajouter la prise en charge du thème query plan
- ...

Pour plus d’informations, consultez le [journal des modifications](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md), et [versions](https://github.com/Microsoft/azuredatastudio/releases).

## <a name="october-2018-october-release"></a>Octobre 2018 (version d’octobre)

date de publication : 29 octobre 2018  
version : 1.1.4

- Présentation de l’Explorateur de ressources Azure pour parcourir les bases de données SQL Azure
- Améliorer la robustesse de connectivité de l’Explorateur d’objets et de l’éditeur de requête
- Améliorations des extensions de l’Agent SQL
- Mettre à jour vers la [extension de la version préliminaire de SQL Server 2019](https://docs.microsoft.com/sql/azure-data-studio/sql-server-2019-extension?view=sql-server-ver15)

### <a name="bug-fixes"></a>Correctifs de bogues
- Corriger [émettre #2717](https://github.com/Microsoft/azuredatastudio/issues/2717): résultat de la colonne XML sur la mise en forme
- Corriger [émettre #2993](https://github.com/Microsoft/azuredatastudio/issues/2993): les fenêtres de résultats de la largeur est incomplète
- Corriger [émettre #2999](https://github.com/Microsoft/azuredatastudio/issues/2999): pas de charger le fichier System.Diagnostics.Tracing sur Mac lors de la connexion à la base de données
- Corriger [émettre #2851](https://github.com/Microsoft/azuredatastudio/issues/2851): TimeSeries graphique n’affiche pas correctement
- Corriger [émettre #2996](https://github.com/Microsoft/azuredatastudio/issues/2996): Temp de perte de la table en raison du changement de session soudaine
- ...

Pour plus d’informations, consultez le [journal des modifications](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md), et [versions](https://github.com/Microsoft/azuredatastudio/releases).

## <a name="september-2018-september-ga-release"></a>Septembre 2018 (version de septembre GA)

date de publication : 24 septembre 2018  
Version : 1.0

Version disponibilité générale d’Azure Data Studio (anciennement SQL Operations Studio).

- Annonce de l’extension de la version préliminaire de SQL Server 2019.
  - Prise en charge des fonctionnalités en version préliminaire de SQL Server 2019 notamment [cluster big data](../big-data-cluster/big-data-cluster-overview.md) prennent en charge.
    - Se connecter à la passerelle HDFS/Spark fournis avec la version préliminaire de SQL Server 2019.
    - Parcourir HDFS, de télécharger des fichiers, d’enregistrer des fichiers et de lancer des actions utiles telles que d’analyser dans le bloc-notes pour les fichiers CSV.
    - Envoyer des travaux Spark à partir du tableau de bord ou avec le bouton droit sur une connexion de HDFS/Spark dans l’Explorateur d’objets.
  - Azure Data Studio blocs-notes
    - Créez ou ouvrez des ordinateurs portables à l’aide d’une visionneuse de Notebook intégrée. Dans cette version du bloc-notes viewer prend en charge la connexion à noyaux locaux et de cluster SQL Server 2019 big data.
    - Utiliser les bibliothèques d’accélérateur de Code PROSE dans votre bloc-notes pour en savoir plus de types de données et de format de fichier pour la préparation des données rapide.
  - Explorateur de ressources Azure
    - La vue Explorateur de ressources Azure vous permet de parcourir les points de terminaison liées aux données de vos comptes Azure et créer des connexions avec eux dans l’Explorateur d’objets. Dans cette version prise en charge les serveurs et les bases de données SQL Azure.
  - Table externe Assistant de création de SQL Server PolyBase
    - Créer une table externe et ses structures de métadonnées de prise en charge avec un Assistant facile à utiliser. Dans cette version, les serveurs SQL Server et Oracle à distance sont pris en charge.
- Grille de résultats améliorations des performances et l’expérience utilisateur pour un grand nombre de jeux de résultats de requête.
- Visual Studio de Code source code Actualiser à partir de 1.23 à 1.26.1 avec disposition en grille et l’éditeur de paramètres amélioré (version préliminaire).
- Améliorations de l’accessibilité pour le lecteur d’écran, la navigation au clavier et à contraste élevé.
- Ajouté `Connection name` possibilité de fournir un nom d’affichage autre dans la vue-permettent de serveurs.

### <a name="bug-fixes"></a>Correctifs de bogues

- Corriger [émettre #2647](https://github.com/Microsoft/azuredatastudio/issues/143): les graphiques a pris un grand pas vers l’arrière.
- Corriger [émettre #2648](https://github.com/Microsoft/azuredatastudio/issues/143): SELECT qui retourne un lien hypertexte est JSON toute la colonne.
- ...

Pour plus d’informations, consultez le [journal des modifications](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md), et [versions](https://github.com/Microsoft/azuredatastudio/releases).


## <a name="august-2018-august-public-preview"></a>Août 2018 (préversion publique août)

date de publication : 30 août 2018  
version : 0.32.8

*0.32.8 contient des correctifs pour quelques régression trouvée dans 0.32.7 ([#1971](https://github.com/Microsoft/azuredatastudio/issues/1971), [#2372](https://github.com/Microsoft/azuredatastudio/issues/2372)*)

Le *version préliminaire publique d’août* se concentre sur les correctifs de bogues, stabilisation de produit et le remplissage des écarts dans les scénarios existants.  

- Annonce de l’Extension d’importation SQL Server
- Gestion des sessions de SQL Server Profiler
- Prise en charge des modèles de session SQL Server Profiler
- Améliorations de l’Agent SQL Server
- Nouvelle extension de la Communauté : premier kit de répondeur
- Améliorations de la qualité de vie : chaînes de connexion

### <a name="bug-fixes"></a>Correctifs de bogues

- Analyser SQL dans une fenêtre d’éditeur de requête à l’aide de la `Parse Syntax` commande.
- Corriger [émettre #143](https://github.com/Microsoft/azuredatastudio/issues/143): double-cliquez sur désélectionnez dans le nom de la variable.
- Corriger [émettre #387](https://github.com/Microsoft/azuredatastudio/issues/387): icône de base de données SQL onglet est rouge.
- Corriger [émettre #825](https://github.com/Microsoft/azuredatastudio/issues/825): demander : connexion automatique au serveur actuel après le Script en tant que... 
- Corriger [émettre #1278](https://github.com/Microsoft/azuredatastudio/issues/1278): sqlops.desktop [entrée du bureau] - valeur redondant pour nom & commentaire.
- Corriger [émettre #1285](https://github.com/Microsoft/azuredatastudio/issues/1285): la mise à jour entraîne l’icône d’application à être supprimé/remplacé dans Windows.
- Corriger [émettre #1317](https://github.com/Microsoft/azuredatastudio/issues/1317): corriger le séparateur décimal.
- Corriger [émettre #1474](https://github.com/Microsoft/azuredatastudio/issues/1474): Annuler Modifier la connexion déconnecte la connexion actuelle.
- Corriger [émettre #1497](https://github.com/Microsoft/azuredatastudio/issues/1497): vue en tant que graphique options sont tronquées en bas.
- Corriger [émettre #1524](https://github.com/Microsoft/azuredatastudio/issues/1524): Shell/tableau de bord : icônes de vues font Main sont déplaçables et peut se bloquer l’application.
- Corriger [émettre #1578](https://github.com/Microsoft/azuredatastudio/issues/1578): Impossible de développer/réduire le dossier de navigateur de fichier distant en cliquant sur le nom.
- Corriger [émettre #1620](https://github.com/Microsoft/azuredatastudio/issues/1620): Suggestion de fonctionnalité : obtenir la chaîne de connexion pour la connexion existante.
- Corriger [émettre #1624](https://github.com/Microsoft/azuredatastudio/issues/1624): SelectBox ne change pas lorsque désactivé.
- Corriger [émettre #1728](https://github.com/Microsoft/azuredatastudio/issues/1728): enregistrer en tant que JSON/EXCEL/CSV non professionnel.
- Corriger [émettre #1744](https://github.com/Microsoft/azuredatastudio/issues/1744): volet des résultats perd ses positions de défilement quand vous basculez entre les onglets.
- Corriger [émettre #1748](https://github.com/Microsoft/azuredatastudio/issues/1748): message d’erreur lors de l’enregistrement d’heure de fichier deuxième (et ultérieures) Excel.
- Corriger [émettre #1782](https://github.com/Microsoft/azuredatastudio/issues/1782): modifier des données : cellule ne revert à la valeur d’origine sur appuyant sur la touche ÉCHAP.
- Corriger [émettre #1836](https://github.com/Microsoft/azuredatastudio/issues/1836): fichiers .sql non associés à SQL Operations Studio.
- Corriger [émettre #1850](https://github.com/Microsoft/azuredatastudio/issues/1850): N en tapant « remplissage automatique des N'' '.
- Corriger [émettre #1985](https://github.com/Microsoft/azuredatastudio/issues/1985): copie à partir de la grille de résultats de requête est désactivée par la 1 colonne.
- Corriger [émettre #1998](htpts://github.com/Microsoft/azuredatastudio/pull/1998): version d’ajouter du Code Visual Studio à sur la boîte de dialogue.
- Corriger [émettre #2042](https://github.com/Microsoft/azuredatastudio/pull/2042): l’Agent : bouton activé pour importer des requêtes à partir de fichiers sql.
- Corriger [émettre #2091](https://github.com/Microsoft/azuredatastudio/issues/2091): Impossible d’utiliser le raccourci de Ctrl + C pour copier à partir du volet de résultats.
- Corriger [émettre #2099](https://github.com/Microsoft/azuredatastudio/pull/2099): ajout de plusieurs options saveAsCsv.
- Corriger [émettre #2107](https://github.com/Microsoft/azuredatastudio/issues/2107): icône de document de mise à jour pour les documents de tableau de bord et de Profiler.
- Corriger [émettre #2129](https://github.com/Microsoft/azuredatastudio/pull/2129): enregistrement des données de modifier la position de défilement lors du changement.
- Corriger [émettre #2152](https://github.com/Microsoft/azuredatastudio/issues/2152): résultats de grille ligne indicateur zéro basée.

## <a name="known-issues"></a>Problèmes connus

- [Problème #2371](https://github.com/Microsoft/azuredatastudio/issues/2371) enregistrer comme Excel uniquement enregistre première ligne de données
- [Problème #2150](https://github.com/Microsoft/azuredatastudio/issues/2150): Impossible de se connecter sur Ubuntu 16.04 to SQL dans un conteneur


## <a name="july-2018-july-public-preview"></a>Juillet 2018 (préversion publique de juillet)

date de publication : 19 juillet 2018  
version : 0.31.4

Le *préliminaire de juillet* se concentre sur la version initiale des scénarios de configuration de l’Agent SQL Server, des améliorations de modèle de session et la vue SQL Server Profiler et permanent de correctifs de bogues pour le client a signalé des problèmes GitHub. Cette version contient les points importants suivants :  

- [SQL Server Agent pour l’extension de SQL Operations Studio](sql-server-agent-extension.md) améliorations
 - Ajout d’affichage des alertes, des opérateurs et des proxys et des icônes sur le volet gauche
 - Boîtes de dialogue Ajout pour le nouveau travail nouvelle étape du travail, nouvelle alerte et New, opérateur
 - Ajout Delete Job, supprimer l’alerte et Delete (opérateur) (clic droit)
 - Visualisation d’exécutions précédentes ajoutée
 - Ajout de filtres pour chaque nom de colonne
- [SQL Server Profiler pour l’extension de SQL Operations Studio](sql-server-profiler-extension.md) améliorations
 - Touches d’accès rapide ajoutés rapidement lancer et démarrer/arrêter Profiler
 - Ajout des modèles par défaut 5 pour afficher les événements étendus
 - Nom de connexion de serveur/base de données ajouté
 - Prise en charge pour les instances de base de données SQL Azure
 - Ajout de suggestion pour quitter Profiler lors de l’onglet est fermé lorsque Profiler est en cours d’exécution
- Version de l’Extension des Scripts de combinaison
- Assistant et l’extensibilité de la boîte de dialogue points ajoutées pour les auteurs de l’Extension
- Résoudre les problèmes de GitHub :
 - Corriger [émettre 728](https://github.com/Microsoft/azuredatastudio/issues/728): aucune réponse pour ajouter une connexion sur macOS
 - Corriger [émettre 1612](https://github.com/Microsoft/azuredatastudio/issues/1612): affichage de texte de grille de résultats est désordre par des caractères internationaux
 - Corriger [émettre 1693](https://github.com/Microsoft/azuredatastudio/issues/1693): boîte de dialogue de sauvegarde : interface utilisateur du navigateur de fichier est interrompue
 - Corriger [émettre 1713](https://github.com/Microsoft/azuredatastudio/issues/1713): nombre de lignes affectées
 - Corriger [émettre 1718](https://github.com/Microsoft/azuredatastudio/issues/1718): Impossible de se connecter à une source de données
 - Corriger [émettre 1719](https://github.com/Microsoft/azuredatastudio/issues/1719): TypeError lors de la connexion au serveur
 - Corriger [émettre 1724](https://github.com/Microsoft/azuredatastudio/issues/1724): boîtes de dialogue Extension ont cessé de fonctionner
 - Corriger [émettre 1749](https://github.com/Microsoft/azuredatastudio/issues/1749): bogue : données HTML dans une colonne sont ensuite interprétées
 - Corriger [émettre 1789](https://github.com/Microsoft/azuredatastudio/issues/1789): extensibilité : Si vous ajoutez un fournisseur de connexion désinstaller jamais supprimerons dans la liste
 - Corriger [émettre 1791](https://github.com/Microsoft/azuredatastudio/issues/1791): Sqlops Extensions : queryeditor.connect() se connecte à la base de données cible, mais l’interface utilisateur n’affiche pas l’éditeur est connecté
 - Corriger [émettre 1799](https://github.com/Microsoft/azuredatastudio/issues/1799): graphique de taille de base de données de 10 haut ne fonctionne pas sur les instances de la casse
 - Corriger [émettre 1814](https://github.com/Microsoft/azuredatastudio/issues/1814): définition de type de faute de frappe sqlops.d.ts à l’origine implicite 'any'
 - Corriger [émettre 1817](https://github.com/Microsoft/azuredatastudio/issues/1817): erreur de Ortografia
 - Corriger [émettre 1830](https://github.com/Microsoft/azuredatastudio/issues/1830): paramètre iconPath dans ButtonComponent après l’appel de component() ne change pas l’icône
 - Corriger [émettre 1843](https://github.com/Microsoft/azuredatastudio/issues/1843): organisation d’une meilleure Table


## <a name="june-2018-june-public-preview"></a>Juin 2018 (aperçu Public de juin)

date de publication : 20 juin 2018  
version : 0.30.6

Le *préliminaire de juin* contient les points importants suivants :  

- **SQL Server Profiler pour SQL Operations Studio *aperçu***  version initiale d’extension.
- La nouvelle **SQL Data Warehouse** extension inclut des widgets de tableau de bord personnalisable riche en exposant des insights à votre entrepôt de données. Ceci permet de déverrouiller des scénarios clés de gestion et votre entrepôt de données pour vous assurer qu’il est optimisé pour des performances cohérentes.
- **Modifier les données de « Filtrage et tri »** prennent en charge.
- **L’Agent SQL Server pour SQL Operations Studio *aperçu***  améliorations d’extension pour les travaux et l’historique des travaux vues.
- Amélioration de **Assistant & infrastructure de générateur de l’interface utilisateur de boîte de dialogue** API d’extensibilité.
- Mettre à jour l’intégration de Visual Studio Code plateforme source code [mars 2018 (1.22)](https://code.visualstudio.com/updates/v1_22) et [avril 2018 (1.23)](https://code.visualstudio.com/updates/v1_23) libère.
- Résoudre les problèmes de GitHub :
  - Demande de fonctionnalité ([émettre 1204](https://github.com/Microsoft/azuredatastudio/issues/1204)) : Veuillez mettre les résultats de la largeur de colonne de l’ajustement automatique de la grille données et/ou n’oubliez pas de modifications manuelles si la même requête est relancée.
  - Corriger [émettre 1398](https://github.com/Microsoft/azuredatastudio/issues/1398): show doit ajouter de message et le bouton Ajouter un compte compte lorsque compte lié est vide.
  - Corriger [émettre 1399](https://github.com/Microsoft/azuredatastudio/issues/1399): onglet compte lié est interrompue lorsque la vue est réduite.
  - Corriger [émettre 1374](https://github.com/Microsoft/azuredatastudio/issues/1374): SQL outils Service tombe en panne lors de l’ouverture du fichier .sql à partir du disque.
  - Corriger [émettre 1372](https://github.com/Microsoft/azuredatastudio/issues/1372): mot clé « BETWEEN » de SQL manquant.
  - Corriger [émettre 1395](https://github.com/Microsoft/azuredatastudio/issues/1395): mot clé « Correspondance » bloque le Service des outils SQL.
  - Corriger [émettre 1496](https://github.com/Microsoft/azuredatastudio/issues/1496): option de menu contextuel « Nouveau Profiler » dans l’Explorateur d’objets n’a aucun effet.
  - Corriger [émettre 1495](https://github.com/Microsoft/azuredatastudio/issues/1495): plan de requête de requête éditeur « Explain » est interrompue.


## <a name="may-2018-may-public-preview"></a>Mai 2018 (version préliminaire publique de mai)

date de publication : 7 mai 2018  
version : 0.29.3

Le *préliminaire peut* se concentre sur la stabilisation et de correctifs de bogues. Cette build contient les points importants suivants :  

- Annonce l’extension de Redgate SQL Search est disponible dans le Gestionnaire d’extensions.
- Localisation de la Communauté disponible dans 10 langues : allemand, espagnol, Français, italien, japonais, coréen, portugais, russe, chinois simplifié et chinois traditionnel.
- Collecte des informations télémétriques réduite, annulations améliore l’expérience et des liens dans le produit à la déclaration de confidentialité.
- Gestionnaire d’extensions a amélioré la place de marché d’expérience pour découvrir facilement des extensions de la Communauté.
- Travaux d’extension de l’Agent SQL et l’historique des travaux afficher amélioration du produit.
- Met à jour des extensions pour whoisactive et les rapports de serveur.
- Améliorer le défilement de gérer les propriétés de tableau de bord.
- Résoudre les problèmes de GitHub :
   - Corriger [émettre 703](https://github.com/Microsoft/azuredatastudio/issues/703): entrée de texte HTML similaire dans modifier des données entraîne la valeur à afficher incorrectement jusqu'à ce que l’actualisation
   - Corriger [émettre 821](https://github.com/Microsoft/azuredatastudio/issues/821): dépendance de package azuredatastudio.deb
   - Corriger [émettre 1260](https://github.com/Microsoft/azuredatastudio/issues/1260): mot clé « distinct » pas mis en surbrillance
   - Corriger [émettre 1332](https://github.com/Microsoft/azuredatastudio/issues/1332): modifier des données rétablir ligne ne fonctionne pas
   - Corriger [émettre 1215](https://github.com/Microsoft/azuredatastudio/issues/1215): extension de l’Agent SQL et de la barre d’état
   - Corriger [émettre 1316](https://github.com/Microsoft/azuredatastudio/issues/1316): SQL Agent ne redimensionnez après modifier la taille de windows




## <a name="april-2018-april-public-preview"></a>Avril 2018 (aperçu Public d’avril)

date de publication : 25 avril 2018  
version : 0.28.6

Le *version préliminaire publique avril* contient des correctifs de bogues et améliorations. 

- Améliorations apportées à l’extension de l’aperçu de l’Agent SQL.
- Prise en charge des fichiers volumineux et protégé pour l’enregistrement d’administrateur protégé améliorée et > fichiers 256M dans SQL Operations Studio.
- Terminal intégré fractionnement pour travailler avec plusieurs terminaux ouverts à la fois.
- Pied de nombre de fichier sur disque installation réduite d’impression pour des installations plus rapides et les heures de démarrage.
- Continuer à résoudre les problèmes de GitHub :
   - Corriger [émettre 37](https://github.com/Microsoft/azuredatastudio/issues/37): lorsque la visionneuse de graphique génère une erreur, un comportement inattendu se produit.
   - Corriger [émettre 462](https://github.com/Microsoft/azuredatastudio/issues/462): demande de fonctionnalité : Option pour les groupes de serveurs à être développé par défaut.
   - Corriger [émettre 606](https://github.com/Microsoft/azuredatastudio/issues/606): intellisense - suggestion incorrecte pour la commande « update ».
   - Corriger [émettre 967](https://github.com/Microsoft/azuredatastudio/issues/967): attendez le plan de requête lorsque sélectionnez showplan XML dans la grille de résultats.
   - Corriger [émettre 1023](https://github.com/Microsoft/azuredatastudio/issues/1023): ajouter des crochets pour ms_foreachdb appel à partir de flyfishingdba.
   - Corriger [émettre 1048](https://github.com/Microsoft/azuredatastudio/issues/1048): erreur de négociation de préconnexion SSL/TLS.
   - Corriger [émettre 1050](https://github.com/Microsoft/azuredatastudio/issues/1050): afficher les insights clair avant d’afficher l’erreur.
   - Corriger [émettre 1057](https://github.com/Microsoft/azuredatastudio/issues/1057): nouvelles actions de requête dans le widget d’explorer et de restauration sont interrompues.
   - Corriger [émettre 1068](https://github.com/Microsoft/azuredatastudio/issues/1068): sortie de tableau de bord pop-up windows avec le message d’erreur pour la base de données SQL Azure.
   - Corriger [émettre 1069](https://github.com/Microsoft/azuredatastudio/issues/1069): boîte de dialogue Connexion affiche une erreur de serveur requis lors de l’affichage initial.
   - Corriger [émettre 1070](https://github.com/Microsoft/azuredatastudio/issues/1070): groupes de serveurs nécessitent désormais un double-clic pour développer.
   - Corriger [émettre 1072](https://github.com/Microsoft/azuredatastudio/issues/1072): arrière-plan du contrôle sélectionné est semi-transparent.
   - Corriger [émettre 1115](https://github.com/Microsoft/azuredatastudio/issues/1115): résoudre des problèmes d’accessibilité Contraste élevé tous les dans SQL Operations Studio.
   - Corriger [émettre 1101](https://github.com/Microsoft/azuredatastudio/issues/1101): Échec de l’Extension au lien de mise à niveau « télécharger manuellement » accède à un emplacement incorrect.
   - Corriger [émettre 1103](https://github.com/Microsoft/azuredatastudio/issues/1103): défilement V ne fonctionne ne pas dans l’onglet Accueil.
   - Corriger [émettre 1104](https://github.com/Microsoft/azuredatastudio/issues/1104): onglets de l’extension SQL a cessé de fonctionner.


Une importante mise en surbrillance de la préversion publique d’avril est l’actualisation de code de source de plateforme 1.21 de Code Visual Studio. Cela offre plusieurs mises à jour l’éditeur principal et workbench à partir du point de 1.19 synchronisation précédente. Voici quelques exemples :

- [Nouvelle interface utilisateur de Notifications](https://code.visualstudio.com/updates/v1_21#_new-notifications-ui) - facilement gérer et passez en revue les notifications SQL Operations Studio.
- [Intégré fractionnement Terminal](https://code.visualstudio.com/updates/v1_21#_split-terminals) -travailler avec plusieurs terminaux ouverts à la fois.
- [Enregistrer des fichiers volumineux et protégés](https://code.visualstudio.com/updates/v1_20#_save-files-that-need-admin-privileges) - permet d’enregistrer l’administrateur protégé et > fichiers 256 M dans SQL Operations Studio.
- [Prise en charge des fichiers volumineux améliorée](https://code.visualstudio.com/updates/v1_21#_text-buffer-improvements) -optimisations de mémoire tampon de texte pour les fichiers volumineux.
- [Recherche de paramètres améliorée](https://code.visualstudio.com/updates/v1_20#_settings-search) - facilement trouver le paramètre de droite avec la recherche en langage naturel.
- [Extraits de code globales](https://code.visualstudio.com/updates/v1_20#_global-snippets) -créer des extraits de code que vous pouvez utiliser pour tous les types de fichier.
- [Sélection multiple Explorer](https://code.visualstudio.com/updates/v1_20#_multi-select-in-the-explorer) -effectuer des actions sur plusieurs fichiers à la fois.
- [Erreurs et avertissements dans l’Explorateur de](https://code.visualstudio.com/updates/v1_20#_error-indicators-in-the-explorer) - rapidement accéder aux erreurs dans votre base de code.
- [Faites glisser et supprimer, copier et coller entre des fenêtres](https://code.visualstudio.com/updates/v1_21#_better-drag-and-drop-support) -déplacer des fichiers entre les fenêtres ouvertes de SQL Operations Studio.
- [Prise en charge du sous-module GIT](https://code.visualstudio.com/updates/v1_20#_git-submodules) -Git effectuer des opérations sur des dépôts Git imbriquées.
- [Prise en charge du lecteur de l’écran de terminal](https://code.visualstudio.com/updates/v1_20#_screen-reader-support) -Terminal intégré a maintenant le mode « Écran lecteur optimisé ».
- [Mise en page centrée éditeur](https://code.visualstudio.com/updates/v1_21#_centered-editor-layout) -optimiser votre écran d’affichage du code.
- [Résultats de la recherche horizontal (version préliminaire)](https://code.visualstudio.com/updates/v1_21#_horizontal-search) -vous pouvez maintenant afficher les résultats de recherche dans un volet horizontal.

Pour plus d’informations, extraction le [Notes de publication Visual Studio Code février](https://code.visualstudio.com/updates/v1_21)et le [Notes de publication Visual Studio Code janvier](https://code.visualstudio.com/updates/v1_20).

Pour plus d’informations, consultez le [journal des modifications](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md).

## <a name="march-2018-march-public-preview"></a>Mars 2018 (préversion publique mars)

date de publication : 28 mars 2018  
version : 0.27.3

Le *version préliminaire publique mars* continue à résoudre les principaux problèmes de GitHub et se concentre sur l’amélioration de notre histoire d’extensibilité. Plus précisément l’activation de gestionnaire d’extensions, amélioration de la gestion du tableau de bord et en fournissant l’Agent SQL et les extensions d’insights. Cette version inclut les améliorations suivantes :

- Améliorer le modèle d’extensibilité de tableau de bord pour prendre en charge des insights à onglets et volets de configuration.
   - Gestionnaire d’extensions permet simple d’acquisition des extensions.
   - Extensions de tableau de bord pour sp_whoisactive de [whoisactive.com](http://www.whoisactive.com).
   - Pour plus d’informations, consultez [étendre les fonctionnalités de SQL Operations Studio](extensions.md).
- Ajoutez d’autres [API d’extensibilité pour la connexion et l’objet explorer](https://github.com/Microsoft/azuredatastudio/wiki/Extensibility-API) gestion.
- Continuer à résoudre des clients importants ayant un impact sur [problèmes GitHub](https://github.com/Microsoft/azuredatastudio/issues).


## <a name="february-2018-february-public-preview"></a>Février 2018 (préversion publique février)

date de publication : 15 février 2018  
version : 0.26.7

Le *préliminaire de février* inclut des suggestions de fonctionnalités et les correctifs de bogues de priorité élevée. Cette version inclut les améliorations suivantes :

- Présentation d’Installation de mise à jour automatique, qui fournit une notification lorsqu’une nouvelle version est disponible au téléchargement 
- La boîte de dialogue de connexion 'Database' champ est désormais une liste déroulante remplie dynamiquement qui contient une liste de bases de données rempli à partir du serveur spécifié.
- Corriger [n° 6](https://github.com/Microsoft/azuredatastudio/issues/6): conserver la connexion et la base de données sélectionnée lors de l’ouverture de nouveaux onglets de requête.
- Corriger [numéro 22](https://github.com/Microsoft/azuredatastudio/issues/22): « Server Name » et « Nom de la base de données » - peut ces zones de liste déroulante au lieu de zones de texte ?
- Corriger [émettre 549](https://github.com/Microsoft/azuredatastudio/issues/549): installation sans assistance en mode silencieux/très résulte dans une application qui ouvre après l’installation.
- Corriger [émettre 481](https://github.com/Microsoft/azuredatastudio/issues/481): ajouter l’option « Vérifier les mises à jour ».
- Colorisation de l’éditeur SQL et les correctifs de la saisie semi-automatique :
   - Corriger [émettre 584](https://github.com/Microsoft/azuredatastudio/issues/584): mot clé « Complet » pas mis en surbrillance par IntelliSense.
   - Corriger [émettre 345](https://github.com/Microsoft/azuredatastudio/issues/345): fonctions SQL mettre en couleur dans l’éditeur.
   - Corriger [émettre 300](https://github.com/Microsoft/azuredatastudio/issues/300): [#tempData] dernière «] » affichera la couleur verte.
   - Corriger [émettre 225](https://github.com/Microsoft/azuredatastudio/issues/225): incompatibilité de couleur de mot clé.
   - Corriger [émettre 60](https://github.com/Microsoft/azuredatastudio/issues/60): sql non valide syntaxe couleur mise en surbrillance lorsque vous utilisez une table temporaire dans la clause from.
- Introduire des API d’extensibilité de connexion.
- Intégration VS 1.19 d’éditeur de Code.
- Mettre à jour les composant JustinPealing/html-plan de requête pour la prise en charge plusieurs améliorations de l’Observateur de Plan de requête.


## <a name="january-2018-january-public-preview"></a>Janvier 2018 (préversion publique janvier)

date de publication : 17 janvier 2018  
version : 0.25.4

Le *préliminaire de janvier* inclut des suggestions de fonctionnalités et les correctifs de bogues de priorité élevée. Cette version inclut les améliorations suivantes :

- Les connexions serveur enregistrées sont disponibles dans la boîte de dialogue de connexion.
- Activer la sortie à chaud. Sortie à chaud est désactivée par défaut, pour permettre de voir [paramètre de sortie à chaud](settings.md#hot-exit).
- La coloration d’onglet basée sur le groupe de serveurs. La coloration d’onglet est désactivé par défaut, pour permettre de voir [onglet paramètre des couleurs](settings.md#tab-color).
- Modification *nom du serveur* à *Server* dans la boîte de dialogue de connexion.
- Résoudre interrompu *exécuter la requête actuelle* commande.
- Corriger la rupture de glisser-déplacer bogue de script.
- Correctif incorrect épinglé icône du Menu Démarrer.
- Corriger le compte Azure manquant icône de marque.


## <a name="december-2017-december-public-preview"></a>Décembre 2017 (préversion publique décembre)

date de publication : 19 décembre 2017  
version : 0.24.1

Le *préliminaire de décembre* comprend plusieurs correctifs de bogues sur toutes les zones de fonctionnalité, ainsi que les améliorations suivantes :

- Créer boîte de dialogue règle de pare-feu est désormais disponible pour faciliter la connexion à la base de données SQL Azure et Azure SQL Data Warehouse.
- Ajouté le programme d’installation Windows et les packages d’installation Linux DEB et tr/min.
- Gérer l’éditeur de disposition visuelle du tableau de bord.
- *Script en tant que Alter* et *Script comme exécuter* commandes.
- *Exécutez la requête en cours avec le Plan réel* commande.
- Intégrer la plateforme d’éditeur Visual Studio Code 1.18.1.
- Activer les fichiers de chargement de version test d’une Extension VSIX.
- Prend en charge la syntaxe d’itération lot « GO N ».


## <a name="november-2017"></a>Novembre 2017

date de publication : 15 novembre 2017  
version : 0.23.6

- Version initiale du [!INCLUDE[name-sos](../includes/name-sos-short.md)].


## <a name="next-steps"></a>Étapes suivantes

Consultez les Démarrages rapides suivants pour commencer :
- [Connexion & interrogation de SQL Server](quickstart-sql-server.md)
- [Connexion & interrogation de base de données SQL Azure](quickstart-sql-database.md)
- [Connexion & interrogation d’entrepôt de données Azure](quickstart-sql-dw.md)

Contribuer à [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/azuredatastudio](https://github.com/Microsoft/azuredatastudio)
