---
title: "Create, &#233;l&#233;ment (Assistant Param&#233;trage de base de donn&#233;es) | Microsoft Docs"
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
  - "Create, élément (Assistant Paramétrage de base de données)"
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# Create, &#233;l&#233;ment (Assistant Param&#233;trage de base de donn&#233;es)
  Contient des informations sur les index, les statistiques ou les structures de segments d'une configuration spécifiée par l'utilisateur.  
  
## Syntaxe  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une fois pour chaque type de structure PDS (index, statistiques ou structures de segments).|  
  
## Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Recommendation, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/recommendation-element-dta.md)|  
|**Éléments enfants**|[Index, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/index-element-dta.md)<br /><br /> Élément **Statistics** (pour plus d’informations, consultez [Database Engine Tuning Advisor XML schema](http://schemas.microsoft.com/sqlserver/) (Schéma XML de l’Assistant Paramétrage du moteur de base de données))<br /><br /> Élément **Heap** (pour plus d’informations, consultez [Database Engine Tuning Advisor XML schema](http://schemas.microsoft.com/sqlserver/) (Schéma XML de l’Assistant Paramétrage du moteur de base de données))|  
  
## Notes  
 Cet élément porte le nom **CreateTypecomplexType** dans le schéma XML de l’Assistant Paramétrage du moteur de base de données. Il est utilisé pour créer des index, des statistiques ou des structures de segments pour une configuration spécifiée par l'utilisateur. Ne confondez pas cet élément **Create** avec les autres types d’éléments qui peuvent être utilisés pour créer des vues (**CreateViewType**) ou des partitions (**CreatePType**). Pour plus d’informations sur les autres types d’éléments **Create**, consultez [Database Engine Tuning Advisor XML schema](http://schemas.microsoft.com/sqlserver/) (Schéma XML de l’Assistant Paramétrage du moteur de base de données).  
  
## Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  