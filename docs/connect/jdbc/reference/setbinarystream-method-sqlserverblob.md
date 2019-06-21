---
title: setbinarystream, méthode (SQLServerBlob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.setBinaryStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: abcec31f-1a60-4765-9725-8cf7e9f1f8ab
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3ca2b8afe197c2509f0a2633266ea21c619bdeb1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66764684"
---
# <a name="setbinarystream-method-sqlserverblob"></a>Méthode setBinaryStream (SQLServerBlob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère un flux qui permet d'écrire sur la valeur du BLOB.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.io.OutputStream setBinaryStream(long pos)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Pos*  
  
 Position dans la valeur BLOB à laquelle démarrer l'écriture.  
  
## <a name="return-value"></a>Valeur retournée  
 Flux de sortie.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode setBinaryStream est spécifiée par la méthode setBinaryStream dans l’interface java.sql.Blob.  
  
 Les données dans le BLOB sont remplacées par le flux de sortie à partir de la position spécifiée et peuvent dépasser la longueur initiale du BLOB. Si vous spécifiez une valeur position+1, des octets sont ajoutés. Le passage d'une valeur position+2 ou supérieure (ou inférieure ou égale à zéro) génère une erreur de position.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerBlob, méthodes](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob, membres](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob, classe](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
