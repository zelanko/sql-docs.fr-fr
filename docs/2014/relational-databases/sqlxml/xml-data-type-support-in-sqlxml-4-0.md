---
title: prise en charge du Type de données dans SQLXML 4.0 XML | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, xml data type support
- xml data type [SQL Server], SQLXML
ms.assetid: 9a6f5ad8-4a8f-4de7-ac17-81d5ccf78459
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1a0fa49a1dac16ed366c66c72f7d800ccc4aed8e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52750619"
---
# <a name="xml-data-type-support-in-sqlxml-40"></a>Prise en charge du type de données xml dans SQLXML 4.0
  À partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge XML typées à l’aide de données le `xml` type de données. Cette rubrique fournit des informations sur la façon dont SQLXML 4.0 reconnaît les instances du type de données `xml` et implémente leur prise en charge.  
  
## <a name="working-with-xml-data-types"></a>Utilisation des types de données xml  
 Pour mieux comprendre l'utilisation des tables SQL qui implémentent des colonnes de type de données `xml`, les exemples suivants sont fournis :  
  
|Tâche|Exemple|Rubrique|  
|----------|-------------|-----------|  
|Comment mapper et inclure une colonne `xml` dans une vue XML|« Mappage d'un élément XML à une colonne de type de données XML »|[Mappage par défaut d’éléments XSD et d’attributs aux Tables et colonnes &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)|  
|Comment insérer des données dans une colonne `xml` avec des codes de mise à jour (updategrams)|« Insertion de données dans une colonne de type de données XML »|[Insertion de données à l’aide de codes XML &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)|  
|Chargement en masse de données XML dans une colonne `xml`|« Chargement en masse dans les colonnes de type de données xml »|[Exemples de chargement en masse XML &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)|  
  
## <a name="guidelines-and-limitations"></a>Instructions et limitations  
  
-   **\<XSD : n’importe quel >** ne peut pas être mappé à une colonne, y compris un `xml` type de données. La prise en charge de ce scénario en SQLXML est fournie via l'annotation `sql:overflow-field`. Une autre solution consiste à mapper un champ de type de données `xml` en tant qu'élément de `xsd:anyType`. Cette solution est illustrée dans l'exemple de mappage d'un élément XML à une colonne de type de données XML, référencé dans le tableau ci-dessus.  
  
-   L'interrogation par une requête XPath du contenu de colonnes de type de données `xml` n'est pas prise en charge.  
  
-   L'utilisation d'une colonne de type de données `xml` dans les annotations où cela n'est pas pris en charge (par exemple `sql:relationship` et `sql:key-fields`) ni autorisé, provoque des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui ne sont pas interceptées par les composants de couche intermédiaire implémentant SQLXML 4.0. Cela se produit, car SQLXML ne requiert pas d'informations de type SQL. Ce comportement est semblable à celui de SQLXML pour les autres types de données, par exemple les types BLOB et binaires.  
  
-   Le mappage de colonnes `xml` est pris en charge uniquement pour les schémas XSD. Les schémas XDR ne prennent pas en charge le mappage de colonnes `xml`.  
  
-   SQLXML 4.0 s'appuie sur la prise en charge de l'analyse XML fournie dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Une colonne `xml` peut être mappée en tant que colonne XML typée ou non typée. Dans les deux cas, SQLXML 4.0 ne valide pas le code XML d'entrée.  Si le code XML d'entrée n'est pas valide ou s'il est incorrect, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le signale à SQLXML et propage toutes les informations d'erreur pertinentes retournées par le serveur à l'utilisateur.  
  
-   SQLXML 4,0 s'appuie sur la prise en charge limitée des DTD a fourni dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. permet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DTD interne dans les données de type de données d'`xml`, qui peuvent être utilisées pour fournir des valeurs par défaut et remplacer des références d'entité par leur contenu développé. SQLXML passe les données XML « en l'état » (y compris la DTD interne) au serveur. Vous pouvez convertir les DTD en documents XSD (XML Schema Documents) à l'aide d'outils tiers, puis charger les données avec des schémas XSD insérés dans la base de données.  
  
-   SQLXML 4.0 ne conserve pas les instructions de traitement de déclaration XML (par exemple), en fonction du comportement de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. À la place, la déclaration XML est traitée comme une directive pour l'analyseur XML [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; en outre, ses attributs (version, encoding et standalone) sont perdus une fois que les données ont été converties vers le type de données `xml`. Les données XML sont stockées en interne au format UCS-2. Toutes les autres instructions de traitement dans l'instance XML sont conservées ; elles sont autorisées dans la colonne `xml` et peuvent être prises en charge par SQLXML.  
  
## <a name="see-also"></a>Voir aussi  
 [Données XML &#40;SQL Server&#41;](../xml/xml-data-sql-server.md)  
  
  
