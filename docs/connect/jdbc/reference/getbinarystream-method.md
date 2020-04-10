---
title: Méthode getBinaryStream () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.getBinaryStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0c8f7741-daba-4c04-adc0-8d76345a899a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cd4742b7c327899d8f3f7a0ce2a6d091a74eee03
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921666"
---
# <a name="getbinarystream-method-"></a>Méthode getBinaryStream ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne un flux d'entrée pour la lecture des données depuis le BLOB.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.io.InputStream getBinaryStream()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Flux d'entrée contenant les données du BLOB.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getBinaryStream est spécifiée par la méthode getBinaryStream de l’interface java.sql.Blob.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerBlob, méthodes](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob, membres](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob, classe](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
