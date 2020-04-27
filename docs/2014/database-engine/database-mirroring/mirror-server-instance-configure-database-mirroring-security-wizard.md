---
title: Instance de serveur miroir (Configurer l’Assistant Sécurité de mise en miroir de bases de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.mirrorsrvr.f1
ms.assetid: 53223432-615e-440f-904d-925d33ec2144
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 83a92633a4c466e72c8cc2de0cc1c220e88e01bb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62755167"
---
# <a name="mirror-server-instance-configure-database-mirroring-security-wizard"></a>Instance de serveur miroir (Configurer l'Assistant Sécurité de mise en miroir de bases de données)
  Cette page vous permet de spécifier des informations sur l'instance de serveur avec la base de données miroir.  
  
> [!IMPORTANT]  
>  L'instance de serveur miroir doit exécuter la même édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](Standard ou Entreprise) que l'instance de serveur principal. En outre, nous vous conseillons vivement d'exécuter les instances sur des systèmes comparables pouvant gérer des charges de travail identiques.  
  
 **Pour configurer la mise en miroir de bases de données à l'aide de SQL Server Management Studio**  
  
-   [Établir une session de mise en miroir de bases de données au moyen de l’authentification Windows &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Démarrer l’Assistant Configuration de la sécurité de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Options  
 **Instance de serveur miroir**  
 Si une instance de serveur miroir est déjà spécifiée (dans la page **Mise en miroir** de la boîte de dialogue **Propriétés de la base de données** ), cette instance est affichée. Pour plus d’informations, consultez [Propriétés de la base de données &#40;page Mise en miroir&#41;](../../relational-databases/databases/database-properties-mirroring-page.md).  
  
 Dans le cas contraire, entrez le nom de l'instance de serveur miroir. Notez que l'instance de serveur miroir ne peut pas être identique à l'instance de serveur principal.  
  
 **Connexion**  
 Si aucune instance de serveur miroir n’a été spécifiée, cliquez sur **Se connecter** pour afficher la boîte de dialogue **Se connecter au serveur** , dans laquelle vous pouvez spécifier l’instance de serveur et établir une connexion.  
  
 Si l’instance a été spécifiée, mais que l’Assistant ne propose pas de connexion doté d’autorisations suffisantes pour vérifier l’existence du point de terminaison, cliquez sur **Se connecter**. Dans la boîte de dialogue **Se connecter au serveur** qui s’affiche, l’instance de serveur est présélectionnée et ne peut pas être modifiée. Spécifiez un compte de domaine qui possède une autorisation suffisante et connectez-vous à l'instance du serveur.  
  
> [!NOTE]  
>  Au moment de se connecter à l’instance du serveur, l’Assistant de configuration de la sécurité de mise en miroir de bases de données utilise les informations d’identification fournies dans la boîte de dialogue **Se connecter au serveur** . Celles-ci diffèrent des informations d'identification d'une session de mise en miroir, qui utilise les informations d'identification du compte de démarrage où l'instance de serveur est en cours d'exécution en tant que service.  
  
 **Port de l’écouteur**  
 Le comportement de cette option varie comme suit selon qu'il existe ou non un point de terminaison de mise en miroir pour cette instance du serveur :  
  
-   Si aucun port d’écoute n’existe pour l’instance de serveur, le numéro de port 5022 est affiché dans la zone de texte **Port** . Vous pouvez utiliser n'importe quel numéro de port disponible, tel que 7022.  
  
-   Lorsque le point de terminaison de mise en miroir existe déjà, le numéro de port issu de ce point de terminaison est affiché. Si vous devez modifier le port, utilisez une commande ALTER ENDPOINT. Pour plus d’informations, consultez [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).  
  
    > [!NOTE]  
    >  Un numéro de port est obligatoire.  
  
 **Nom du point de terminaison**  
 Si le point de terminaison de mise en miroir existe pour cette instance du serveur, le nom du point de terminaison est affiché ici. Si le point de terminaison n'existe pas, vous pouvez spécifier son nom.  
  
 **Chiffrer les données envoyées via ce point de terminaison**  
 Par défaut, le chiffrement est activé. Lorsqu'il est activé, il devient obligatoire (et non simplement pris en charge) et il utilise les valeurs par défaut pour toutes les options de chiffrement. Pour plus d’informations, consultez [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).  
  
 Pour désactiver le chiffrement, désactivez la case à cocher. Pour réactiver le chiffrement, activez la case à cocher.  
  
## <a name="see-also"></a>Voir aussi  
 [Le point de terminaison de mise en miroir de bases de données &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md)   
 [Propriétés de la base de données &#40;page mise en miroir&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Créer un point de terminaison de mise en miroir de bases de données pour l’authentification Windows &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)   
 [Démarrer Moniteur de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)  
  
  
