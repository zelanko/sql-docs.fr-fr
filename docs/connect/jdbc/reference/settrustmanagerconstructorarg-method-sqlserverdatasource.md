---
title: Méthode setTrustManagerConstructorArg (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setTrustManagerConstructorArg
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 13eb5b436bc813ae448fd88045e2726ab6a0ebcc
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67972219"
---
# <a name="settrustmanagerconstructorarg-method-sqlserverdatasource"></a>setTrustManagerConstructorArg, méthode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit la valeur de chaîne de la propriété de connexion TrustManagerConstructorArg.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setTrustManagerConstructorArg(java.lang.String trustManagerClass)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *trustManagerClass*  
  
 **Chaîne** contenant le nom de classe complet d’un paramètre javax.net.ssl.TrustManager personnalisé.
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
