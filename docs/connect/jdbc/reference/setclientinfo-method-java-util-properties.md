---
description: Méthode setClientInfo (java.util.Properties)
title: Méthode setClientInfo (java.util.Properties) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b2a8ec0b-40a2-44d1-90d9-a810d4132e56
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 44c70b1f1a8bd88065ecee03cb85aa0ed7502208
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432191"
---
# <a name="setclientinfo-method-javautilproperties"></a>Méthode setClientInfo (java.util.Properties)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit la valeur des propriétés d'informations client de la connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setClientInfo (java.util.Properties properties)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *properties*  
  
 Objet Properties contenant la liste des propriétés d’informations client à définir.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setClientInfo est spécifiée par la méthode setClientInfo de l’interface java.sql.Connection.  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ne prend en charge aucune propriété d’informations client. Cette méthode génère des avertissements si le paramètre d’entrée *properties* ne fait pas référence à un jeu de propriétés vide. En d'autres termes, cette méthode génère des avertissements pour les propriétés que l'application souhaite définir. Les applications doivent utiliser la méthode [getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) pour récupérer chaque avertissement.  
  
## <a name="see-also"></a>Voir aussi  
 [setClientInfo, méthode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
