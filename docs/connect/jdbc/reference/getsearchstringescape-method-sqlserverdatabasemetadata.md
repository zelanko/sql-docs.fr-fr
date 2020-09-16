---
description: Méthode getSearchStringEscape (SQLServerDatabaseMetaData)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5801a6a971a0714af8408fa15c206770b9101bd5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434631"
---
# <a name="getsearchstringescape-method-sqlserverdatabasemetadata"></a>Méthode getSearchStringEscape (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la **String** qui peut être utilisée pour placer les caractères génériques dans une séquence d’échappement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getSearchStringEscape()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **Chaîne** contenant la chaîne de caractères génériques d’échappement.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getSearchStringEscape est spécifiée par la méthode getSearchStringEscape de l’interface java.sql.DatabaseMetaData.  
  
 Cette méthode est utilisée uniquement pour les recherches de modèles de métadonnées. Elle retourne « \\ ». Un modèle de recherche **String** peut placer des caractères génériques (« % » et « _ ») dans une séquence d’échappement et les fournir sous forme de littéraux en ajoutant en préfixe une barre oblique inverse. Cela permet de traduire « \\% » en « [%] » et « \\\_ » en « [\_] ».  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
