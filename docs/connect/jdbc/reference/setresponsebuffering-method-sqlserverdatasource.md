---
title: Méthode setResponseBuffering (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: c9e43ff2-8117-4dca-982d-83c863d0c8e1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f5bfc0fb1d1a74131d0e8e71055356f958a9b508
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67973099"
---
# <a name="setresponsebuffering-method-sqlserverdatasource"></a>Méthode setResponseBuffering (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le mode de mise en mémoire tampon des réponses pour les connexions créées avec cet objet [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *value*  
  
 **Chaîne** qui contient la mise en mémoire tampon et le mode de diffusion en continu. Le mode valide peut être l’une des chaînes non sensibles à la casse suivantes : **full** ou **adaptive**.  
  
## <a name="remarks"></a>Notes  
 La valeur **full** consiste à lire l’intégralité du résultat du serveur à l’exécution.  
  
 La valeur **adaptive** consiste à mettre en mémoire tampon le moins de données possible si nécessaire. La valeur **adaptive** correspond au mode de mise en mémoire tampon par défaut.  
  
 Pour plus d’informations sur l’utilisation du mode de mise en mémoire tampon des réponses, consultez Utilisation de la [mise en mémoire tampon adaptative](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
