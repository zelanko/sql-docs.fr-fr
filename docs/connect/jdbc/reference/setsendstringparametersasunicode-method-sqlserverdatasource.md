---
title: Méthode setSendStringParametersAsUnicode (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setSendStringParametersAsUnicode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 49198d63-76cb-4843-8d04-e49b1fbb6916
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fe32325caccebd0e85204bbbc11b7a0cbe4eefca
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972993"
---
# <a name="setsendstringparametersasunicode-method-sqlserverdatasource"></a>Méthode setSendStringParametersAsUnicode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit une valeur **booléenne** qui indique si l’envoi de paramètres de type chaîne au serveur au format UNICODE est activé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setSendStringParametersAsUnicode(boolean sendStringParametersAsUnicode)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sendStringParametersAsUnicode*  
  
 Si elle a la valeur **true**, les paramètres de type string sont envoyés au serveur au format UNICODE. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Si la propriété sendStringParametersAsUnicode a la valeur **true** (valeur par défaut), les paramètres de type chaîne sont envoyés au serveur au format UNICODE. Si la propriété sendStringParametersAsUnicode a la valeur **false**, les paramètres de type chaîne sont envoyés au serveur au format ASCII/MBCS, et non UNICODE. Si sendStringParametersAsUnicode n’est pas défini, [getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md) retourne la valeur par défaut (**true**).  
  
 Pour plus d’informations sur la propriété de connexion sendStringParametersAsUnicode, consultez [définition des propriétés de connexion](../../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
