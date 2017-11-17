---
title: xml_schema_namespace (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xml_schema_namespace_TSQL
- xml_schema_namespace
dev_langs:
- TSQL
helpviewer_keywords:
- XML schema collections [SQL Server], reconstructing schemas
- xml_schema_namespace function
- reconstructing schemas
- schemas [SQL Server], XML
- schema collections [SQL Server], reconstructing schemas
ms.assetid: ee9873d8-dd3a-4bff-a10c-68bbadbdf1a6
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 449e545672192baa9d16204afe1fb23497959094
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="xmlschemanamespace"></a>xml_schema_namespace
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Reconstruit tous les schémas ou un schéma particulier dans la collection de schémas XML. Cette fonction renvoie une instance de type de données **xml** .  
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
xml_schema_namespace( Relational_schema , XML_schema_collection_name , [ Namespace ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Relational_schema*  
 Nom du schéma relationnel. *Relational_schema* est **sysname**.  
  
 *XML_schema_collection_name*  
 Nom de la collection de schémas XML à reconstruire. *XML_schema_collection_name* est **sysname**.  
  
 *Espace de noms*  
 Espace de noms URI du schéma XML que vous voulez reconstruire. Il est limité à 1 000 caractères. Si cet argument n'est pas fourni, l'ensemble de la collection de schémas XML est reconstruit. *Namespace* est **nvarchar (4000)**.  
  
## <a name="return-types"></a>Types de retour  
 **xml**  
  
## <a name="remarks"></a>Notes  
 Lorsque vous importez des composants de schéma XML dans la base de données à l’aide de [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md) ou [ALTER XML SCHEMA COLLECTION](../../t-sql/statements/alter-xml-schema-collection-transact-sql.md), les aspects du schéma utilisé pour la validation sont conservés. Par conséquent, le schéma reconstruit peut être lexicalement différent du document du schéma d'origine. En particulier, les commentaires, les espaces et les annotations sont perdus ; les informations de type implicite deviennent explicites. Par exemple, \<xs : element name = « e1 » / > devient \<xs : element name = « e1 » type = « xs : anyType » / >. Également, les préfixes des espaces de noms ne sont pas conservés.  
  
 Si vous spécifiez un paramètre d'espace de noms, le document du schéma résultant contient les définitions de tous les composants de schéma dans cet espace de noms, même s'ils ont été ajoutés dans des documents de schémas différents ou dans des étapes DDL, ou dans les deux.  
  
 Vous ne pouvez pas utiliser cette fonction pour construire des documents de schéma XML à partir de la **sys.sys** collection de schémas XML.  
  
## <a name="examples"></a>Exemples  
 Le code exemple suivant extrait la collection de schémas XML `ProductDescriptionSchemaCollection` du schéma relationnel de production dans la base de données `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT xml_schema_namespace(N'production',N'ProductDescriptionSchemaCollection');  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher une collection de schémas XML stockée](../../relational-databases/xml/view-a-stored-xml-schema-collection.md)   
 [Collections de schémas XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-schema-collections-sql-server.md)  
  
  

