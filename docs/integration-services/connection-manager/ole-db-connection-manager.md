---
title: Gestionnaire de connexions OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.oledbconnection.f1
helpviewer_keywords:
- OLE DB connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], OLE DB
- connections [Integration Services], OLE DB
ms.assetid: 91e3622e-4b1a-439a-80c7-a00b90d66979
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c455e449ff59296848c7e3f15d07aaee80d415c7
ms.sourcegitcommit: e92ce0f59345fe61c0dd3bfe495ef4b1de469d4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2019
ms.locfileid: "66221155"
---
# <a name="ole-db-connection-manager"></a>Gestionnaire de connexions OLE DB

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Un gestionnaire de connexions OLE DB permet à un package de se connecter à une source de données à l'aide d'un fournisseur OLE DB. Par exemple, un gestionnaire de connexions OLE DB qui se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut utiliser le fournisseur [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].    
    
> [!NOTE]
>  Le fournisseur OLEDB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 ne prend pas en charge les mots clés de la nouvelle chaîne de connexion (MultiSubnetFailover=True) pour le clustering de basculement de sous-réseaux multiples. Pour plus d’informations, consultez les [Notes de publication de SQL Server](https://go.microsoft.com/fwlink/?LinkId=247824) et la publication de blog [Basculement de sous-réseaux multiples Always On et SSIS](https://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/)sur www.mattmasson.com.    
> 
> [!NOTE]
>  Si la source de données est [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007 ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 2007, elle requiert un fournisseur de données différent des versions antérieures d’Excel ou d’Access. Pour plus d’informations, consultez [Établir une connexion à un classeur Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md) et [Établir une connexion à une base de données Access](../../integration-services/connection-manager/connect-to-an-access-database.md).    
    
 Plusieurs tâches et composants de flux de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilisent un gestionnaire de connexions OLE DB. Ainsi, la source et la destination OLE DB utilisent ce gestionnaire de connexions pour extraire et charger des données, tandis que la tâche d’exécution SQL utilise ce gestionnaire pour se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin d’exécuter des requêtes.    
    
 Le gestionnaire de connexions OLE DB est également utilisé pour accéder à des sources de données OLE DB dans des tâches personnalisées écrites dans du code non géré utilisant un langage comme C++.    
    
 Quand vous ajoutez un gestionnaire de connexions OLE DB à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui sera résolu en une connexion OLE DB au moment de l’exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection **Connections** sur le package.    
    
 La propriété **ConnectionManagerType** du gestionnaire de connexions a pour valeur **OLEDB**.    
    
 Le gestionnaire de connexions OLE DB peut être configuré de plusieurs manières :    
    
-   Indiquez une chaîne de connexion spécifique configurée pour répondre aux besoins du fournisseur sélectionné.    
    
-   Selon le fournisseur, incluez le nom de la source de données à laquelle se connecter.    
    
-   Fournissez les informations d'identification de sécurité nécessaires selon le fournisseur sélectionné.    
    
-   Indiquez si la connexion créée à partir du gestionnaire de connexions est conservée au moment de l'exécution.    
    
## <a name="logging"></a>Journalisation    
 Vous pouvez consigner les appels que le gestionnaire de connexions OLE DB effectue vers des fournisseurs de données externes. Cette fonctionnalité de journalisation permet de résoudre des problèmes liés aux connexions que le gestionnaire de connexions OLE DB établit avec des sources de données externes. Pour consigner les appels que le gestionnaire de connexions OLE DB effectue vers des fournisseurs de données externes, activez la journalisation de package et sélectionnez l’événement **Diagnostic** au niveau du package. Pour plus d’informations, consultez [Outils de dépannage pour l’exécution des packages](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).    
    
## <a name="configuration-of-the-oledb-connection-manager"></a>Configuration du gestionnaire de connexions OLEDB    
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation. Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Configurer le gestionnaire de connexions OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md). Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez la documentation de la classe **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** dans le Guide du développeur.    
    
## <a name="related-content"></a>Contenu associé    
    
-   Article Wiki, [SSIS with Oracle Connectors](https://go.microsoft.com/fwlink/?LinkId=220670) (SSIS avec connecteurs Oracle) sur social.technet.microsoft.com.    
    
-   Article technique, [Connection Strings for OLE DB Providers](https://go.microsoft.com/fwlink/?LinkId=220744)(Chaînes de connexion pour les fournisseurs OLE DB), sur carlprothman.net.    
    
## <a name="configure-ole-db-connection-manager"></a>Configurer le gestionnaire de connexions OLE DB
  La boîte de dialogue **Configurer le gestionnaire de connexions OLE DB** vous permet d’ajouter une connexion à une source de données, qui peut être une nouvelle connexion ou la copie d’une connexion existante.  
  
> [!NOTE]  
>  Si la source de données est [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007, la source de données requiert un gestionnaire de connexions différent des versions antérieures d'Excel. Pour plus d’informations, consultez [Établir une connexion à un classeur Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md).  
>   
>  Si la source de données est [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 2007, la source de données requiert un fournisseur OLE DB différent des versions antérieures d’Access. Pour plus d’informations, consultez [Établir une connexion à une base de données Access](../../integration-services/connection-manager/connect-to-an-access-database.md).  
  
 Pour en savoir plus sur le gestionnaire de connexions OLE DB, consultez [Gestionnaire de connexions OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
### <a name="options"></a>Options  
 **Connexions de données**  
 Sélectionnez une connexion de données OLE DB existante dans la liste.  
  
 **Propriétés des connexions de données**  
 Permet d'afficher les propriétés et les valeurs relatives à la connexion de données OLE DB sélectionnée.  
  
 **Nouveau**  
 Créez une connexion de données OLE DB à l’aide de la boîte de dialogue **Gestionnaire de connexions** .  
  
 **Supprimer**  
 Sélectionnez une connexion de données, puis supprimez-la à l’aide du bouton **Supprimer** .  
  
### <a name="managed-identities-for-azure-resources-authentication"></a>Identités managées pour l’authentification des ressources Azure
Lors de l’exécution de packages SSIS sur le [runtime d’intégration Azure-SSIS dans Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime), vous pouvez utiliser l’[identité managée](https://docs.microsoft.com/azure/data-factory/connector-azure-sql-database#managed-identity) associée à votre fabrique de données pour l’authentification Azure SQL Database (ou Managed Instance). La fabrique en question peut accéder à votre base de données et copier des données depuis ou vers celle-ci à l’aide de cette identité.

Pour utiliser l’authentification d’identité managée pour Azure SQL Database, suivez ces étapes afin de configurer votre base de données :

1. **Créez un groupe dans Azure AD.** Faites de l’identité managée un membre du groupe.
    
   1. [Recherchez l’identité managée de la fabrique de données à partir du portail Azure](https://docs.microsoft.com/azure/data-factory/data-factory-service-identity). Accédez aux **Propriétés** de votre fabrique de données. Copiez l’**ID objet de l’identité managée**.
    
   1. Installez le module [Azure AD PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2). Connectez-vous à l’aide de la commande `Connect-AzureAD`. Exécutez les commandes suivantes pour créer un groupe et ajouter l’identité managée en tant que membre.
      ```powershell
      $Group = New-AzureADGroup -DisplayName "<your group name>" -MailEnabled $false -SecurityEnabled $true -MailNickName "NotSet"
      Add-AzureAdGroupMember -ObjectId $Group.ObjectId -RefObjectId "<your data factory managed identity object ID>"
      ```
    
1. **[Provisionnez un administrateur Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#provision-an-azure-active-directory-administrator-for-your-azure-sql-database-server)** pour votre serveur SQL Azure sur le portail Azure si ce n’est déjà fait. L’administrateur Azure AD peut être un utilisateur Azure AD ou un groupe Azure AD. Si vous accordez au groupe détenant l’identité managée un rôle d’administrateur, ignorez les étapes 3 et 4. L’administrateur a un accès complet à la base de données.

1. **[Créez des utilisateurs de base de données autonome](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#create-contained-database-users-in-your-database-mapped-to-azure-ad-identities)** pour le groupe Azure AD. Connectez-vous à la base de données depuis ou vers laquelle vous souhaitez copier des données à l’aide d’outils tels que SSMS, avec une identité Azure AD qui a au moins l’autorisation ALTER ANY USER. Exécutez la commande T-SQL suivante : 
    
    ```sql
    CREATE USER [your AAD group name] FROM EXTERNAL PROVIDER;
    ```

1. **Accordez au groupe Azure AD les autorisations requises** comme vous le feriez, entre autres, pour des utilisateurs SQL. Par exemple, exécutez le code suivant :

    ```sql
    ALTER ROLE [role name] ADD MEMBER [your AAD group name];
    ```

Pour utiliser l’authentification par identité managée pour Azure SQL Database Managed Instance, suivez ces étapes afin de configurer votre base de données :
    
1. **[Provisionnez un administrateur Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#provision-an-azure-active-directory-administrator-for-your-managed-instance)** pour votre instance managée sur le portail Azure si ce n’est déjà fait. L’administrateur Azure AD peut être un utilisateur Azure AD ou un groupe Azure AD. Si vous accordez au groupe détenant l’identité managée un rôle d’administrateur, ignorez les étapes 2 à 5. L’administrateur a un accès complet à la base de données.

1. **[Recherchez l’identité managée de la fabrique de données à partir du portail Azure](https://docs.microsoft.com/azure/data-factory/data-factory-service-identity)** . Accédez aux **Propriétés** de votre fabrique de données. Copiez l’**ID d’application de l’identité managée** (pas l’**ID d’objet de l’identité managée**).

1. **Convertissez l’identité managée de la fabrique de données en type binaire**. Connectez-vous à la base de données **MASTER** dans votre instance managée à l’aide d’outils tels que SSMS, avec votre compte d’administrateur SQL/Active Directory. Exécutez la commande T-SQL suivante sur la base de données **MASTER** pour obtenir votre ID d’application de l’identité managée sous forme binaire :
    
    ```sql
    DECLARE @applicationId uniqueidentifier = '{your managed identity application ID}'
    select CAST(@applicationId AS varbinary)
    ```

1. **Ajoutez l’identité managée de la fabrique de données en tant qu’utilisateur** dans Azure SQL Database Managed Instance. Exécutez la commande T-SQL suivante sur la base de données **MASTER** :
    
    ```sql
    CREATE LOGIN [{a name for the managed identity}] FROM EXTERNAL PROVIDER with SID = {your managed identity application ID as binary}, TYPE = E
    ```

1. **Octroyez à l’identité managée de la fabrique de données les autorisations requises**. Exécutez la commande T-SQL suivante sur la base de données depuis ou vers laquelle vous souhaitez copier des données :

    ```sql
    CREATE USER [{the managed identity name}] FOR LOGIN [{the managed identity name}] WITH DEFAULT_SCHEMA = dbo
    ALTER ROLE db_owner ADD MEMBER [{the managed identity name}]
    ```

Ensuite, **configurez le fournisseur OLE DB** pour le gestionnaire de connexions OLE DB. Pour ce faire, vous disposez de deux options.
    
1. Effectuez la configuration au moment du design. Dans le concepteur SSIS, double-cliquez sur le gestionnaire de connexions OLE DB pour ouvrir la fenêtre **Gestionnaire de connexions**. Dans la liste déroulante **Fournisseur**, sélectionnez [**Microsoft OLE DB Driver pour SQL Server**](https://go.microsoft.com/fwlink/?linkid=871294).
    > [!NOTE]
    >  Il est possible que les autres fournisseurs dans la liste déroulante ne prennent pas en charge l’authentification d’identité managée.
    
1. Effectuez la configuration au moment de l’exécution. Quand vous exécutez le package par le biais de [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/integration-services/ssis-quickstart-run-ssms) ou de l’[activité Exécuter le package SSIS d’Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity), recherchez la propriété de gestionnaire de connexions **ConnectionString** pour le gestionnaire de connexions OLE DB et définissez la propriété de connexion **Fournisseur** sur **MSOLEDBSQL** (autrement dit, Microsoft OLE DB Driver pour SQL Server).
    ```vb
    Data Source=serverName;Initial Catalog=databaseName;Provider=MSOLEDBSQL;...
    ```

Enfin, **configurez l’authentification d’identité managée** pour le gestionnaire de connexions OLE DB. Pour ce faire, vous disposez de deux options.
    
1. Effectuez la configuration au moment du design. Dans le concepteur SSIS, cliquez avec le bouton droit sur le gestionnaire de connexions OLE DB et cliquez sur **Propriétés** pour ouvrir la **fenêtre Propriétés**. Définissez la propriété **ConnectUsingManagedIdentity** sur **True**.
    > [!NOTE]
    >  La propriété du gestionnaire de connexions **ConnectUsingManagedIdentity** NE prend PAS effet (indiquant que l’authentification d’identité managée ne fonctionne pas) quand vous exécutez le package SSIS dans le concepteur SSIS ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server.

1. Effectuez la configuration au moment de l’exécution. Quand vous exécutez le package par le biais de SSMS ou de l’activité Exécuter le package SQL, recherchez le gestionnaire de connexions OLE DB et définissez sa propriété **ConnectUsingManagedIdentity** sur **True**.
    > [!NOTE]
    >  Dans le runtime d’intégration Azure-SSIS, toutes les autres méthodes d’authentification (par exemple, sécurité intégrée, mot de passe) préconfigurées sur le gestionnaire de connexions OLE DB sont **remplacées** quand l’authentification d’identité managée est utilisée pour établir la connexion de base de données.

> [!NOTE]
>  Pour configurer l’authentification d’identité managée sur les packages existants, regénérez votre projet SSIS avec le [dernier concepteur SSIS](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) au moins une fois et redéployez ce projet SSIS sur votre runtime d’intégration Azure-SSIS afin que la nouvelle propriété de gestionnaire de connexions **ConnectUsingManagedIdentity** soit automatiquement ajoutée à tous les gestionnaires de connexions OLE DB dans votre projet SSIS.

## <a name="see-also"></a>Voir aussi    
 [Source OLE DB](../../integration-services/data-flow/ole-db-source.md)     
 [Destination OLE DB](../../integration-services/data-flow/ole-db-destination.md)     
 [Tache d'exécution de requêtes SQL](../../integration-services/control-flow/execute-sql-task.md)     
 [Connexions Integration Services &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)    
    
  
