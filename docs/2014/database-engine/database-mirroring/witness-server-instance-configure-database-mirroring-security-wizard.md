---
title: Instance de serveur témoin (Assistant Configuration de la sécurité de la mise en miroir de bases de données) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.witnsrvr.f1
ms.assetid: b5763663-984a-473b-93a3-6cd3322ad41c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7db00b9deeb5faad62731aa666c54fa385be765b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62753971"
---
# <a name="witness-server-instance-configure-database-mirroring-security-wizard"></a>Instance de serveur témoin (Assistant Configuration de la sécurité de la mise en miroir de bases de données)
  Utilisez cette page pour spécifier des informations sur l'instance du serveur qui fera office de témoin pour cette session.  
  
> [!NOTE]  
>  Une instance de serveur témoin n'est pas disponible dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 **Pour configurer la mise en miroir de bases de données à l'aide de SQL Server Management Studio**  
  
-   [Établir une session de mise en miroir de bases de données au moyen de l’authentification Windows &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Démarrer l’Assistant Configuration de la sécurité de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Options  
 **Instance de serveur témoin**  
 Si une instance de serveur témoin est déjà spécifiée (dans la page **Mise en miroir** de la boîte de dialogue **Propriétés de la base de données** ), cette instance est affichée (pour plus d’informations, consultez [Propriétés de la base de données &#40;page Mise en miroir&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)).  
  
 Sinon, cette zone de liste affiche le nom du serveur actuel. Notez que l'instance de serveur témoin ne peut pas être la même que l'instance du principal ou du serveur miroir.  
  
 **Se connecter**  
 Si aucune instance de serveur témoin n’a été spécifiée, cliquez sur **Se connecter**. Dans la boîte de dialogue **Se connecter au serveur** qui s’affiche, vous pouvez spécifier l’instance de serveur et établir une connexion.  
  
 Si l’instance a été spécifiée, mais que l’Assistant ne propose pas de connexion doté d’autorisations suffisantes pour vérifier l’existence du point de terminaison, cliquez sur **Se connecter**. Dans la boîte de dialogue **Se connecter au serveur** qui s’affiche, l’instance de serveur est présélectionnée et ne peut pas être modifiée. Spécifiez un compte de domaine qui possède une autorisation suffisante et connectez-vous à l'instance du serveur.  
  
> [!NOTE]  
>  Au moment de se connecter à l’instance du serveur, l’Assistant de configuration de la sécurité de mise en miroir de bases de données utilise les informations d’identification fournies dans la boîte de dialogue **Se connecter au serveur** . Celles-ci diffèrent des informations d'identification d'une session de mise en miroir, qui utilise les informations d'identification du compte de démarrage où l'instance de serveur est en cours d'exécution en tant que service.  
  
 **Port d'écoute**  
 Le comportement de cette option varie comme suit selon qu'il existe ou non un point de terminaison de mise en miroir pour cette instance du serveur :  
  
-   Si le port d’écoute n’existe pas pour l’instance de serveur, le numéro de port 5022 s’affiche dans la zone de texte **Port** . Vous pouvez entrer n'importe quel numéro de port disponible, tel que 7022.  
  
-   Si le point de terminaison de mise en miroir existe déjà, son numéro de port est affiché. Pour modifier ce port, utilisez l'instruction ALTER ENDPOINT. Pour plus d’informations, consultez [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).  
  
    > [!NOTE]  
    >  Un numéro de port est obligatoire.  
  
 **Nom du point de terminaison**  
 Si le point de terminaison de mise en miroir existe pour cette instance du serveur, le nom du point de terminaison est affiché ici. Si le point de terminaison n'existe pas, vous pouvez spécifier son nom.  
  
 **Chiffrer les données envoyées via ce point de terminaison**  
 Par défaut, le chiffrement est activé. Lorsqu'il est activé, il devient obligatoire (et non simplement pris en charge) et il utilise les valeurs par défaut pour toutes les options de chiffrement. Pour plus d’informations, consultez [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).  
  
 Pour désactiver le chiffrement, désactivez la case à cocher. Pour réactiver le chiffrement, activez la case à cocher.  
  
## <a name="see-also"></a>Voir aussi  
 [Point de terminaison de mise en miroir de bases de données &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md)   
 [Propriétés de la base de données &#40;page Mise en miroir&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Créer un point de terminaison de mise en miroir de bases de données pour l’authentification Windows &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)   
 [Démarrer le moniteur de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Témoin de mise en miroir de base de données](database-mirroring-witness.md)  
  
  
