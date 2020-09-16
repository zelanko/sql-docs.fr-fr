---
description: Méthode getApplicationName (SQLServerDataSource)
title: Méthode getApplicationName (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getApplicationName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f71e501c-ccd7-4a1e-b6ea-4d47a81c18c6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3d558d088c8bd993183fe1bdac95fe8b40b213b4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437571"
---
# <a name="getapplicationname-method-sqlserverdatasource"></a>Méthode getApplicationName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Renvoie le nom de l'application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getApplicationName()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **Chaîne** qui contient le nom de l’application ou « [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] » si aucune valeur n’est définie.  
  
## <a name="remarks"></a>Notes  
 Le nom d’application est utilisé pour identifier l’application spécifique dans différents de profilage et de journalisation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si le nom d’application n’est pas défini, la méthode getApplicationName retourne la chaîne non localisée « [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ».  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
