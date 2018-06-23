---
title: Processeur fantôme XTP | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
caps.latest.revision: 4
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bc489c0fc5be77e8dfaf2d2ea11a10515ec460e8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053276"
---
# <a name="xtp-phantom-processor"></a>Processeur fantôme XTP
  L'objet de performance Processeur fantôme XTP contient des compteurs connexes au sous-système de traitement fantôme du moteur XTP. Ce composant détecte les lignes fantômes dans les transactions exécutées dans le niveau d'isolation SERIALIZABLE.  
  
 Ce tableau décrit les compteurs **Processeur fantôme XTP** .  
  
|Compteur|Description|  
|-------------|-----------------|  
|**Nouvelles tentatives d'analyse d'angles inutilisés par seconde (sortie fantôme)**|Nombre de tentatives d'analyse dues à des conflits d'écriture lors des nettoyages d'angles inutilisés indiqué par le processeur fantôme (en moyenne), par seconde. Il s'agit d'un compteur de très bas niveau, non destiné au client.|  
|**Lignes fantômes expirées, supprimées par seconde**|Nombre de lignes expirées supprimées par les analyses fantômes (en moyenne), par seconde.|  
|**Lignes expirées fantômes, touchées par seconde**|Nombre de lignes expirées touchées par les analyses fantômes (en moyenne), par seconde.|  
|**Lignes expirant fantômes, touchées par seconde**|Nombre de lignes expirant touchées par les analyses fantômes (en moyenne), par seconde.|  
|**Lignes fantômes touchées par seconde**|Nombre de lignes touchées par les analyses fantômes (en moyenne), par seconde.|  
|**Analyses fantômes démarrées par seconde**|Nombre d'analyses fantômes démarrées (en moyenne), par seconde.|  
  
## <a name="see-also"></a>Voir aussi  
 [XTP &#40;OLTP en mémoire&#41; les compteurs de Performance](../../integration-services/performance/performance-counters.md)  
  
  