---
title: "Table, &#233;l&#233;ment pour les sch&#233;mas (Assistant Param&#233;trage de base de donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "XML"
helpviewer_keywords: 
  - "Table (élément) [Assistant Paramétrage de base de données]"
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# Table, &#233;l&#233;ment pour les sch&#233;mas (Assistant Param&#233;trage de base de donn&#233;es)
  Spécifie la table pour le paramétrage.  
  
## Syntaxe  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## Attributs des éléments  
  
|Attribut|Description|  
|---------------|-----------------|  
|**NumberOfRows**|Ce paramètre est facultatif. Entier qui vous permet de simuler des tables de différentes tailles.|  
  
## Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|**string**, entre 1 et 255 caractères.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Ce paramètre est facultatif. Répertoriez autant de tables que nécessaire pour votre charge de travail.|  
  
## Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Schema, élément pour les bases de données &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/schema-element-for-database-dta.md)|  
|**Éléments enfants**|[Name, élément pour les tables &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/name-element-for-table-dta.md)|  
  
## Notes  
 Si vous ne spécifiez pas d'élément **Table** , l'Assistant Paramétrage du moteur de base de données suppose que toutes les tables sur la base de données spécifiée peuvent être paramétrées.  
  
## Exemple  
 Pour obtenir un exemple d’utilisation, consultez [Server, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/server-element-dta.md).  
  
## Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  