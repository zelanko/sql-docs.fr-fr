---
title: Prise en charge du type de données xml dans SQLXML 4.0
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, xml data type support
- xml data type [SQL Server], SQLXML
ms.assetid: 9a6f5ad8-4a8f-4de7-ac17-81d5ccf78459
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4c56efd6c79b7ce7d74af621963f4b12e734d5f9
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75252170"
---
# <a name="xml-data-type-support-in-sqlxml-40"></a>Prise en charge du type de données xml dans SQLXML 4.0
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  À partir [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , prend en charge les données typées XML à l’aide du type de données **XML** . Cette rubrique fournit des informations sur la façon dont SQLXML 4,0 reconnaît les instances du type de données **XML** et en implémente la prise en charge.  
  
## <a name="working-with-xml-data-types"></a>Utilisation des types de données xml  
 Pour en savoir plus sur l’utilisation des tables SQL qui implémentent des colonnes de type de données **XML** , les exemples suivants sont fournis :  
  
|Tâche|Exemple|Rubrique|  
|----------|-------------|-----------|  
|Mappage et inclusion d’une colonne **XML** dans une vue XML|« Mappage d'un élément XML à une colonne de type de données XML »|[Mappage par défaut d’éléments et d’attributs XSD à des tables et des colonnes &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)|  
|Insertion de données dans une colonne **XML** avec codes|« Insertion de données dans une colonne de type de données XML »|[Insertion de données à l’aide de XML codes &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)|  
|Chargement en masse de données XML dans une colonne **XML**|« Chargement en masse dans les colonnes de type de données xml »|[Exemples de chargement en masse XML &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)|  
  
## <a name="guidelines-and-limitations"></a>Instructions et limitations  
  
-   xsd : tout>ne peut pas être mappé à une colonne, y compris un type de données **XML** . ** \<** La prise en charge dans SQLXML pour ce scénario est fournie par le biais de l’annotation **SQL : overflow-field** . Une autre solution consiste à mapper un champ de type de données **XML** en tant qu’élément de **xsd : anyType**. Cette solution est illustrée dans l'exemple de mappage d'un élément XML à une colonne de type de données XML, référencé dans le tableau ci-dessus.  
  
-   La requête XPath dans le contenu des colonnes de type de données **XML** n’est pas prise en charge.  
  
-   L’utilisation d’une colonne de type de données **XML** dans les annotations où elle n’est pas prise en charge (par exemple, **SQL : Relationship** et **SQL : key-fields**) ou allowed entraîne des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erreurs qui ne seront pas interceptées par les composants de couche intermédiaire qui implémentent SQLXML 4,0. Cela se produit, car SQLXML ne requiert pas d'informations de type SQL. Ce comportement est semblable à celui de SQLXML pour les autres types de données, par exemple les types BLOB et binaires.  
  
-   Le mappage des colonnes **XML** est pris en charge uniquement pour les schémas XSD. Les schémas XDR ne prennent pas en charge le mappage de colonnes **XML** .  
  
-   SQLXML 4.0 s'appuie sur la prise en charge de l'analyse XML fournie dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Une colonne **XML** peut être mappée en tant que XML TYPÉ ou XML non typé. Dans les deux cas, SQLXML 4.0 ne valide pas le code XML d'entrée.  Si le code XML d'entrée n'est pas valide ou s'il est incorrect, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le signale à SQLXML et propage toutes les informations d'erreur pertinentes retournées par le serveur à l'utilisateur.  
  
-   SQLXML 4,0 s'appuie sur la prise en charge limitée des DTD a fourni dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]autorise une DTD interne dans les données de type de données **XML** , qui peut être utilisée pour fournir des valeurs par défaut et remplacer des références d’entité par leur contenu développé. SQLXML passe les données XML « en l'état » (y compris la DTD interne) au serveur. Vous pouvez convertir les DTD en documents XSD (XML Schema Documents) à l'aide d'outils tiers, puis charger les données avec des schémas XSD insérés dans la base de données.  
  
-   SQLXML 4,0 ne conserve pas les instructions de traitement de déclaration XML (par exemple,) en fonction [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]du comportement de. Au lieu de cela, la déclaration XML est traitée comme une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] directive de l’analyseur XML, et ses attributs (version, encodage et autonome) sont perdus une fois les données converties en type de données **XML** . Les données XML sont stockées en interne au format UCS-2. Toutes les autres instructions de traitement dans l’instance XML sont conservées ; elles sont autorisées dans la colonne **XML** et peuvent être prises en charge par SQLXML.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server de &#40;de données XML&#41;](../../relational-databases/xml/xml-data-sql-server.md)  
  
  
