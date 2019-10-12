---
title: Renommer les connexions correspondant aux noms de rôles serveur fixes | Microsoft Docs
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
ms.openlocfilehash: df9d9e51846e286c67a4773823207524755d15dc
ms.sourcegitcommit: 710d60e7974e2c4c52aebe36fceb6e2bbd52727c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72278218"
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
  
3.  Utilisez la procédure système **sp_addlogin** pour créer de nouvelles connexions. Spécifiez le SID retourné à l’étape 1 dans le paramètre **\@sid** pour chaque connexion correspondante.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau de Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller &#91;de mise à niveau de SQL Server 2014 nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
