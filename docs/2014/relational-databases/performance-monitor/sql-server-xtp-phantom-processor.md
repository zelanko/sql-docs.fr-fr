---
title: Processeur fantôme XTP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
caps.latest.revision: 4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 063fe5925c67e75381c4c97d17b5d7eba2125dfb
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43810665"
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
 [XTP &#40;In-Memory OLTP&#41; les compteurs de performances](../../integration-services/performance/performance-counters.md)  
  
  
