---
title: Types de curseurs (fr) Microsoft Docs
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4782c61c2f150e36c9632d09170468229c238cbb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305458"
---
# <a name="cursor-types"></a>Types de curseurs
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC définit quatre types de curseurs pris en charge par Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote Native Client ODBC. Ces curseurs varient dans leur capacité à détecter les changements à l’ensemble de résultats et dans les ressources qu’ils consomment, telles que la mémoire et l’espace dans **tempdb**. Un curseur peut détecter des modifications apportées à des lignes uniquement lorsqu'il tente d'extraire à nouveau ces lignes ; il n'existe aucun moyen pour la source de données d'informer le curseur des modifications apportées aux lignes en cours d'extraction. La capacité d'un curseur à détecter des modifications qui n'ont pas été apportées par le biais du curseur est également influencée par le niveau d'isolation de la transaction.  
  
 Les quatre types de curseurs ODBC pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont les suivants :  
  
-   Les curseurs avant uniquement ne prennent pas en charge le défilement, mais seulement l'extraction de lignes en séquence à partir du début jusqu'à la fin du curseur.  
  
-   Les curseurs statiques sont construits en **tempdb** lorsque le curseur est ouvert. Ils affichent toujours l'ensemble de résultats tel qu'il était au moment où le curseur a été ouvert. Ils ne reflètent jamais les modifications apportées aux données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les curseurs statiques sont toujours en lecture seule. Parce qu’un curseur serveur statique est construit comme une table de travail dans **tempdb**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]la taille de l’ensemble de résultat curseur ne peut pas dépasser la taille maximale de la rangée autorisée par .  
  
-   L'appartenance et l'ordre des lignes dans le jeu de résultats des curseurs de jeux de clés sont fixés au moment de l'ouverture du curseur. Les modifications aux colonnes non-clés sont visibles à travers le curseur.  
  
-   Les curseurs dynamiques sont le contraire des curseurs statiques. Les curseurs dynamiques reflètent toutes les modifications apportées aux lignes de leur jeu de résultats. Les valeurs des données, l'ordre et l'appartenance des lignes du jeu de résultats peuvent changer à chaque extraction.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de cursors &#40;&#41;ODBC](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
