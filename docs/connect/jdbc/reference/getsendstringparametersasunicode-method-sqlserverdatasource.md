---
title: Méthode getSendStringParametersAsUnicode (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getSendStringParametersAsUnicode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3836d0ab-c3fb-41ff-bb89-10389594ae51
author: MightyPen
ms.author: genemi
ms.openlocfilehash: df27a5368dfea7f417fb84e2ebe38a8987165aec
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67979972"
---
# <a name="getsendstringparametersasunicode-method-sqlserverdatasource"></a>Méthode getSendStringParametersAsUnicode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne une valeur **booléenne** qui indique si l’envoi de paramètres de type chaîne au serveur au format UNICODE est activé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean getSendStringParametersAsUnicode()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Si elle a la valeur **true**, les paramètres de type string sont envoyés au serveur au format UNICODE. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Si la propriété sendStringParametersAsUnicode a la valeur **true** (valeur par défaut), les paramètres de type chaîne sont envoyés au serveur au format UNICODE. Si la propriété sendStringParametersAsUnicode a la valeur **false**, les paramètres de type chaîne sont envoyés au serveur au format ASCII/MBCS, et non UNICODE. Si sendStringParametersAsUnicode n’est pas défini, getSendStringParametersAsUnicode retourne la valeur par défaut (**true**).  
  
 Pour plus d’informations sur la propriété de connexion sendStringParametersAsUnicode, consultez [Définir les propriétés de connexion](../../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
