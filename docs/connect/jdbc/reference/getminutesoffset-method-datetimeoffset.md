---
title: Méthode getMinutesOffset (DateTimeOffset) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 18ba844a-ea36-42de-87da-bbc222082efe
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 350a1f63eefa87eccbca7ba0a12c4381ab820854
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80906160"
---
# <a name="getminutesoffset-method-datetimeoffset"></a>Méthode getMinutesOffset (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le décalage, en minutes, par rapport à l’heure GMT, de cet objet DateTimeOffset.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getMinutesOffset()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Décalage en minutes.  
  
## <a name="remarks"></a>Notes  
 Pour un objet DateTimeOffset représentant le 8 mars 2010, 11:35:48 -0800, getMinutesOffset retourne la valeur 480.  
  
## <a name="see-also"></a>Voir aussi  
 [DateTimeOffset, classe](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset, membres](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
