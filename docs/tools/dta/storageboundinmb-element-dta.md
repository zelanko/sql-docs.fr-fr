---
title: "StorageBoundInMB, &#233;l&#233;ment (Assistant Param&#233;trage de base de donn&#233;es) | Microsoft Docs"
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
  - "StorageBoundInMB (élément)"
ms.assetid: a8374910-bf68-4edb-b464-53a3a705e7f4
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# StorageBoundInMB, &#233;l&#233;ment (Assistant Param&#233;trage de base de donn&#233;es)
  Spécifie l'espace maximal, en mégaoctets, pouvant être consommé par la recommandation de paramétrage de l'Assistant Paramétrage du moteur de base de données (jeu d'index et de partitions).  
  
## Syntaxe  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <StorageBoundInMB>...</ StorageBoundInMB >  
```  
  
## Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|**unsignedInt**, longueur illimitée.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Ce paramètre est facultatif. Ne peut être utilisé qu'une seule fois pour l'élément **TuningOptions** .|  
  
## Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[TuningOptions, élément &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Éléments enfants**|Aucune|  
  
## Notes  
 Lorsque plusieurs bases de données sont paramétrées, les recommandations pour toutes les bases de données sont prises en compte pour le calcul de l'espace. Par défaut, l'Assistant Paramétrage du moteur de base de données utilise la plus petite taille des tailles de stockage suivantes :  
  
-   Trois fois la taille des données brutes, qui comprend la taille totale des segments et des index cluster sur les tables.  
  
-   L'espace libre disponible sur tous les lecteurs de disques connectés, plus la taille des données brutes.  
  
 La taille de stockage par défaut ne comprend pas les index non-cluster et les vues indexées.  
  
 Si la valeur spécifiée pour l'élément **StorageBoundInMB** dépasse celle de l'espace disque, l'Assistant Paramétrage du moteur de base de données renvoie une erreur mais continue le paramétrage. Une fois le paramétrage terminé, vous pouvez ajouter de l'espace disque si vous décidez d'appliquer la recommandation.  
  
## Exemple  
  
## Description  
 L'exemple de code suivant montre comment définir une limite de 1500 mégaoctets comme espace disque maximal consommable par une recommandation de réglage :  
  
## Code  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <StorageBoundInMB>1500</StorageBoundInMB>  
...code removed here...  
</DTAInput>  
```  
  
## Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  