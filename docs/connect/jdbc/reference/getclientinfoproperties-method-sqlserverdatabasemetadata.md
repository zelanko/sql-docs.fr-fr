---
title: Méthode getClientInfoProperties (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1568aef4-f4c4-40a0-a1ab-9c106905bd92
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 08b919ec6b626cd61b757b380d24efffcada0d55
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67953103"
---
# <a name="getclientinfoproperties-method-sqlserverdatabasemetadata"></a>Méthode getClientInfoProperties (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une liste de propriétés d'informations clientes prises en charge par le pilote.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getClientInfoProperties()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Objet ResultSet.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getClientInfoProperties est spécifiée par la méthode getClientInfoProperties de l’interface java.sql.DatabaseMetaData.  
  
> [!NOTE]  
>  Cette méthode retourne un jeu de résultats vide. Le pilote prend uniquement en charge le paramétrage d’**applicationName** et ne définit **applicationName** que lors de la connexion. SQL Server ne prend pas en charge la mise à jour des informations d'application cliente une fois la connexion établie.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
