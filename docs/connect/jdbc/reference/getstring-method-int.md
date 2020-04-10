---
title: Méthode getString (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getString (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f3fce8bf-8d6e-476f-aa6d-992daa79b899
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 92344de125e7711858d6a365eac1bdcadd109cef
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926258"
---
# <a name="getstring-method-int"></a>Méthode getString (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant que **chaîne** dans le langage de programmation Java en fonction de l’index du paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getString(int index)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 **int** indiquant l’index du paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur de **chaîne**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getString est spécifiée par la méthode getString de l’interface java.sql.CallableStatement.  
  
 Toutes les colonnes dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peuvent être retournées en tant que chaîne. Cela signifie qu'une représentation de chaîne de tous les types à base de nombres et de caractères, et une représentation de chaîne hexadécimale des colonnes binaires telles que binary, varbinary, varbinary(max), image, timestamp et uniqueidentifier, peuvent être retournées.  
  
 Les types sensibles à l'emplacement tels que money, smallmoney, datetime, smalldatetime, float, real, decimal et numeric retourneront le format toString() canonique pour la valeur sous-jacente du type.  
  
 Les types définis par l'utilisateur sont retournés en tant que valeurs de chaînes hexadécimales.  
  
## <a name="see-also"></a>Voir aussi  
 [getString, méthode (SQLServerCallableStatement)](../../../connect/jdbc/reference/getstring-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
