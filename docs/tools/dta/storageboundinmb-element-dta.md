---
title: "Storageboundinmb, élément (DTA) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: StorageBoundInMB element
ms.assetid: a8374910-bf68-4edb-b464-53a3a705e7f4
caps.latest.revision: "12"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d7377acefc270c6e497a1a8890ab6bea41a92fd1
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="storageboundinmb-element-dta"></a>StorageBoundInMB, élément (Assistant Paramétrage de base de données)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Spécifie l’espace maximal (en mégaoctets) qui peut être consommé par la recommandation de paramétrage de l’Assistant Paramétrage du moteur de base de données (index et le partitionnement du jeu).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <StorageBoundInMB>...</ StorageBoundInMB >  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|**unsignedInt**, longueur illimitée.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Ce paramètre est facultatif. Ne peut être utilisé qu'une seule fois pour l'élément **TuningOptions** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Élément TuningOptions &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Éléments enfants**|Aucune|  
  
## <a name="remarks"></a>Notes  
 Lorsque plusieurs bases de données sont paramétrées, les recommandations pour toutes les bases de données sont prises en compte pour le calcul de l'espace. Par défaut, l'Assistant Paramétrage du moteur de base de données utilise la plus petite taille des tailles de stockage suivantes :  
  
-   Trois fois la taille des données brutes, qui comprend la taille totale des segments et des index cluster sur les tables.  
  
-   L'espace libre disponible sur tous les lecteurs de disques connectés, plus la taille des données brutes.  
  
 La taille de stockage par défaut ne comprend pas les index non-cluster et les vues indexées.  
  
 Si la valeur spécifiée pour l'élément **StorageBoundInMB** dépasse celle de l'espace disque, l'Assistant Paramétrage du moteur de base de données renvoie une erreur mais continue le paramétrage. Une fois le paramétrage terminé, vous pouvez ajouter de l'espace disque si vous décidez d'appliquer la recommandation.  
  
## <a name="example"></a>Exemple  
  
## <a name="description"></a>Description  
 L'exemple de code suivant montre comment définir une limite de 1500 mégaoctets comme espace disque maximal consommable par une recommandation de réglage :  
  
## <a name="code"></a>Code  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <StorageBoundInMB>1500</StorageBoundInMB>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
