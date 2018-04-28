---
title: Méthode valueOf (java.sql.Timestamp, java.util.Calendar) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7320c383-0b06-446d-963b-7005e50324a2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8ac7bdcc4c1d4ba0cc55824d3b49be9470fe20e0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="valueof-method-javasqltimestamp-javautilcalendar"></a>Méthode valueOf (java.sql.Timestamp, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un **DateTimeOffset** objet représentant un point dans le temps d’un décalage particulier à partir de l’heure GMT selon une valeur java.sql.Timestamp et une valeur java.util.Calendar indiquant le décalage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, java.util.Calendar calendar)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *timestamp*  
  
 Valeurjava.sql.Timestamp.  
  
 *Calendrier*  
  
 Valeur de décalage.  Les composants de date et heure de *calendrier* définira conformément à la *timestamp* valeur.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un objet DateTimeOffset qui représente le point dans le temps spécifié par l’objet java.sql.Timestamp sur fuseau horaire de l’objet java.util.Calendar donné.  
  
## <a name="remarks"></a>Notes  
 Cette méthode définit également l’objet java.util.Calendar au point dans le temps spécifié par l’objet java.sql.Timestamp.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset, membres](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
