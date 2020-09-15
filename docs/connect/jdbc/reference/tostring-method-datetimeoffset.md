---
description: Méthode toString (DateTimeOffset)
title: Méthode toString (DateTimeOffset) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e77b9be3-1a02-4769-8acf-ac71d48d6a76
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 66931c3ada32b112de920aab3ac62fdb50fd40cd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431431"
---
# <a name="tostring-method-datetimeoffset"></a>Méthode toString (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne une représentation de chaîne de l’objet **DateTimeOffset**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public String toString()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Représentation de chaîne de l’objet **DateTimeOffset**.  
  
## <a name="remarks"></a>Notes  
 La chaîne respecte le format `YYYY-MM-DD HH:mm:ss[.fffffff] [+|-]HH:mm`.  
  
 Les fractions de seconde de la chaîne renvoyée sont remplies avec des zéros jusqu'à la précision déclarée. Par exemple, **datetimeoffset(6)** avec la valeur « 2010-03-10 12:34:56.78 -08:00 » sera mis en forme comme « 2010-03-10 12:34:56.780000 -08:00 » par DateTimeOffset.toString.  
  
## <a name="see-also"></a>Voir aussi  
 [DateTimeOffset, classe](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Membres de DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
