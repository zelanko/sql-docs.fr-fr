---
title: Créer le catalogue SSIS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6ed56d36-18d9-40c2-b51f-f2a4c71d1e73
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f8db507966f9b3323e415ca7f2abfe4a12601c1c
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798020"
---
# <a name="create-the-ssis-catalog"></a>Créer le catalogue SSIS
  Après avoir conçu et testé des packages dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], vous pouvez déployer les projets qui contiennent les packages sur un serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Avant de pouvoir déployer des projets sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], celui-ci doit contenir le catalogue `SSISDB`. Le programme d'installation de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] ne crée pas automatiquement le catalogue ; vous devez le créer manuellement à l'aide des instructions suivantes.  
  
 Vous pouvez créer le catalogue SSISDB dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Vous pouvez également créer le catalogue par programmation en utilisant Windows PowerShell.  
  
### <a name="to-create-the-ssisdb-catalog-in-sql-server-management-studio"></a>Pour créer le catalogue SSISDB dans SQL Server Management Studio  
  
1.  Ouvrir [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Connectez-vous au moteur de base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
3.  Dans l’Explorateur d’objets, développez le nœud du serveur, cliquez avec le bouton droit sur le nœud **Catalogues Integration Services** , puis cliquez sur **Créer un catalogue**.  
  
4.  Cliquez sur **Activer l'intégration du CLR**.  
  
     Le catalogue utilise des procédures stockées du CLR.  
  
5.  Cliquez sur **Activer l’exécution automatique des procédures stockées Integration Services au démarrage de SQL Server** pour permettre à la procédure stockée [catalog.startup](/sql/integration-services/system-stored-procedures/catalog-startup) de s’exécuter à chaque redémarrage de l’instance de serveur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
     La procédure stockée effectue la maintenance de l'état des opérations pour le catalogue SSISDB. Elle résout l'état de tous les packages en cours d'exécution si et quand l'instance de serveur [!INCLUDE[ssIS](../includes/ssis-md.md)] s'arrête.  
  
6.  Entrez un mot de passe, puis cliquez sur **OK**.  
  
     Le mot de passe protège la clé principale de la base de données utilisée pour le chiffrement des données du catalogue. Enregistrez le mot de passe dans un emplacement sécurisé. Il est également recommandé de sauvegarder la clé principale de base de données. Pour plus d’informations, voir [Sauvegarder une clé primaire de base de données](../relational-databases/security/encryption/back-up-a-database-master-key.md).  
  
### <a name="to-create-the-ssisdb-catalog-programmatically"></a>Pour créer le catalogue SSISDB par programmation  
  
1.  Exécutez le script PowerShell suivant :  
  
    ```powershell
    # Load the IntegrationServices Assembly  
    [Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Management.IntegrationServices")  
  
    # Store the IntegrationServices Assembly namespace to avoid typing it every time  
    $ISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"  
  
    Write-Host "Connecting to server ..."  
  
    # Create a connection to the server  
    $sqlConnectionString = "Data Source=localhost;Initial Catalog=master;Integrated Security=SSPI;"  
    $sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString  
  
    # Create the Integration Services object  
    $integrationServices = New-Object $ISNamespace".IntegrationServices" $sqlConnection  
  
    # Provision a new SSIS Catalog  
    $catalog = New-Object $ISNamespace".Catalog" ($integrationServices, "SSISDB", "P@assword1")  
    $catalog.Create()
    ```  
  
     Vous trouverez d’autres exemples d’utilisation de Windows PowerShell et de l’espace de noms <xref:Microsoft.SqlServer.Management.IntegrationServices> dans l’entrée de blog [SSIS et PowerShell dans SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=242539), sur blogs.msdn.com. Pour obtenir une vue d'ensemble de l'espace de noms et des exemples de code, consultez l'entrée de blog, [A Glimpse of the SSIS Catalog Managed Object Model](https://go.microsoft.com/fwlink/?LinkId=254267), sur blogs.msdn.com.  
  
## <a name="see-also"></a>Voir aussi  
 [Catalogue SSIS](catalog/ssis-catalog.md)   
 [Sauvegarder, restaurer et déplacer le catalogue SSIS](../../2014/integration-services/backup-restore-and-move-the-ssis-catalog.md)  
