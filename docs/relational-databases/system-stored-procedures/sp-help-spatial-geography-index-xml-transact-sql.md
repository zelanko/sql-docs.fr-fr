---
title: sp_help_spatial_geography_index_xml (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_index_xml_TSQL
- sp_help_spatial_geography_index_xml
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geography_index_xml procedure
ms.assetid: 821d4127-3ce5-4474-8561-043404a20d81
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c2503e5d3b94b5bc73d9bf2427e0162ba2eda2fe
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "72304901"
---
# <a name="sp_help_spatial_geography_index_xml-transact-sql"></a>sp_help_spatial_geography_index_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne le nom et la valeur d’un jeu de propriétés spécifié à propos d’un index spatial **Geography** . Vous pouvez choisir de retourner un jeu principal de propriétés ou toutes les propriétés de l'index.  
  
 Les résultats sont retournés dans un fragment XML qui affiche le nom et la valeur des propriétés sélectionnées.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_spatial_geography_index_xml [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ] 'verboseoutput' ]   
     [ , [ @query_sample = ] 'query_sample' ]   
     [ ,.[ @xml_output = ] 'xml_output' ]   
```  
  
## <a name="arguments"></a>Arguments  
 Consultez [les arguments et les propriétés des procédures stockées d’index spatial](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="properties"></a>Propriétés  
 Consultez [les arguments et les propriétés des procédures stockées d’index spatial](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="permissions"></a>Autorisations  
 L'utilisateur doit être assigné un rôle PUBLIC pour accéder à la procédure. Nécessite une autorisation READ ACCESS sur le serveur et l'objet.  
  
## <a name="remarks"></a>Notes  
 Les propriétés qui contiennent des valeurs NULL ne sont pas incluses dans le jeu de retour.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise `sp_help_spatial_geography_index_xml` pour étudier l’index spatial **SIndx_SpatialTable_geography_col2** défini sur la table **geography_col** pour l’exemple de requête donné dans ** \@QS**. Cet exemple retourne les propriétés principales de l'index spécifié dans un fragment XML qui affiche le nom et la valeur des propriétés sélectionnées.  
  
 Un [XQuery](../../xquery/xquery-basics.md) est ensuite exécuté sur le jeu de résultats, retournant une propriété spécifique.  
  
```  
declare @qs geography  
        ='POLYGON((-90.0 -180, -90 180.0, 90 180.0, 90 -180, -90 -180.0))';  
declare @x xml;  
exec sp_help_spatial_geography_index_xml 'geography_col', 'SIndx_SpatialTable_geography_col2', 0, @qs, @x output;  
select @x.value('(/Primary_Filter_Efficiency/text())[1]', 'float');  
```  
  
 Comme pour [sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md), cette procédure stockée fournit un accès par programme plus simple aux propriétés d’un index spatial **Geography** et signale le jeu de résultats en XML.  
  
 Le cadre englobant d’une **géographie** est l’ensemble de la terre.  
  
## <a name="requirements"></a>Spécifications  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées d’index spatial](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)   
 [Vue d’ensemble des index spatiaux](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [SQL Server de &#40;de données spatiales&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [Notions de base de XQuery](../../xquery/xquery-basics.md)   
 [Informations de référence sur le langage XQuery](../../xquery/xquery-language-reference-sql-server.md)  
  
  
