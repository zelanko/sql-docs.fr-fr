---
title: Utilise des données de catalogue | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d9b75d59d8fc28e364f5826d95e7fc50cb6afda7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63312531"
---
# <a name="uses-of-catalog-data"></a>Utilisations des données du catalogue
Applications utilisent des données de catalogue dans plusieurs façons. Voici quelques utilisations courantes :  
  
-   **Construction d’instructions SQL en cours d’exécution.** Applications verticales, par exemple une application de saisie de commandes, contiennent des instructions SQL codées en dur. Les tables et colonnes qui sont utilisées par l’application sont fixes avance, sont les instructions qui accèdent à ces tables. Par exemple, une application de saisie de commandes contient généralement un seul, paramétrable **insérer** instruction pour l’ajout de nouvelles commandes au système.  
  
     Souvent, les applications génériques, tel qu’un programme de feuille de calcul qui utilise ODBC pour récupérer des données, créer des instructions SQL en cours d’exécution basée sur l’entrée de l’utilisateur. Ce type d’application peut nécessiter l’utilisateur à taper les noms des tables et des colonnes à utiliser. Toutefois, il serait plus simple pour l’utilisateur si l’application affiche des listes de tables et colonnes à partir de laquelle l’utilisateur peut effectuer des sélections. Pour générer ces listes, l’application appelle le **SQLTables** et **SQLColumns** fonctions de catalogue.  
  
-   **Construction d’instructions SQL au cours du développement.** En règle générale, les environnements de développement d’application permettant au programmeur de créer des requêtes de base de données lors du développement d’un programme. Les requêtes sont ensuite codé en dur dans l’application en cours de génération.  
  
     Ces environnements peuvent également utiliser des **SQLTables** et **SQLColumns** pour créer des listes à partir de laquelle le programmeur peut effectuer des sélections. Ces environnements peuvent également utiliser **SQLPrimaryKeys** et **SQLForeignKeys** pour déterminer automatiquement et afficher les relations entre les tables sélectionnées et utiliser **SQLStatistics** pour déterminer et mettre en surbrillance les champs indexés afin que le programmeur peut créer des requêtes efficaces.  
  
-   **Construction des curseurs.** Une application, un pilote ou un intergiciel (middleware) qui fournit un moteur de curseur de défilement utilise **SQLSpecialColumns** pour déterminer l’ou les colonnes qui identifient une ligne. Le programme peut générer un *keyset* contenant les valeurs de ces colonnes pour chaque ligne qui a été extrait. Lorsque l’application fait défiler vers la ligne, il utilise ensuite ces valeurs pour extraire les données les plus récentes pour la ligne. Pour plus d’informations sur les curseurs avec défilement et les jeux de clés, consultez [curseurs avec défilement](../../../odbc/reference/develop-app/scrollable-cursors.md).
