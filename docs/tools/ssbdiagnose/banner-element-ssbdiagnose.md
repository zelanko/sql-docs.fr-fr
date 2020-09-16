---
description: Élément Banner (ssbdiagnose)
title: Élément Banner
diagnose: In SQL Server, the Banner element identifies which utility generated the ssbdiagnose output XML file.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- banner element
- XML output file format [ssbdiagnose], banner element
- ssbdiagnose
ms.assetid: cc6cd49a-acf0-4cfb-8c6a-554692b89de2
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: dae521477b4255c6e4f697631960d4647e736f01
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484942"
---
# <a name="banner-element-ssbdiagnose"></a>Élément Banner (ssbdiagnose)


 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Identifie quel utilitaire a généré le fichier de sortie XML **ssbdiagnose** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Banner  
    title="..."   
    product="..."   
    version="..." />  
```  
  
## <a name="element-attributes"></a>Attributs des éléments  
  
|Attribut|Description|  
|---------------|-----------------|  
|**title**|Identifie l’utilitaire qui a généré le fichier de sortie XML **ssbdiagnose** .|  
|**product**|Identifie le produit qui a généré le fichier de sortie XML **ssbdiagnose** .|  
|**version**|Identifie quelle version de l'utilitaire a généré le fichier de sortie XML.|  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Se produit une fois par fichier de sortie XML **ssbdiagnose** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Élément DiagnosticInformation &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)|  
|**Éléments enfants**|Aucun.|  
  
## <a name="example"></a>Exemple  
 Exemple d'élément Banner.  
  
```  
<Banner title="Service Broker Diagnostics Utility" product="Microsoft SQL Server" version="10.0.1073.0" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire ssbdiagnose &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
