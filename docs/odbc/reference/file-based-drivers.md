---
title: "Pilotes basés sur le fichier | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
- drivers [ODBC], file-based drivers
ms.assetid: d92e0c5c-d176-4282-bbe1-d449e2223d50
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2ab8cb4066a8c5c7ab2e31401dd1e80d003d5b38
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="file-based-drivers"></a>Pilotes basés sur des fichiers
Pilotes basés sur des fichiers sont utilisés avec des sources de données telles que dBASE qui ne fournissent pas d’un moteur de base de données autonome pour le pilote à utiliser. Ces pilotes accéder directement aux données physiques et vous doivent implémenter un moteur de base de données pour traiter les instructions SQL. En tant qu’une pratique standard, les moteurs de base de données dans les pilotes basés sur le fichier implémentent le sous-ensemble de ODBC SQL définie par le niveau de conformité minimal SQL ; Pour obtenir la liste des instructions SQL dans ce niveau de conformité, consultez [annexe c : SQL grammaire](../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Dans les pilotes basés sur SGBD et fichier de comparaisons, pilotes basés sur le fichier sont plus difficiles à écrire en raison du composant du moteur de base de données, moins compliqué à configurer, car aucune autre pièce réseau et moins puissants, car peu de gens ont le temps de rédiger des moteurs de base de données aussi puissantes que celles produites par des sociétés de la base de données.  
  
 L’illustration suivante montre les deux configurations de pilotes basés sur des fichiers, dans lequel les données résident localement et l’autre dans lequel il réside sur un serveur de fichiers réseau.  
  
 ![Deux configurations du fichier &#45; pilotes en fonction](../../odbc/reference/media/pr06.gif "pr06")

