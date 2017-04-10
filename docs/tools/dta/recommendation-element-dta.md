---
title: "Recommendation, &#233;l&#233;ment (Assistant Param&#233;trage de base de donn&#233;es) | Microsoft Docs"
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
  - "Recommendation (élément)"
ms.assetid: 679ea535-865a-4633-a4d3-5b3090515158
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# Recommendation, &#233;l&#233;ment (Assistant Param&#233;trage de base de donn&#233;es)
  Contient des informations sur les index hypothétiques qui font partie d'une configuration spécifiée par l'utilisateur.  
  
## Syntaxe  
  
```  
  
<Configuration>  
    ...code removed here...  
    <Table>  
      <Name>...</Name>  
      <Recommendation>  
      ...code removed here...  
      </Recommendation>  
```  
  
## Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Ce paramètre est facultatif. Utilisable une seule fois par élément **Table**.|  
  
## Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Table, élément pour les schémas &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/table-element-for-schema-dta.md)|  
|**Éléments enfants**|[Create, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/create-element-dta.md)<br /><br /> Élément **Drop**. Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## Notes  
 Cet élément porte le nom **RecommendationTypecomplexType** dans le schéma XML de l’Assistant Paramétrage du moteur de base de données. Il est utilisé pour spécifier des index dans une configuration hypothétique. Ne confondez pas cet élément **Recommendation** avec les autres types qui peuvent être utilisés pour spécifier le partitionnement (**RecommendationPType**) ou les vues (**RecommendationViewType**). Pour plus d’informations sur ces autres types d’éléments **Recommendation**, consultez le [schéma XML de l’Assistant Paramétrage du moteur de base de données](http://go.microsoft.com/fwlink/?linkid=43100).  
  
## Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  