---
title: Méthode valueOf (java.sql.Timestamp, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 114f55af-62ab-4c60-8724-0affbbbbbcdc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c13438851fdc543a3567abdc001af5b5b9e726fc
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "68001561"
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
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un objet DateTimeOffset représentant le point dans le temps donné par l’objet java.sql.Timestamp au décalage donné, en minutes par rapport à l’heure GMT.  
  
## <a name="see-also"></a>Voir aussi  
 [DateTimeOffset, classe](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset, membres](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
