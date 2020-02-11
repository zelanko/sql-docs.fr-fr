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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3e4b097a0ae2a591b5a719ee3a9622ee292e5b52
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73784690"
---
# <a name="cursor-types"></a>Types de curseurs
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC définit quatre types de curseurs pris [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en charge [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par Microsoft et le pilote ODBC Native Client. Ces curseurs varient en fonction de leur capacité à détecter les modifications apportées au jeu de résultats et aux ressources qu’ils consomment, telles que la mémoire et l’espace dans **tempdb**. Un curseur peut détecter des modifications apportées à des lignes uniquement lorsqu'il tente d'extraire à nouveau ces lignes ; il n'existe aucun moyen pour la source de données d'informer le curseur des modifications apportées aux lignes en cours d'extraction. La capacité d'un curseur à détecter des modifications qui n'ont pas été apportées par le biais du curseur est également influencée par le niveau d'isolation de la transaction.  
  
 Les quatre types de curseurs ODBC pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont les suivants :  
  
-   Les curseurs avant uniquement ne prennent pas en charge le défilement, mais seulement l'extraction de lignes en séquence à partir du début jusqu'à la fin du curseur.  
  
-   Les curseurs statiques sont créés dans **tempdb** lorsque le curseur est ouvert. Ils affichent toujours l'ensemble de résultats tel qu'il était au moment où le curseur a été ouvert. Ils ne reflètent jamais les modifications apportées aux données. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les curseurs statiques sont toujours en lecture seule. Étant donné qu’un curseur de serveur statique est créé en tant que table de travail dans **tempdb**, la taille du jeu de résultats du curseur ne peut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]pas dépasser la taille de ligne maximale autorisée par.  
  
-   L'appartenance et l'ordre des lignes dans le jeu de résultats des curseurs de jeux de clés sont fixés au moment de l'ouverture du curseur. Les modifications aux colonnes non-clés sont visibles à travers le curseur.  
  
-   Les curseurs dynamiques sont le contraire des curseurs statiques. Les curseurs dynamiques reflètent toutes les modifications apportées aux lignes de leur jeu de résultats. Les valeurs des données, l'ordre et l'appartenance des lignes du jeu de résultats peuvent changer à chaque extraction.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de curseurs &#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
