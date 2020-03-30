---
title: setString, méthode (long, java.lang.String, int, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.setString (long, java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9fb59b09-e825-46a6-ba5d-85d4a8dc143a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5741f8ba74009327befc8f940e1d3b37df6ef1ea
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67972701"
---
# <a name="setstring-method-long-javalangstring-int-int"></a>Méthode setString (long, java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Écrit la chaîne donnée dans le CLOB, en démarrant à la position spécifiée et en fonction du décalage et de la longueur donnés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int setString(long pos,  
                     java.lang.String str,  
                     int offset,  
                     int len)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pos*  
  
 Position à laquelle démarrer l'écriture dans l'objet CLOB.  
  
 *str*  
  
 Chaîne à écrire sur l'objet CLOB.  
  
 *offset*  
  
 Décalage dans la chaîne à partir duquel démarrer la lecture des caractères.  
  
 *len*  
  
 Nombre de caractères à écrire.  
  
## <a name="return-value"></a>Valeur de retour  
 Nombre de caractères écrits.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode setString est spécifiée par la méthode setString de l’interface java.sql.NClob.  
  
 Les données de caractères sont remplacées, en démarrant à la position spécifiée et peuvent remplacer la longueur initiale de l'objet CLOB. La spécification d'une valeur position+1 permet d'ajouter la chaîne. La spécification d'une valeur position+2 ou supérieure (ou de zéro ou d'une valeur inférieure) génère une erreur de position.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode setString &#40;SQLServerClob&#41;](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)   
 [SQLServerClob, méthodes](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob, membres](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob, classe](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
