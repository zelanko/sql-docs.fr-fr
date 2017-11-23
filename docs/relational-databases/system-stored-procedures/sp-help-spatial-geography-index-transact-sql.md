---
title: sp_help_spatial_geography_index (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_index
- sp_help_spatial_geography_index_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_spatial_geography_index procedure
ms.assetid: c9bf5675-eafc-4d71-bfdb-da963384fa0c
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 52561d1513d668aa6d2507f0c38c3206d584a4e2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpspatialgeographyindex-transact-sql"></a>sp_help_spatial_geography_index (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne les noms et valeurs pour un ensemble spécifié de propriétés sur un **geography** index spatial. Le résultat est retourné dans un format de table. Vous pouvez choisir de retourner un jeu principal de propriétés ou toutes les propriétés de l'index.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_spatial_geography_index [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ] 'verboseoutput' ]   
     [ , [ @query_sample = ] 'query_sample' ]   
```  
  
## <a name="arguments"></a>Arguments  
 Consultez [Arguments et les propriétés d’Index Spatial de procédures stockées](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="properties"></a>Propriétés  
 Consultez [Arguments et les propriétés d’Index Spatial de procédures stockées](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="permissions"></a>Permissions  
 L'utilisateur doit être assigné un rôle PUBLIC pour accéder à la procédure. Nécessite une autorisation READ ACCESS sur le serveur et l'objet.  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise `sp_help_spatial_geography_index` pour étudier la **geography** index spatial **SIndx_SpatialTable_geography_col2** définie sur la table **geography_col** de l’exemple de requête donné dans  **@qs** . Cet exemple retourne uniquement les propriétés principales de l'index spécifié.  
  
```  
declare @qs geography  
        ='POLYGON((-90.0 -180, -90 180.0, 90 180.0, 90 -180, -90 -180.0))';  
exec sp_help_spatial_geography_index 'geography_col', 'SIndx_SpatialTable_geography_col2', 0, @qs;  
```  
  
 La zone englobante d’un **geography** instance est le monde entier.  
  
## <a name="requirements"></a>Spécifications  
  
## <a name="see-also"></a>Voir aussi  
 [Les procédures stockées d’Index spatial](http://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)   
 [Vue d’ensemble des index spatiaux](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Données spatiales &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
