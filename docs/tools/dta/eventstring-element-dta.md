---
title: "EventString, &#233;l&#233;ment (Assistant Param&#233;trage de base de donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
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
  - "EventString (élément)"
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# EventString, &#233;l&#233;ment (Assistant Param&#233;trage de base de donn&#233;es)
  Spécifie une charge de travail de script [!INCLUDE[tsql](../../includes/tsql-md.md)] directement dans le fichier d'entrée XML.  
  
## Syntaxe  
  
```  
  
<Workload>  
    <EventString Weight="...">  
    ...code removed here...  
    </EventString>  
</Workload>  
```  
  
## Attributs des éléments  
  
|Attribut|Description|  
|---------------|-----------------|  
|**Weight**|Ce paramètre est facultatif. Spécifie le facteur de pondération de la requête (facteur d'importance) pour l'événement spécifié. Utilisez un type de données **float** pour spécifier la pondération. Par exemple, **Weight**="100.01". La valeur minimale que vous pouvez spécifier pour **Weight** est « 0 ».|  
  
## Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|**string**, longueur illimitée.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une fois si aucun autre type de charge de travail n'est spécifié. Vous devez spécifier un élément enfant **EventString**, **File**ou **Database** pour le parent **Workload** , mais un seul type peut être utilisé. Par exemple, si vous spécifiez une charge de travail avec l'élément **EventString** , vous ne pouvez pas spécifier une charge de travail avec l'élément **File** dans le même fichier d'entrée XML.|  
  
## Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Workload, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/workload-element-dta.md)|  
|**Éléments enfants**|Aucun.|  
  
## Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez [Exemple de fichier d’entrée XML avec une charge de travail Inline &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md).  
  
## Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  