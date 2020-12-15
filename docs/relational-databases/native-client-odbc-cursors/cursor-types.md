---
description: Types de curseurs
title: Types de curseurs | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- cursors [ODBC], types
- ODBC cursors, types
ms.assetid: 3a916cc7-f352-42cb-8b83-f78e06cef991
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9bffc8d5197117533913dca63c171fb4fffab588
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97438652"
---
# <a name="cursor-types"></a>Types de curseurs
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  ODBC définit quatre types de curseurs pris en charge par Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client. Ces curseurs varient en fonction de leur capacité à détecter les modifications apportées au jeu de résultats et aux ressources qu’ils consomment, telles que la mémoire et l’espace dans **tempdb**. Un curseur peut détecter des modifications apportées à des lignes uniquement lorsqu'il tente d'extraire à nouveau ces lignes ; il n'existe aucun moyen pour la source de données d'informer le curseur des modifications apportées aux lignes en cours d'extraction. La capacité d'un curseur à détecter des modifications qui n'ont pas été apportées par le biais du curseur est également influencée par le niveau d'isolation de la transaction.  
  
 Les quatre types de curseurs ODBC pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont les suivants :  
  
-   Les curseurs avant uniquement ne prennent pas en charge le défilement, mais seulement l'extraction de lignes en séquence à partir du début jusqu'à la fin du curseur.  
  
-   Les curseurs statiques sont créés dans **tempdb** lorsque le curseur est ouvert. Ils affichent toujours l'ensemble de résultats tel qu'il était au moment où le curseur a été ouvert. Ils ne reflètent jamais les modifications apportées aux données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les curseurs statiques sont toujours en lecture seule. Étant donné qu’un curseur de serveur statique est créé en tant que table de travail dans **tempdb**, la taille du jeu de résultats du curseur ne peut pas dépasser la taille de ligne maximale autorisée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   L'appartenance et l'ordre des lignes dans le jeu de résultats des curseurs de jeux de clés sont fixés au moment de l'ouverture du curseur. Les modifications aux colonnes non-clés sont visibles à travers le curseur.  
  
-   Les curseurs dynamiques sont le contraire des curseurs statiques. Les curseurs dynamiques reflètent toutes les modifications apportées aux lignes de leur jeu de résultats. Les valeurs des données, l'ordre et l'appartenance des lignes du jeu de résultats peuvent changer à chaque extraction.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de curseurs &#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
