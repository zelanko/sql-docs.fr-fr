---
title: Méthode getSearchStringEscape (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSearchStringEscape
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ea0f95d0-0238-4dc8-9f26-7ff9b65f30c3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a12b9ca70dd8e48fa92df9b1b2be55b22ee6994
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721357"
---
# <a name="getsearchstringescape-method-sqlserverdatabasemetadata"></a>Méthode getSearchStringEscape (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la **String** qui peut être utilisée pour placer les caractères génériques dans une séquence d’échappement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getSearchStringEscape()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **chaîne** qui contient la chaîne de caractères génériques d’échappement.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getSearchStringEscape est spécifiée par la méthode getSearchStringEscape dans l’interface java.sql.DatabaseMetaData.  
  
 Cette méthode est utilisée uniquement pour les recherches de modèles de métadonnées. Elle retourne « \\ ». Un modèle de recherche **String** peut placer des caractères génériques (« % » et « _ ») dans une séquence d’échappement et les fournir sous forme de littéraux en ajoutant en préfixe une barre oblique inverse. Cela permet de traduire « \\% » en « [%] » et « \\\_ » en « [\_] ».  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
