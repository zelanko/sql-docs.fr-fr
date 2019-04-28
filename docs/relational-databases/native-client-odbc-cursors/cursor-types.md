---
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7fb5d6893921b7d8947a138c8c7a77c61fdd765e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63013731"
---
# <a name="cursor-types"></a>Types de curseurs
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC définit quatre types de curseurs pris en charge par Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client. Ces curseurs diffèrent au niveau de leur capacité à détecter les modifications apportées au jeu de résultats et dans les ressources qu’ils consomment, telles que la mémoire et de l’espace dans **tempdb**. Un curseur peut détecter des modifications apportées à des lignes uniquement lorsqu'il tente d'extraire à nouveau ces lignes ; il n'existe aucun moyen pour la source de données d'informer le curseur des modifications apportées aux lignes en cours d'extraction. La capacité d'un curseur à détecter des modifications qui n'ont pas été apportées par le biais du curseur est également influencée par le niveau d'isolation de la transaction.  
  
 Les quatre types de curseurs ODBC pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont les suivants :  
  
-   Les curseurs avant uniquement ne prennent pas en charge le défilement, mais seulement l'extraction de lignes en séquence à partir du début jusqu'à la fin du curseur.  
  
-   Curseurs statiques sont intégrés **tempdb** lorsque le curseur est ouvert. Ils affichent toujours l'ensemble de résultats tel qu'il était au moment où le curseur a été ouvert. Ils ne reflètent jamais les modifications apportées aux données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les curseurs statiques sont toujours en lecture seule. Car un curseur côté serveur statique est généré sous la forme d’une table de travail **tempdb**, la taille du jeu de résultats de curseur ne peut pas dépasser la taille de ligne maximale autorisée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   L'appartenance et l'ordre des lignes dans le jeu de résultats des curseurs de jeux de clés sont fixés au moment de l'ouverture du curseur. Les modifications aux colonnes non-clés sont visibles à travers le curseur.  
  
-   Les curseurs dynamiques sont le contraire des curseurs statiques. Les curseurs dynamiques reflètent toutes les modifications apportées aux lignes de leur jeu de résultats. Les valeurs des données, l'ordre et l'appartenance des lignes du jeu de résultats peuvent changer à chaque extraction.  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation de curseurs &#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
