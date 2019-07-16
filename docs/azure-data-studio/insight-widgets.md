---
title: Utiliser des widgets d’analyse dans Studio de données Azure pour surveiller les serveurs et bases de données
titleSuffix: Azure Data Studio
description: En savoir plus sur les widgets d’analyse dans Azure Data Studio
ms.custom: seodec18, sqlfreshmay19
ms.date: 05/14/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
ms.openlocfilehash: c1ab90efa97878676b1adc2a62579527407d6ba6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959526"
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

