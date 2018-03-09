---
title: "Notes de publication Microsoft SQL Studio Operations (version préliminaire) | Documents Microsoft"
description: "Notes de publication Microsoft SQL Studio Operations (version préliminaire)"
ms.custom: tools|sos
ms.date: 02/15/2018
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1b8c5e3cce8f84f0565c764a47d3f3b7c1709454
ms.sourcegitcommit: 4edac878b4751efa57601fe263c6b787b391bc7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2018
---
# <a name="sql-operations-studio-preview-release-notes"></a>Notes de publication SQL opérations Studio (version préliminaire)

**[Télécharger la version préliminaire publique de février](download.md)**

## <a name="february-2018-february-public-preview"></a>Février 2018 (février version préliminaire publique)

date de publication : le 15 février 2018  
version : 0.26.7

Le *Public Preview de février* inclut des suggestions de fonctionnalités et les correctifs de bogues de priorité élevée. Cette version inclut les améliorations suivantes :

- Présentation d’Installation de la mise à jour automatique, qui fournit une notification lorsqu’une nouvelle version est disponible en téléchargement 
- La boîte de dialogue de connexion 'Database' champ est désormais une liste déroulante remplie dynamiquement qui contient la liste des bases de données rempli à partir du serveur spécifié.
- Corriger [émettre 6](https://github.com/Microsoft/sqlopsstudio/issues/6): conserver la connexion et la base de données sélectionnée lors de l’ouverture de nouveaux onglets de requête.
- Corriger [numéro 22](https://github.com/Microsoft/sqlopsstudio/issues/22): 'Nom_serveur' et 'Nom de la base de données' - peut ces zones de liste déroulante au lieu de zones de texte ?
- Corriger [émettre 549](https://github.com/Microsoft/sqlopsstudio/issues/549): installation sans assistance en mode silencieux/très entraîne l’application qui ouvre après l’installation.
- Corriger [émettre 481](https://github.com/Microsoft/sqlopsstudio/issues/481): ajouter l’option de « Vérifier les mises à jour ».
- Éditeur SQL colorisation et la saisie semi-automatique des correctifs :
   - Corriger [émettre 584](https://github.com/Microsoft/sqlopsstudio/issues/584): mot clé « Complet » pas mis en surbrillance par IntelliSense.
   - Corriger [émettre 345](https://github.com/Microsoft/sqlopsstudio/issues/345): fonctions SQL de colorisation dans l’éditeur.
   - Corriger [émettre 300](https://github.com/Microsoft/sqlopsstudio/issues/300): [#tempData] dernières «] » affiche la couleur verte.
   - Corriger [émettre 225](https://github.com/Microsoft/sqlopsstudio/issues/225): incompatibilité de couleur de mot clé.
   - Corriger [émettre 60](https://github.com/Microsoft/sqlopsstudio/issues/60): sql non valide couleur mise en évidence lors de l’utilisation d’une table temporaire dans la clause from.
- Introduire des API d’extensibilité de connexion.
- Intégration de 1.19 de l’éditeur de Code Visual Studio.
- Mettre à jour les composants JustinPealing/html-plan de requête utilisent plusieurs améliorations de l’Observateur de Plan de requête.


## <a name="january-2018-january-public-preview"></a>Janvier 2018 (janvier version préliminaire publique)

date de publication : le 17 janvier 2018  
version : 0.25.4

Le *préliminaire de janvier* inclut des suggestions de fonctionnalités et les correctifs de bogues de priorité élevée. Cette version inclut les améliorations suivantes :

- Les connexions serveur enregistrées sont disponibles dans la boîte de dialogue de connexion.
- Activer la sortie à chaud. Sortie à chaud est désactivée par défaut, pour permettre de voir [paramètre de sortie à chaud](settings.md#hot-exit).
- La coloration d’onglet basée sur le groupe de serveurs. La coloration d’onglet est désactivé par défaut, pour permettre de voir [onglet paramètre des couleurs](settings.md#tab-color).
- Modification *nom du serveur* à *Server* dans la boîte de dialogue de connexion.
- Résoudre interrompu *exécuter la requête en cours* commande.
- Corrigez la rupture de glisser-déposer bogue de script.
- Correctif incorrect épinglé icône du Menu Démarrer.
- Corrigez le compte Azure manquant icône de marque.

Pour plus d’informations, consultez la [journal des modifications](https://github.com/Microsoft/sqlopsstudio/blob/master/CHANGELOG.md).


## <a name="december-2017-december-public-preview"></a>Décembre 2017 (préliminaire de décembre)

date de publication : 19 décembre 2017  
version : 0.24.1

Le *préliminaire de décembre* comprend plusieurs correctifs de bogues sur toutes les zones de fonctionnalité, ainsi que les améliorations suivantes :

- Créer boîte de dialogue règle de pare-feu est désormais disponible pour faciliter la connexion à la base de données SQL Azure et Azure SQL Data Warehouse.
- Ajout d’installation de Windows et Linux DEB et RPM packages d’installation.
- Gérer l’éditeur de présentation visuelle du tableau de bord.
- *Script en tant que Alter* et *Script en tant qu’exécutez* commandes.
- *Exécuter la requête en cours avec le Plan réel* commande.
- Intégrer la plateforme de l’éditeur VS Code 1.18.1.
- Activer les fichiers de chargement de version test d’une Extension VSIX.
- Prend en charge la syntaxe d’itération lot « GO N ».


## <a name="november-2017"></a>Novembre 2017

date de publication : 15 novembre 2017  
version : 0.23.6

- Version d’initiale [!INCLUDE[name-sos](../includes/name-sos-short.md)].


## <a name="next-steps"></a>Étapes suivantes

Consultez une des Démarrages rapides suivants pour commencer :
- [Se connecter et de requêtes SQL Server](quickstart-sql-server.md)
- [Se connecter et interroger la base de données SQL Azure](quickstart-sql-database.md)
- [Connecter la re & quête d’entrepôt de données Azure](quickstart-sql-dw.md)

Contribuer à [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio)
