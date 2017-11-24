---
title: "Méthode valueOf (java.sql.Timestamp, int) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 114f55af-62ab-4c60-8724-0affbbbbbcdc
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2c79a5f486377bc86264377a898a9f908bbc7153
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="valueof-method-javasqltimestamp-int"></a>Méthode valueOf (java.sql.Timestamp, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un **DateTimeOffset** objet représentant un point dans le temps d’un décalage particulier à partir de l’heure GMT selon une valeur java.sql.Timestamp et une valeur indiquant le décalage en minutes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, int minutesOffset)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *timestamp*  
  
 Valeurjava.sql.Timestamp.  
  
 *minutesOffset*  
  
 Décalage en minutes.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un objet DateTimeOffset qui représente le point dans le temps indiqué par l’objet java.sql.Timestamp à l’offset donné, minutes, à l’heure GMT.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset, membres](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
