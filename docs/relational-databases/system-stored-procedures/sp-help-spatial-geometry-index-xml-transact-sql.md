---
title: sp_help_spatial_geometry_index_xml (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geometry_index_xml_TSQL
- sp_help_spatial_geometry_index_xml
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geometry_index_xml procedure
ms.assetid: 9668ae6d-9ed5-418e-bb9a-9e7b66f7dd16
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 1a166589b4544cf38709736ef45d30e383531d8e
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43036100"
---
# <a name="sphelpspatialgeometryindexxml-transact-sql"></a>sp_help_spatial_geometry_index_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne les noms et valeurs pour un ensemble spécifié de propriétés sur un **geometry** index spatial. Vous pouvez choisir de retourner un jeu principal de propriétés ou toutes les propriétés de l'index.  
  
 Les résultats sont retournés dans un fragment XML qui affiche le nom et la valeur des propriétés sélectionnées.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_spatial_geometry_index [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ]'{ 0 | 1 }]   
     [ , [ @query_sample = ] 'query_sample' ]   
     [ ,.[ @xml_output = ] 'xml_output' ]   
```  
  
## <a name="arguments"></a>Arguments  
 Consultez [Arguments et les propriétés d’Index Spatial de procédures stockées](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="properties"></a>Properties  
 Consultez [Arguments et les propriétés d’Index Spatial de procédures stockées](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="permissions"></a>Permissions  
 Utilisateur doit être un membre de la **public** rôle. Nécessite une autorisation READ ACCESS sur le serveur et l'objet.  
  
## <a name="remarks"></a>Notes  
 Les propriétés qui contiennent des valeurs NULL ne sont pas incluses dans le jeu de retour XML.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise `sp_help_spatial_geometry_index_xml` pour étudier l’index spatial **SIndx_SpatialTable_geometry_col2** définie sur la table **geometry_col** pour l’exemple de requête donnée dans **@qs**. Cet exemple retourne les propriétés principales de l'index spécifié dans un fragment XML qui affiche le nom et la valeur des propriétés sélectionnées.  
  
 Un [XQuery](../../xquery/xquery-basics.md) est alors exécutée sur le jeu de résultats, en retournant une propriété spécifique.  
  
```  
DECLARE @qs geometry  
        ='POLYGON((-90.0 -180.0, -90.0 180.0, 90.0 180.0, 90.0 -180.0, -90.0 -180.0))';  
DECLARE @x xml;  
EXEC sp_help_spatial_geometry_index_xml 'geometry_col', 'SIndx_SpatialTable_geometry_col2', 0, @qs, @x output;  
SELECT @x.value('(/Primary_Filter_Efficiency/text())[1]', 'float');  
```  
  
 Semblable à [sp_help_spatial_geometry_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md), cette procédure stockée fournit un accès par programme plus simple aux propriétés d’un index spatial et signale le jeu de résultats en XML.  
  
## <a name="requirements"></a>Spécifications  
  
## <a name="see-also"></a>Voir aussi  
 [Arguments et les propriétés de spatiale d’Index des procédures stockées](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md)   
 [Procédures stockées d’Index spatial](http://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geometry_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)   
 [Vue d’ensemble des index spatiaux](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Données spatiales &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [Principes fondamentaux de XQuery](../../xquery/xquery-basics.md)   
 [Informations de référence sur le langage XQuery](../../xquery/xquery-language-reference-sql-server.md)  
  
  
