---
title: Utiliser le mode PATH avec FOR XML | Microsoft Docs
description: Découvrez comment utiliser le mode PATH avec des requêtes FOR XML imbriquées et la directive TYPE pour écrire des requêtes moins complexes qui retournent des instances de type XML.
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode
- characters [SQL Server], XML
- aliases [SQL Server], XML
- FOR XML clause, PATH mode
- FOR XML PATH mode
- column names [SQL Server]
- XPath queries [SQL Server]
ms.assetid: a685a9ad-3d28-4596-aa72-119202df3976
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ff6beee153a5f923178436710d1b38b1151d6c7d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85724544"
---
# <a name="use-path-mode-with-for-xml"></a>Utiliser le mode PATH avec FOR XML
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Comme décrit dans la rubrique [Construction de code XML à l’aide de FOR XML](../../relational-databases/xml/for-xml-sql-server.md), le mode PATH permet de combiner des éléments et des attributs de façon simplifiée. En outre, il facilite l'extension de l'imbrication pour la représentation des propriétés complexes. Vous pouvez utiliser des requêtes en mode FOR XML EXPLICIT pour construire un document XML de ce type à partir d'un ensemble de lignes, mais le mode PATH offre une solution plus simple que les requêtes en mode EXPLICIT potentiellement lourdes. Le mode PATH, allié à la possibilité d’écrire des requêtes FOR XML imbriquées et de faire appel à la directive TYPE pour renvoyer les instances de type **xml** , vous permet d’écrire des requêtes de moindre complexité.  
  
 En mode PATH, les noms ou alias de colonnes sont traités en tant qu'expressions XPath. Ces expressions indiquent comment les valeurs sont mappées au document XML. Chaque expression XPath est un chemin d'accès XPath relatif qui fournit le type d'élément, tel que les valeurs d'attribut, d'élément et scalaire, ainsi que le nom et la hiérarchie du nœud à générer par rapport à l'élément de ligne.  
  
 Cette section décrit le mappage des colonnes dans un ensemble de lignes sous différentes conditions et fournit des exemples.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Colonnes sans nom](../../relational-databases/xml/columns-without-a-name.md)  
  
-   [Colonnes avec nom](../../relational-databases/xml/columns-with-a-name.md)  
  
-   [Colonnes avec un nom spécifié sous la forme d'un caractère générique](../../relational-databases/xml/columns-with-a-name-specified-as-a-wildcard-character.md)  
  
-   [Colonnes avec le nom d’un test de nœud XPath](../../relational-databases/xml/columns-with-the-name-of-an-xpath-node-test.md)  
  
-   [Noms de colonnes avec le chemin d’accès spécifié sous la forme data&#40;&#41;](../../relational-databases/xml/column-names-with-the-path-specified-as-data.md)  
  
-   [Colonnes contenant une valeur NULL par défaut](../../relational-databases/xml/columns-that-contain-a-null-value-by-default.md)  
  
-   [Prise en charge d'espace de noms en mode PATH](../../relational-databases/xml/namespace-support-in-path-mode.md)  
  
-   [Exemples : Utilisation du mode PATH](../../relational-databases/xml/examples-using-path-mode.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des espaces de noms aux requêtes avec WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [FOR XML &#40;SQL Server&#41;](../../relational-databases/xml/for-xml-sql-server.md)  
  
  
