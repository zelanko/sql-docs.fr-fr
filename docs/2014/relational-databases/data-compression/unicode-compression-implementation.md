---
title: Implémentation de la compression Unicode | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Unicode data compression
- compression [SQL Server], Unicode data
ms.assetid: 44e69e60-9b35-43fe-b9c7-8cf34eaea62a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a43a437b277c0fcc090a4ebd52d9deb14bec9fd0
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52756021"
---
# <a name="unicode-compression-implementation"></a>Implémentation de la compression Unicode
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise une implémentation de l’algorithme SCSU (Standard Compression Scheme for Unicode) pour compresser les valeurs Unicode stockées dans des objets à compression de ligne ou de page. Pour ces objets compressés, la compression Unicode est automatique pour les colonnes `nchar(n)` et `nvarchar(n)`. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] stocke les données Unicode comme 2 octets, indépendamment des paramètres régionaux. Ceci porte le nom d'encodage UCS-2. Pour certains paramètres régionaux, l'implémentation de la compression SCSU dans SQL Server peut économiser jusqu'à 50 pour cent d'espace de stockage.  
  
## <a name="supported-data-types"></a>Types de données pris en charge  
 La compression Unicode prend en charge les types de données de longueur fixe `nchar(n)` et `nvarchar(n)`. Les valeurs de données stockées hors ligne ou dans des colonnes `nvarchar(max)` ne sont pas compressées.  
  
> [!NOTE]  
>  La compression Unicode n'est pas prise en charge pour les données d'`nvarchar(max)`, même si celles-ci sont stockées dans des lignes. Toutefois, ce type de données peut tirer parti de la compression de page.  
  
## <a name="upgrading-from-earlier-versions-of-sql-server"></a>Mise à niveau à partir de versions antérieures de SQL Server  
 Quand une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], les modifications liées à la compression Unicode ne sont apportées à aucun objet de base de données, compressé ou non compressé. Une fois la base de données mise à niveau, les objets sont affectés comme suit :  
  
-   Si l'objet n'est pas compressé, aucune modification n'est apportée et l'objet continue de fonctionner comme précédemment.  
  
-   Les objets à compression de page ou de ligne continuent de fonctionner comme précédemment. Les données non compressés restent sous forme non compressée jusqu'à ce que leur valeur soit mise à jour.  
  
-   Les nouvelles lignes insérées dans une table à compression de page ou de ligne sont compressées à l'aide de la compression Unicode.  
  
    > [!NOTE]  
    >  Pour tirer pleinement parti des avantages de la compression Unicode, l'objet doit être reconstruit avec compression de ligne ou de page.  
  
## <a name="how-unicode-compression-affects-data-storage"></a>Impact de la compression Unicode sur le stockage des données  
 Lorsqu'un index est créé ou reconstruit ou lorsqu'une valeur est modifiée dans une table compressée avec la compression de page ou de ligne, l'index ou la valeur affecté est stockée sous forme compressée uniquement si sa taille compressée est inférieure à sa taille actuelle. Cela empêche que la taille des lignes dans une table ou un index n'augmente à cause de la compression Unicode.  
  
 L'espace de stockage économisé par la compression dépend des caractéristiques des données compressées et des paramètres régionaux des données. Le tableau suivant répertorie les économies d'espace qui peuvent être accomplies pour plusieurs paramètres régionaux.  
  
|Paramètres régionaux|Pourcentage de compression|  
|------------|-------------------------|  
|Anglais|50|  
|German|50|  
|Hindi|50|  
|Turc|48|  
|Vietnamien|39|  
|Japonais|15|  
  
## <a name="see-also"></a>Voir aussi  
 [Compression de données](data-compression.md)   
 [sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql)   
 [Implémentation de la compression de page](page-compression-implementation.md)   
 [sys.dm_db_persisted_sku_features &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-persisted-sku-features-transact-sql)  
  
  
