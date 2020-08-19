---
description: Problèmes de performances des pilotes pour les bases de données de poste de travail
title: Problèmes de performances des pilotes de base de données du Bureau | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 20c21c493d81df6afb4a338675f86ad96ccfab68
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449551"
---
# <a name="desktop-database-driver-performance-issues"></a>Problèmes de performances des pilotes pour les bases de données de poste de travail
Pour garantir la compatibilité avec les applications ANSI existantes, les types de données SQL_WCHAR, SQL_WVARCHAR et SQL_WLONGVARCHAR sont exposés en tant que SQL_CHAR, SQL_VARCHAR et SQL_LONGVARCHAR pour les sources de données Microsoft Access 4,0 ou version ultérieure. Les sources de données ne retournent pas de types de données CHAR ÉTENDUs, mais les données doivent toujours être envoyées à jet sous forme de caractères larges. Il est important de comprendre que la conversion est effectuée si un paramètre SQL_C_CHAR ou une colonne de résultats est lié à un type de données SQL_CHAR dans une application ANSI.  
  
 Cette conversion peut être particulièrement inefficace en termes de mémoire lorsqu’un type de SQL_C_CHAR est lié à un paramètre de type LONGVARCHAR. Étant donné que le moteur Jet 4,0 ne peut pas diffuser en continu les données de paramètre LONGTEXT, une mémoire tampon de conversion UNICODE doit être allouée à deux fois la taille de la mémoire tampon ANSI SQL_C_CHAR. Le mécanisme le plus efficace est que l’application effectue la conversion UNICODE et lie le paramètre en tant que type SQL_C_WCHAR. Lorsqu’un paramètre est marqué en tant que données en cours d’exécution et que les données sont fournies dans plusieurs appels à SQLPutData, une mémoire tampon de données LONGTEXT est augmentée. Une façon d’éviter les dépenses liées à la croissance de cette mémoire tampon « put Data » consiste à fournir une longueur facultative via SQL_DATA_AT_EXEC_LEN (x), où *x* est la longueur attendue de octets. La taille d’une mémoire tampon PutData interne est alors initialisée sur *x* octets.  
  
> [!NOTE]  
>  Un moyen efficace d’insérer ou de mettre à jour des données de type long peut être effectué à l’aide de **SQLBulkOperations ()** ou de **SQLSetPos ()** et en définissant les données de type long sur SQL_DATA_AT_EXEC. (EXEC_LEN est ignoré dans ce cas.) Les données peuvent être diffusées en bloc en appelant **SQLPutData** plusieurs fois, ce qui a pour effet d’ajouter les données à la table.  
  
 Lorsqu’une application utilisant une base de données Jet 3,5 via les pilotes de base de données Microsoft ODBC Desktop est mise à niveau vers la version 4,0, une dégradation des performances et une taille de jeu de travail accrue peuvent se produire. Cela est dû au fait qu’une version 3. *x* est ouverte à l’aide de la nouvelle version 4,0 du pilote, elle charge Jet 4,0. Lorsque Jet 4,0 ouvre la base de données et constate que la base de données est 3. *x* , il charge un pilote ISAM installable équivalent au chargement du moteur Jet 3,5. Pour supprimer les performances et la pénalité de taille, Jet 3. *x* la base de données doit être compactée dans une base de données au format Jet 4,0. Cela permet d’éliminer le chargement de deux moteurs jet et de réduire le chemin de code des données.  
  
 En outre, le moteur Jet 4,0 est un moteur Unicode. Toutes les chaînes sont stockées et manipulées en Unicode. Quand une application ANSI accède à un jet 3. *x* Database via le moteur Jet 4,0, les données sont converties d’ANSI en Unicode, puis de nouveau en ANSI. Si la base de données est mise à jour au format 4,0, les chaînes sont converties en Unicode, en supprimant un niveau de conversion de chaîne et en minimisant le chemin d’accès du code aux données en passant par un seul moteur Jet.
