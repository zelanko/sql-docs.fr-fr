---
title: sp_help_spatial_geography_index (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_index
- sp_help_spatial_geography_index_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geography_index procedure
ms.assetid: c9bf5675-eafc-4d71-bfdb-da963384fa0c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 73bb564880cae238cdbaa7e3c13a1f18ab95dc99
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72304875"
---
# <a name="sp_help_spatial_geography_index-transact-sql"></a>sp_help_spatial_geography_index (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne les noms et les valeurs d’un jeu spécifié de propriétés à propos d’un index spatial **Geography** . Le résultat est retourné dans un format de table. Vous pouvez choisir de retourner un jeu principal de propriétés ou toutes les propriétés de l'index.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_spatial_geography_index [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ] 'verboseoutput' ]   
     [ , [ @query_sample = ] 'query_sample' ]   
```  
  
## <a name="arguments"></a>Arguments  
 Consultez [les arguments et les propriétés des procédures stockées d’index spatial](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="properties"></a>Properties  
 Consultez [les arguments et les propriétés des procédures stockées d’index spatial](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="permissions"></a>Autorisations  
 L'utilisateur doit être assigné un rôle PUBLIC pour accéder à la procédure. Nécessite une autorisation READ ACCESS sur le serveur et l'objet.  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise `sp_help_spatial_geography_index` pour étudier l' index spatial Geography **SIndx_SpatialTable_geography_col2** défini sur la table **geography_col** pour l’exemple de requête donné dans **\@QS**. Cet exemple retourne uniquement les propriétés principales de l'index spécifié.  
  
```  
declare @qs geography  
        ='POLYGON((-90.0 -180, -90 180.0, 90 180.0, 90 -180, -90 -180.0))';  
exec sp_help_spatial_geography_index 'geography_col', 'SIndx_SpatialTable_geography_col2', 0, @qs;  
```  
  
 Le cadre englobant d’une instance **Geography** est l’ensemble de la terre.  
  
## <a name="requirements"></a>Configuration requise  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées d’index Spatial](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)   
 [Vue d’ensemble des index spatiaux](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Données spatiales &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
