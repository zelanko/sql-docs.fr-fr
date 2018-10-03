---
title: Pilotes basés sur fichier | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- file-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
- drivers [ODBC], file-based drivers
ms.assetid: d92e0c5c-d176-4282-bbe1-d449e2223d50
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 45d9203a08b9c70809e81fb3d9cf84a521017068
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47722957"
---
# <a name="file-based-drivers"></a>Pilotes basés sur des fichiers
Pilotes basés sur le fichier sont utilisés avec des sources de données comme dBASE qui ne fournissent pas d’un moteur de base de données autonome pour le pilote à utiliser. Ces pilotes accéder directement aux données physiques et doivent implémenter un moteur de base de données pour traiter les instructions SQL. Comme une pratique standard, les moteurs de base de données dans les pilotes basés sur fichier implémentent le sous-ensemble de ODBC SQL définie par le niveau de conformité minimale SQL ; Pour obtenir la liste des instructions SQL dans ce niveau de conformité, consultez [annexe c : SQL grammaire](../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Dans les pilotes basés sur SGBD et fichier de comparaisons, pilotes basés sur le fichier sont plus difficile à écrire en raison du composant du moteur de base de données, moins compliqué à configurer, car aucune autre pièce réseau et moins puissants, car peu de gens ont le temps d’écriture de base de données moteurs aussi puissantes que celles générées par des sociétés de la base de données.  
  
 L’illustration suivante montre deux configurations de pilotes basés sur le fichier, celui dans lequel les données résident localement et l’autre dans lequel il réside sur un serveur de fichiers réseau.  
  
 ![Deux configurations du fichier&#45;pilotes](../../odbc/reference/media/pr06.gif "pr06")
