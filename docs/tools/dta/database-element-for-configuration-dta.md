---
title: "Database, &#233;l&#233;ment pour les configurations (Assistant Param&#233;trage de base de donn&#233;es) | Microsoft Docs"
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
  - "Database (élément)"
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# Database, &#233;l&#233;ment pour les configurations (Assistant Param&#233;trage de base de donn&#233;es)
  Spécifie la base de données dans laquelle vous souhaitez que l’Assistant Paramétrage du moteur de base de données évalue la configuration hypothétique (spécifiée par l’élément **Configuration**).  
  
## Syntaxe  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une ou plusieurs fois par élément **Server**.|  
  
## Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Server, élément pour les configurations &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/server-element-for-configuration-dta.md)|  
|**Éléments enfants**|[Name, élément pour les bases de données &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/name-element-for-database-dta.md)<br /><br /> [Schema, élément pour les bases de données &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/schema-element-for-database-dta.md)<br /><br /> [Recommendation, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/recommendation-element-dta.md)|  
  
## Notes  
 Cet élément porte le nom **DatabaseTypecomplexType** dans le schéma XML de l’Assistant Paramétrage du moteur de base de données. Ne confondez pas cet élément **Database** avec celui dont le parent racine est l’élément **Server**, qui se trouve en haut du fichier d’entrée XML. Pour plus d’informations, consultez [Database, élément pour les serveurs &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/database-element-for-server-dta.md).  
  
## Exemple  
 Pour obtenir un exemple d’utilisation de cet élément **Database**, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  