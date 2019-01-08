---
title: Afficher une collection de schémas XML stockée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- schema collections [SQL Server], viewing
- XML schemas [SQL Server], viewing
- CREATE XML SCHEMA COLLECTION statement
- xml_schema_namespace function
- XML schema collections [SQL Server], viewing
- displaying XML schema collections
- viewing XML schema collections
ms.assetid: e38031af-22df-4cd9-a14e-e316b822f91b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9e43af2841de0f2e5a00bf4e7871f71092e6bc87
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53373781"
---
# <a name="view-a-stored-xml-schema-collection"></a>Afficher une collection de schémas XML stockée
  Après l’importation d’une collection de schémas XML à l’aide de l’instruction [CREATE XML SCHEMA COLLECTION](/sql/t-sql/statements/create-xml-schema-collection-transact-sql), les composants du schéma sont stockés dans les métadonnées. Vous pouvez utiliser la fonction intrinsèque [xml_schema_namespace](/sql/t-sql/xml/xml-schema-namespace)pour reconstruire la collection de schémas XML. Cette fonction renvoie une instance de type de données `xml`.  
  
 Par exemple, la requête suivante reprend une collection de schémas XML (à savoir`ProductDescriptionSchemaCollection`) à partir du schéma relationnel de production se trouvant dans la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection')  
GO  
```  
  
 Si vous ne voulez consulter qu'un seul schéma de la collection de schémas XML, vous pouvez spécifier une requête XQuery portant sur le résultat de type `xml` renvoyé par la fonction `xml_schema_namespace`.  
  
```  
SELECT xml_schema_namespace(N'RelationalSchemaName',N'XmlSchemaCollectionName').query('  
/xs:schema[@targetNamespace="TargetNameSpace"]  
')  
GO  
```  
  
 Par exemple, la requête suivante extrait les informations du schéma XML traitant des garanties et de l'entretien des produits à partir de la collection de schémas XML nommée `ProductDescriptionSchemaCollection` .  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection').query('  
/xs:schema[@targetNamespace="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"]  
')  
GO  
```  
  
 Vous pouvez également transmettre l'espace de noms cible facultatif en tant que troisième paramètre à la fonction `xml_schema_namespace` pour extraire un schéma spécifique de la collection, comme illustré dans la requête suivante :  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection', N'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain')  
GO  
```  
  
 Lors de la création d'une collection de schémas XML par le biais de l'instruction CREATE XML SCHEMA COLLECTION dans la base de données, l'instruction stocke les composants du schéma dans les métadonnées. Notez que seuls les composants de schéma que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comprend sont stockés. Les commentaires, les annotations et les attributs non XSD ne sont pas stockés. Le schéma ainsi reconstruit par **xml_schema_namespace** est donc équivalent au schéma d’origine d’un point de vue fonctionnel, mais ne lui ressemble pas nécessairement. Par exemple, vous n'y verrez pas les mêmes préfixes que dans le schéma d'origine. Le schéma renvoyé par la fonction **xml_schema_namespace** utilise **t** comme préfixe pour l’espace de noms cible et **ns1**, **ns2**, etc., pour les autres espaces de noms.  
  
 Pour conserver une copie identique des schémas XML, vous devez sauvegarder ces derniers dans des fichiers ou dans des colonnes de type `xml` d'une table tirée d'une base de données.  
  
 La vue de catalogue [sys.xml_schema_collections](/sql/relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql) retourne également des informations concernant les collections de schémas XML. Ces informations comprennent le nom de la collection, la date de création et le propriétaire de la	collection.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections de schémas XML &#40;SQL Server&#41;](xml-schema-collections-sql-server.md)  
  
  
