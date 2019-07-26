---
title: Méthode getSubString (SQLServerNClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1d91c930-1bac-4da9-b9a5-ac2cfd31541b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cf2caa03e047bb53ca946153205492c417448e85
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979318"
---
# <a name="getsubstring-method-sqlservernclob"></a>Méthode getSubString (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une copie de la sous-chaîne spécifiée dans le **NCLOB**, en fonction de la position de départ spécifiée et du nombre de caractères à copier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getSubString(long pos,  
                                  int length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pos*  
  
 Premier caractère de la sous-chaîne à extraire. Le premier caractère est à la position 1.  
  
 *length*  
  
 Nombre des caractères consécutifs à copier.  
  
## <a name="return-value"></a>Valeur retournée  
 **Chaîne** qui est la sous-chaîne spécifiée dans **NCLOB**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getSubString est spécifiée par la méthode getSubString de l’interface java.sql.NClob.  
  
 La tentative d'obtention de zéro caractère depuis un NCLOB avec une valeur Null ou de longueur zéro retourne une chaîne vide. La tentative d'obtention d'une longueur de caractères quelconque à n'importe quelle position autre que la position 1 dans un NCLOB de longueur zéro entraîne la levée d'une exception de position.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerNClob, méthodes](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob, membres](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob, classe](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
