---
title: Renommer les connexions correspondant aux noms de rôle de serveur fixe | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- user-defined login names [SQL Server]
- fixed server roles [SQL Server]
- renamed logins [SQL Server]
- logins [SQL Server], names
ms.assetid: 10a1d77c-3153-474f-a6a0-969556794467
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d983f514f7cc0185021de40f153d78fd6e4dd112
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66092877"
---
# <a name="rename-logins-matching-fixed-server-role-names"></a>Renommer les accès correspondant aux noms de rôles serveur fixes
  Le Conseiller de mise à niveau a détecté un ou plusieurs noms de comptes de connexion définis par l'utilisateur correspondant aux noms des rôles serveur fixes. Les noms des rôles serveur fixes sont réservés. Renommez l'accès avant la mise à niveau.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Les noms de rôle serveur fixe suivants sont réservés et ne peuvent pas être utilisés comme noms de compte de connexion défini par l'utilisateur.  
  
-   **sysadmin**  
  
-   **serveradmin**  
  
-   **setupadmin**  
  
-   **securityadmin**  
  
-   **processadmin**  
  
-   **dbcreator**  
  
-   **diskadmin**  
  
-   **bulkadmin**  
  
## <a name="corrective-action"></a>Action corrective  
 Avant d'effectuer la mise à niveau, procédez comme suit :  
  
1.  Enregistrez les SID (identificateurs de sécurité) des connexions en exécutant l'instruction suivante.  
  
    ```  
    SELECT name, sid   
    FROM master.dbo.syslogins   
    WHERE name IN('sysadmin', 'serveradmin','setupadmin', 'securityadmin','processadmin', 'dbcreator','diskadmin','bulkadmin')  
    ```  
  
2.  Supprimez les connexions.  
  
3.  Utilisez le **sp_addlogin** procédure système pour créer des connexions. Spécifiez le SID retourné à l’étape 1 dans le **@sid** paramètre pour chaque connexion correspondante.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
