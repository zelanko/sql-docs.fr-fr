---
title: Méthode valueOf (java.sql.Timestamp, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 114f55af-62ab-4c60-8724-0affbbbbbcdc
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 290878fc0a3687a95fd6335eba4b6ed6e1c2fda2
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979181"
---
# <a name="valueof-method-javasqltimestamp-int"></a>Méthode valueOf (java.sql.Timestamp, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un objet **DateTimeOffset** représentant un point précis dans le temps d’un décalage particulier par rapport à l’heure GMT selon une valeur java.sql.Timestamp et une valeur indiquant le décalage en minutes.  
  
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
 Retourne un objet DateTimeOffset qui représente le point dans le temps indiqué par l’objet java.sql.Timestamp à l’offset donné, minutes, par rapport à GMT.  
  
## <a name="see-also"></a> Voir aussi  
 [DateTimeOffset, classe](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset, membres](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
