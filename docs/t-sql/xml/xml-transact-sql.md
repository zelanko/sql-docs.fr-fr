---
description: xml (Transact-SQL)
title: xml (Transact-SQL)
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- xml_TSQL
- xml
dev_langs:
- TSQL
helpviewer_keywords:
- xml data type [SQL Server], about xml data type
ms.assetid: 9198f671-8e61-4ca4-9c3a-859f84020e62
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 15543b21a462d8ad01ddc3a1cc5ba82847ee3016
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88478700"
---
# <a name="xml-transact-sql"></a>xml (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Type de données qui stocke les données XML. Vous pouvez stocker des instances **xml** dans une colonne ou une variable de type **xml**.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
xml ( [ CONTENT | DOCUMENT ] xml_schema_collection )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
 CONTENT  
 Limite l’instance **xml** pour qu’elle corresponde à un fragment XML correctement formé. Les données XML peuvent contenir zéro ou plusieurs éléments au niveau supérieur. Les nœuds de texte sont également autorisés au niveau supérieur.  
  
 Il s'agit du comportement par défaut.  
  
 DOCUMENT  
 Limite l’instance **xml** pour qu’elle corresponde à un document XML correctement formé. Les données XML doivent posséder un et un seul élément racine. Les nœuds de texte ne sont pas autorisés au niveau supérieur.  
  
 *xml_schema_collection*  
 Nom d'une collection de schémas XML. Pour créer une colonne ou variable **xml** typée, vous pouvez éventuellement spécifier le nom de la collection de schémas XML. Pour plus d’informations sur le XML typé et non typé, consultez [Comparer du XML typé et du XML non typé](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
## <a name="remarks"></a>Notes  
 La représentation stockée des instances de types de données **xml** ne peut pas excéder une taille de 2 gigaoctets (Go).  
  
 Les facettes CONTENT et DOCUMENT s'appliquent uniquement aux variables typées XML. Pour plus d’informations, consultez [Comparer du XML typé et du XML non typé](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
## <a name="examples"></a>Exemples  
  
```  
USE AdventureWorks;  
GO  
DECLARE @DemographicData xml (Person.IndividualSurveySchemaCollection);  
SET @DemographicData =  (SELECT TOP 1 Demographics FROM Person.Person);  
SELECT @DemographicData;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Conversion de type de données &#40;moteur de base de données&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)   
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [méthodes de type de données xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Références relatives au langage Xquery &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md)  
  
  
