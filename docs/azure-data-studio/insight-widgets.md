---
title: Utiliser des widgets d’analyse pour surveiller les serveurs et bases de données
titleSuffix: Azure Data Studio
description: En savoir plus sur les widgets d’analyse dans Azure Data Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7fa7317d048d2bb9e19b6e82f5323a3b8ed15751
ms.sourcegitcommit: 189a28785075cd7018c98e9625c69225a7ae0777
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53030193"
---
# <a name="manage-servers-and-databases-with-insight-widgets-in-includename-sosincludesname-sos-shortmd"></a>Gérer les serveurs et bases de données avec des widgets d’analyse dans [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Widgets d’analyse prennent les requêtes Transact-SQL (T-SQL) vous permet de surveiller les serveurs et bases de données et les transforme en visualisations pertinentes. 

Insights sont personnalisables des graphiques que vous ajoutez au serveur et base de données des tableaux de bord de surveillance. Afficher une vue d’ensemble de vos serveurs et les bases de données, puis d’Explorer plus en détail et de lancer des actions de gestion que vous définissez. 

Vous pouvez générer awesome serveur et base de données de gestion des tableaux de bord similaire à l’exemple suivant :

![tableau de bord de base de données](media/insight-widgets/database-dashboard.png)


Pour lancer et commencer à créer différents types de widgets d’analyse, consultez les didacticiels suivants :

- [Générer un widget d’analyse personnalisée](tutorial-build-custom-insight-sql-server.md)
- *Activer les widgets d’analyse intégrées*
   - [Activer la surveillance d’un aperçu des performances](tutorial-qds-sql-server.md)
   - [Activer l’analyse de l’utilisation d’espace de table](tutorial-table-space-sql-server.md)


## <a name="sql-queries"></a>Requêtes SQL 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] tente d’éviter d’introduire encore un autre utilisateur de langage ou lourde interface afin d’essayer d’utiliser autant que possible le T-SQL avec une configuration minimale JSON. Configuration des widgets d’analyse avec T-SQL s’appuie sur le nombre un nombre illimité de sources existantes de requêtes T-SQL utiles qui peuvent être activés dans les widgets pertinents.

Widgets d’analyse sont composés d’un ou deux requêtes T-SQL :
* *Requête de widget Insight* est obligatoire et est la requête qui retourne les données qui apparaissent dans le widget.
* *Requête de détails Insight* est nécessaire uniquement si vous créez une page de détails de l’analyse.

Une requête de widget insight définit un jeu de données qui restitue un nombre, un graphique ou un graphique. Requête de détails Insight est utilisé pour répertorier les informations de détail d’insight pertinent dans un format tabulaire dans le volet de détails d’un aperçu. 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] exécute des requêtes de widget insight et mappe le jeu de résultats de requête au jeu de données d’un graphique, puis effectue le rendu. Quand les utilisateurs ouvrent les détails d’une information, il exécute la requête de détails insight et imprime le résultat dans une vue de grille dans la boîte de dialogue.

Le principe fondamental consiste à écrire une requête T-SQL de manière afin qu’il peut être utilisé comme un jeu de données d’un nombre, le graphique et le widget de graphique. 

## <a name="summary"></a>Résumé

La requête T-SQL et son jeu de résultats déterminent le comportement de widget insight. Écriture d’une requête pour un type de graphique ou le mappage d’un type de graphique pour la requête existante est la principale considération pour générer un widget d’insight efficace.



## <a name="additional-resources"></a>Ressources supplémentaires
- [Éditeur de requête](tutorial-sql-editor.md)

