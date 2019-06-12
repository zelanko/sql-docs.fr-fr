---
title: getXopenStates, méthode (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de6fdf6b-8345-4490-b35e-7115b61e782e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c0a3859c3195d14243ff570493d3ae04c72d0780
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66768805"
---
# <a name="getxopenstates-method-sqlserverdatasource"></a>Méthode getXopenStates (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne une valeur **booléenne** qui indique si la conversion d'états SQL en états compatibles XOPEN est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean getXopenStates()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si la conversion d’états SQL en États compatibles xopen est activée. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Si la propriété xopenStates a la valeur **true**, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] convertit les états SQL en états compatibles XOPEN. La valeur par défaut est **false**, qui entraîne le pilote JDBC à générer des codes d'état SQL 99. Si xopenStates n’a aucune valeur, la méthode getXopenStates retourne la valeur par défaut **false**.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
