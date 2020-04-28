---
title: Utilisation des données de catalogue | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog data [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], using catalog data
ms.assetid: d5915d0c-eec3-4382-850e-bd863763c99a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 429d42d4a82d0f9f34e33eb4f5f3293100505da9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306810"
---
# <a name="uses-of-catalog-data"></a>Utilisations des données du catalogue
Les applications utilisent des données de catalogue de différentes façons. Voici quelques utilisations courantes :  
  
-   **Construction d’instructions SQL au moment de l’exécution.** Les applications verticales, telles qu’une application de saisie de commandes, contiennent des instructions SQL codées en dur. Les tables et les colonnes utilisées par l’application sont corrigées à l’avance, comme les instructions qui accèdent à ces tables. Par exemple, une application d’entrée de commande contient généralement une seule instruction **Insert** paramétrable pour l’ajout de nouvelles commandes au système.  
  
     Les applications génériques, telles qu’un programme de feuille de calcul qui utilise ODBC pour récupérer des données, construisent souvent des instructions SQL au moment de l’exécution en fonction de l’entrée de l’utilisateur. Une telle application peut demander à l’utilisateur de taper les noms des tables et des colonnes à utiliser. Toutefois, il serait plus facile pour l’utilisateur de faire en sorte que l’application affiche des listes de tables et de colonnes à partir desquelles l’utilisateur peut effectuer des sélections. Pour générer ces listes, l’application doit appeler les fonctions de catalogue **SQLTables** et **SQLColumns** .  
  
-   **Construction d’instructions SQL pendant le développement.** Les environnements de développement d’applications permettent généralement au programmeur de créer des requêtes de base de données lors du développement d’un programme. Les requêtes sont ensuite codées en dur dans l’application en cours de génération.  
  
     De tels environnements pouvaient également utiliser **SQLTables** et **SQLColumns** pour créer des listes à partir desquelles le programmeur peut effectuer des sélections. Ces environnements peuvent également utiliser **SQLPrimaryKeys** et **SQLForeignKeys** pour déterminer automatiquement et afficher les relations entre les tables sélectionnées, et utiliser **SQLStatistics** pour déterminer et mettre en évidence les champs indexés afin que le programmeur puisse créer des requêtes efficaces.  
  
-   **Construction de curseurs.** Une application, un pilote ou un intergiciel (middleware) qui fournit un moteur de curseur à défilement peut utiliser **SQLSpecialColumns** pour déterminer la ou les colonnes qui identifient une ligne de manière unique. Le programme peut générer un *jeu de clés* contenant les valeurs de ces colonnes pour chaque ligne extraite. Lorsque l’application fait défiler vers la ligne, elle utilise ces valeurs pour extraire les données les plus récentes de la ligne. Pour plus d’informations sur les curseurs avec défilement et les jeux de réinitialisation, consultez [curseurs avec défilement](../../../odbc/reference/develop-app/scrollable-cursors.md).
