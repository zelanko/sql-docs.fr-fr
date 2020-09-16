---
description: Méthode setApplicationName (SQLServerDataSource)
title: Méthode setApplicationName (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setApplicationName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 24d6e48d-53c4-4da2-a6de-1cdff463c9cd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e237100c0c1da4ad9188da943412891d808a735c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432661"
---
# <a name="setapplicationname-method-sqlserverdatasource"></a>Méthode setApplicationName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nom de l'application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setApplicationName(java.lang.String applicationName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *applicationName*  
  
 **Chaîne** qui contient le nom de l’application.  
  
## <a name="remarks"></a>Notes  
 Le nom d’application est utilisé pour identifier l’application spécifique dans différents de profilage et de journalisation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si le nom d’application n’est pas défini, la méthode getApplicationName retourne la chaîne non localisée « [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ».  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
