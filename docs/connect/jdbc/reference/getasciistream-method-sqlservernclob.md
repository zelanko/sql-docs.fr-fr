---
title: Méthode getAsciiStream (SQLServerNClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ff1d47e4-572a-4169-a631-ac261f7642b3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 22177442dcec9fb873d4a824b73845ce6fc9bfdf
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67954129"
---
# <a name="getasciistream-method-sqlservernclob"></a>Méthode getAsciiStream (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur **NCLOB** désignée par l’objet **NClob** sous forme de flux ASCII.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.InputStream getAsciiStream()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Objet InputStream contenant les données NCLOB.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getAsciiStream est spécifiée par la méthode getAsciiStream de l’interface java.sql.SQLServerNClob.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerNClob, méthodes](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob, membres](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob, classe](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
