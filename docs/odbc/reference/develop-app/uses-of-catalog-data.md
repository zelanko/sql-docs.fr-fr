---
title: Utilisations des données de catalogue (en anglais) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306810"
---
# <a name="uses-of-catalog-data"></a>Utilisations des données du catalogue
Les applications utilisent les données du catalogue de diverses façons. Voici quelques utilisations courantes :  
  
-   **Construire des relevés SQL à l’heure de l’exécution.** Les applications verticales, telles qu’une application d’entrée de commande, contiennent des relevés SQL codés en dur. Les tableaux et les colonnes qui sont utilisés par l’application sont fixés à l’avance, tout comme les instructions qui accèdent à ces tables. Par exemple, une application d’entrée de commande contient habituellement une seule déclaration **INSERT** paramétrée pour l’ajout de nouvelles commandes au système.  
  
     Les applications génériques, comme un programme de feuilles de calcul qui utilise ODBC pour récupérer des données, construisent souvent des relevés SQL à l’heure d’exécution en fonction des entrées de l’utilisateur. Une telle application pourrait obliger l’utilisateur à taper les noms des tables et des colonnes à utiliser. Cependant, il serait plus facile pour l’utilisateur si l’application affiche des listes de tableaux et de colonnes à partir desquelles l’utilisateur pourrait faire des sélections. Pour établir ces listes, l’application appellerait les fonctions de catalogue **SQLTables** et **SQLColumns.**  
  
-   **Construction des déclarations SQL pendant le développement.** Les environnements de développement d’applications permettent généralement au programmeur de créer des requêtes de base de données tout en élaborant un programme. Les requêtes sont ensuite codées en dur dans l’application en cours de construction.  
  
     De tels environnements pourraient également utiliser **SQLTables** et **SQLColumns** pour créer des listes à partir desquelles le programmeur pourrait faire des sélections. Ces environnements peuvent également utiliser **SQLPrimaryKeys** et **SQLForeignKeys** pour déterminer et afficher automatiquement les relations entre certaines tables, et utiliser **SQLStatistics** pour déterminer et mettre en évidence les champs indexés afin que le programmeur puisse créer des requêtes efficaces.  
  
-   **Construire des curseurs.** Une application, un conducteur ou un middleware qui fournit un moteur curseur défilant pourrait utiliser **SQLSpecialColumns** pour déterminer quelle colonne ou colonne identifient uniquement une ligne. Le programme pourrait construire un *jeu de clés* contenant les valeurs de ces colonnes pour chaque rangée qui a été récupérée. Lorsque l’application fait défiler vers la ligne, elle utiliserait alors ces valeurs pour récupérer les données les plus récentes pour la ligne. Pour plus d’informations sur les curseurs et les clés défilementables, voir [Cursesors défilants](../../../odbc/reference/develop-app/scrollable-cursors.md).
