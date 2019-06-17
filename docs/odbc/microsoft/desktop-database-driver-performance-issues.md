---
title: Problèmes de performances de pilote de base de données de bureau | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], performance
- desktop database drivers [ODBC], performance
- Jet-based ODBC drivers [ODBC], performance
ms.assetid: 1a4c4b7e-9744-411f-9b6e-06dfdad92cf7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b4d92d2784649e4366113b3070b54598df585370
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63240303"
---
# <a name="desktop-database-driver-performance-issues"></a>Problèmes de performances des pilotes pour les bases de données de poste de travail
Pour garantir la compatibilité avec les applications existantes de ANSI, les types de données SQL_WCHAR, SQL_WVARCHAR et SQL_WLONGVARCHAR sont exposées en tant que SQL_CHAR, SQL_VARCHAR et SQL_LONGVARCHAR pour Microsoft Access 4.0 ou des sources de données plus élevées. Les sources de données ne retournent pas de types de données CHAR large, mais les données toujours doivent être envoyées à Jet sous forme de caractère large. Il est important de comprendre que conversion aura lieu si une colonne de paramètre ou résultat SQL_C_CHAR est liée à un type de données SQL_CHAR dans une application ANSI.  
  
 Cette conversion peut être particulièrement inefficace en termes de mémoire lorsqu’un type SQL_C_CHAR est lié à un paramètre de type LONGVARCHAR. Étant donné que le moteur Jet 4.0 est impossible de flux de données de paramètre LONGTEXT, une mémoire tampon de conversion UNICODE qui est deux fois la taille de la mémoire tampon SQL_C_CHAR ANSI doit allouée. Il est le mécanisme le plus efficace pour l’application effectuer la conversion d’UNICODE et de lier le paramètre en tant que type SQL_C_WCHAR. Lorsqu’un paramètre est marqué en tant que data-at-execution et les données sont fournies dans plusieurs appels à SQLPutData, un tampon de données longtext s’accroît. Pour éviter les dépenses liées à l’augmentation de cette mémoire tampon « Placer les données » consiste à fournir une longueur facultative via SQL_DATA_AT_EXEC_LEN(x), où *x* est la longueur attendue d’octets. Cela initialisera la taille d’un tampon interne de PlacerDonnées *x* octets.  
  
> [!NOTE]  
>  Un moyen efficace pour insérer ou mettre à jour des données de type long peut être accompli en utilisant **SQLBulkOperations()** ou **SQLSetPos()** et en définissant les données longues sur SQL_DATA_AT_EXEC. (EXEC_LEN est ignoré dans ce cas). Données peuvent être diffusé en continu dans des blocs en appelant **SQLPutData** plusieurs fois, ce qui en fait ajoute les données à la table.  
  
 Lorsqu’une application à l’aide d’une base de données Jet 3.5 via les pilotes de base de données Microsoft ODBC Desktop est mis à niveau vers la version 4.0, une dégradation des performances et une taille de jeu de travail accrue peuvent se produire. Il s’agit, car lorsqu’une version 3. *x* base de données est ouverte à l’aide de la version 4.0 du pilote nouveau, il charge Jet 4.0. Lorsque Jet 4.0 s’ouvre à la base de données et voit que la base de données est un 3. *x* version, il charge un pilote ISAM Installable qui équivaut au chargement du moteur Jet 3.5 également. Pour supprimer la pénalité de performances et la taille, les 3 Jet. *x* base de données doit-elle être compressée dans une base de données de format de Jet 4.0. Cela éliminer le chargement de deux moteurs Jet et réduire le chemin d’accès du code pour les données.  
  
 En outre, le moteur Jet 4.0 est un moteur de Unicode. Toutes les chaînes sont stockées et manipulées au format Unicode. Lorsqu’une application ANSI accède à un 3 de Jet. *x* base de données via le moteur Jet 4.0, les données est converti d’ANSI en Unicode, puis vers ANSI. Si la base de données est mis à jour vers le format de la version 4.0, les chaînes sont converties en Unicode, suppression d’un niveau de conversion de chaîne comme tout en minimisant le chemin d’accès du code pour les données en passant par un seul moteur Jet.
