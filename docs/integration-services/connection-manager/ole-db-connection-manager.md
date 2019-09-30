---
title: Gestionnaire de connexions OLE DB | Microsoft Docs
description: Un gestionnaire de connexions OLE DB permet à un package de se connecter à une source de données à l'aide d'un fournisseur OLE DB.
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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ffc7da76c7291bbf8e0d4dd6003c572cd9610e92
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71294383"
---
# <a name="ole-db-connection-manager"></a>Gestionnaire de connexions OLE DB

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Un gestionnaire de connexions OLE DB permet à un package de se connecter à une source de données à l'aide d'un fournisseur OLE DB. Par exemple, un gestionnaire de connexions OLE DB qui se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut utiliser le fournisseur [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].    
    
> [!NOTE]
>  Le fournisseur OLEDB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 ne prend pas en charge les mots clés de la nouvelle chaîne de connexion (MultiSubnetFailover=True) pour le clustering de basculement de sous-réseaux multiples. Pour plus d’informations, consultez les [Notes de publication pour SQL Server](https://go.microsoft.com/fwlink/?LinkId=247824).    
> 
> [!NOTE]
>  Si la source de données est [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007 ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 2007, elle requiert un fournisseur de données différent des versions antérieures d’Excel ou d’Access. Pour plus d’informations, consultez [Établir une connexion à un classeur Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md) et [Établir une connexion à une base de données Access](../../integration-services/connection-manager/connect-to-an-access-database.md).    
    
Plusieurs tâches et composants de flux de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilisent un gestionnaire de connexions OLE DB. Par exemple, la source OLE DB et la destination OLE DB utilisent ce gestionnaire de connexions pour extraire et charger des données. La tâche d’exécution de requêtes SQL peut utiliser ce gestionnaire de connexions pour se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin d’exécuter des requêtes.    
    
Vous pouvez également utiliser le gestionnaire de connexions OLE DB pour accéder à des sources de données OLE DB dans des tâches personnalisées écrites dans du code non géré qui utilise un langage comme C++.    
    
Quand vous ajoutez un gestionnaire de connexions OLE DB à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui est résolu en une connexion OLE DB au moment de l’exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection **Connections** sur le package.    
    
La propriété `ConnectionManagerType` du gestionnaire de connexions a pour valeur `OLEDB`.    
    
Configurez le gestionnaire de connexions OLE DB de plusieurs manières :    
    
-   Indiquez une chaîne de connexion spécifique configurée pour répondre aux besoins du fournisseur sélectionné.    
    
-   Selon le fournisseur, incluez le nom de la source de données à laquelle se connecter.    
    
-   Fournissez les informations d'identification de sécurité nécessaires selon le fournisseur sélectionné.    
    
-   Indiquez si la connexion créée à partir du gestionnaire de connexions est conservée au moment de l’exécution.    
    
## <a name="log-calls-and-troubleshoot-connections"></a>Consigner les appels et résoudre les problèmes de connexion    
 Vous pouvez consigner les appels que le gestionnaire de connexions OLE DB effectue vers des fournisseurs de données externes. Vous pouvez alors résoudre les problèmes liés aux connexions établies par le gestionnaire de connexions OLE DB avec des sources de données externes. Pour consigner les appels que le gestionnaire de connexions OLE DB effectue vers des fournisseurs de données externes, activez la journalisation des packages et sélectionnez l’événement **Diagnostic** au niveau du package. Pour plus d’informations, consultez [Outils de dépannage pour l’exécution des packages](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).    
    
## <a name="configure-the-ole-db-connection-manager"></a>Configurer le gestionnaire de connexions OLE DB    
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation. Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Configurer le gestionnaire de connexions OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md). Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez la documentation de la classe **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** dans le Guide du développeur.    
    
### <a name="configure-ole-db-connection-manager"></a>Configurer le gestionnaire de connexions OLE DB

Utilisez la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB** pour ajouter une connexion à une source de données. Cette connexion peut être nouvelle ou une copie d’une connexion existante.  
  
> [!NOTE]  
>  Si la source de données est [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007, la source de données requiert un gestionnaire de connexions différent des versions antérieures d'Excel. Pour plus d’informations, consultez [Établir une connexion à un classeur Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md).  
>   
>  Si la source de données est [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 2007, la source de données requiert un fournisseur OLE DB différent des versions antérieures d’Access. Pour plus d’informations, consultez [Établir une connexion à une base de données Access](../../integration-services/connection-manager/connect-to-an-access-database.md).  
  
 Pour en savoir plus sur le gestionnaire de connexions OLE DB, consultez [Gestionnaire de connexions OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
#### <a name="options"></a>Options  
 **Connexions de données**  
 Sélectionnez une connexion de données OLE DB existante dans la liste.  
  
 **Propriétés des connexions de données**  
 Permet d'afficher les propriétés et les valeurs relatives à la connexion de données OLE DB sélectionnée.  
  
 **Nouveau**  
 Créez une connexion de données OLE DB à l’aide de la boîte de dialogue **Gestionnaire de connexions** .  
  
 **Supprimer**  
 Sélectionnez une connexion de données, puis supprimez-la en sélectionnant **Supprimer**.  
  
#### <a name="managed-identities-for-azure-resources-authentication"></a>Identités managées pour l’authentification des ressources Azure
Lors de l’exécution de packages SSIS sur le [runtime d’intégration Azure-SSIS dans Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime), utilisez l’[identité managée](https://docs.microsoft.com/azure/data-factory/connector-azure-sql-database#managed-identity) associée à votre fabrique de données pour l’authentification Azure SQL Database (ou de l’instance gérée). La fabrique en question peut accéder à votre base de données et copier des données depuis ou vers celle-ci à l’aide de cette identité.

> [!NOTE]
>  Quand vous utilisez l’authentification Azure Active Directory (Azure AD), y compris l’authentification d’identité managée, pour vous connecter à Azure SQL Database (ou à l’instance managée), vous pouvez rencontrer un problème lié à un échec d’exécution de package ou à un changement de comportement inattendu. Pour plus d’informations, consultez [Fonctionnalités et limitations d’Azure AD](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication#azure-ad-features-and-limitations).

Pour utiliser l’authentification d’identité managée pour Azure SQL Database, suivez ces étapes afin de configurer votre base de données :

1. Créez un groupe dans Azure AD. Faites de l’identité managée un membre du groupe.
    
   1. [Recherchez l’identité managée de la fabrique de données à partir du portail Azure](https://docs.microsoft.com/azure/data-factory/data-factory-service-identity). Accédez aux **Propriétés** de votre fabrique de données. Copiez l’**ID objet de l’identité managée**.
    
   1. Installez le module [Azure AD PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2). Connectez-vous à l’aide de la commande `Connect-AzureAD`. Exécutez les commandes suivantes pour créer un groupe et ajouter l’identité managée en tant que membre.
      ```powershell
      $Group = New-AzureADGroup -DisplayName "<your group name>" -MailEnabled $false -SecurityEnabled $true -MailNickName "NotSet"
      Add-AzureAdGroupMember -ObjectId $Group.ObjectId -RefObjectId "<your data factory managed identity object ID>"
      ```
    
1. [Provisionnez un administrateur Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#provision-an-azure-active-directory-administrator-for-your-azure-sql-database-server) pour votre serveur Azure SQL sur le portail Azure, si ce n’est pas déjà fait. L’administrateur Azure AD peut être un utilisateur Azure AD ou un groupe Azure AD. Si vous accordez au groupe détenant l’identité managée un rôle d’administrateur, ignorez les étapes 3 et 4. L’administrateur a un accès complet à la base de données.

1. [Créez des utilisateurs de base de données autonome](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#create-contained-database-users-in-your-database-mapped-to-azure-ad-identities) pour le groupe Azure AD. Connectez-vous à la base de données depuis ou vers laquelle vous souhaitez copier des données à l’aide d’outils tels que SSMS, avec une identité Azure AD qui a au moins l’autorisation ALTER ANY USER. Exécutez la commande T-SQL suivante : 
    
    ```sql
    CREATE USER [your AAD group name] FROM EXTERNAL PROVIDER;
    ```

1. Accordez au groupe Azure AD les autorisations requises, comme vous le faites habituellement pour les utilisateurs SQL et autres. Pour connaître les rôles appropriés, consultez [Rôles au niveau de la base de données](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles). Par exemple, exécutez le code suivant :

    ```sql
    ALTER ROLE [role name] ADD MEMBER [your AAD group name];
    ```

Pour utiliser l’authentification d’identité managée pour l’instance managée Azure SQL Database, effectuez les étapes suivantes afin de configurer votre base de données :
    
1. [Provisionnez un administrateur Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#provision-an-azure-active-directory-administrator-for-your-managed-instance) pour votre instance managée sur le portail Azure, si ce n’est pas déjà fait. L’administrateur Azure AD peut être un utilisateur Azure AD ou un groupe Azure AD. Si vous accordez au groupe détenant l’identité managée un rôle d’administrateur, ignorez les étapes 2 à 5. L’administrateur a un accès complet à la base de données.

1. [Recherchez l’identité managée de la fabrique de données à partir du portail Azure](https://docs.microsoft.com/azure/data-factory/data-factory-service-identity). Accédez aux **Propriétés** de votre fabrique de données. Copiez l’**ID d’application de l’identité managée** (et non pas l’**ID d’objet de l’identité managée**).

1. Convertissez l’identité managée de la fabrique de données en type binaire. Connectez-vous à la base de données **master** dans votre instance managée à l’aide d’outils tels que SSMS, avec votre compte d’administrateur SQL ou Active Directory. Exécutez la commande T-SQL suivante sur la base de données **master** pour obtenir votre ID d’application de l’identité managée sous forme binaire :
    
    ```sql
    DECLARE @applicationId uniqueidentifier = '{your managed identity application ID}'
    select CAST(@applicationId AS varbinary)
    ```

1. Ajoutez l’identité managée de la fabrique de données en tant qu’utilisateur dans l’instance managée Azure SQL Database. Exécutez la commande T-SQL suivante sur la base de données **MASTER** :
    
    ```sql
    CREATE LOGIN [{a name for the managed identity}] FROM EXTERNAL PROVIDER with SID = {your managed identity application ID as binary}, TYPE = E
    ```

1. Octroyez à l’identité managée de la fabrique de données les autorisations requises. Pour connaître les rôles appropriés, consultez [Rôles au niveau de la base de données](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles). Exécutez la commande T-SQL suivante sur la base de données depuis ou vers laquelle vous souhaitez copier des données :

    ```sql
    CREATE USER [{the managed identity name}] FOR LOGIN [{the managed identity name}] WITH DEFAULT_SCHEMA = dbo
    ALTER ROLE [role name] ADD MEMBER [{the managed identity name}]
    ```

Ensuite, configurez le fournisseur OLE DB pour le gestionnaire de connexions OLE DB. Les options disponibles sont les suivantes :
    
- **Configurez au moment de la conception.** Dans le concepteur SSIS, double-cliquez sur le gestionnaire de connexions OLE DB pour ouvrir la fenêtre **Gestionnaire de connexions**. Dans la liste déroulante **Fournisseur**, sélectionnez [**Microsoft OLE DB Driver pour SQL Server**](https://go.microsoft.com/fwlink/?linkid=871294).
    > [!NOTE]
    >  Il est possible que les autres fournisseurs dans la liste déroulante ne prennent pas en charge l’authentification d’identité managée.
    
- **Configurez au moment de l’exécution.** Quand vous exécutez le package via [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/integration-services/ssis-quickstart-run-ssms) ou l’[activité d’exécution d’un package SSIS dans Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity), recherchez la propriété de gestionnaire de connexions **ConnectionString** pour le gestionnaire de connexions OLE DB. Mettez à jour la propriété de connexion `Provider` en spécifiant `MSOLEDBSQL` (autrement dit, Microsoft OLE DB Driver pour SQL Server).
    ```vb
    Data Source=serverName;Initial Catalog=databaseName;Provider=MSOLEDBSQL;...
    ```

Enfin, configurez l’authentification d’identité managée pour le gestionnaire de connexions OLE DB. Les options disponibles sont les suivantes :
    
- **Configurez au moment de la conception.** Dans le concepteur SSIS, cliquez avec le bouton droit sur le gestionnaire de connexions OLE DB et sélectionnez **Propriétés**. Mettez à jour la propriété `ConnectUsingManagedIdentity` en spécifiant `True`.
    > [!NOTE]
    >  La propriété du gestionnaire de connexions `ConnectUsingManagedIdentity` ne prend pas effet (ce qui indique que l’authentification d’identité managée ne fonctionne pas) quand vous exécutez le package SSIS dans le concepteur SSIS ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server.

- **Configurez au moment de l’exécution.** Quand vous exécutez le package via SSMS ou une activité **Exécuter le package SQL**, recherchez le gestionnaire de connexions OLE DB et mettez à jour sa propriété `ConnectUsingManagedIdentity` en spécifiant `True`.
    > [!NOTE]
    >  Dans le runtime d’intégration Azure-SSIS, toutes les autres méthodes d’authentification (par exemple, la sécurité intégrée et le mot de passe) préconfigurées sur le gestionnaire de connexions OLE DB sont remplacées quand l’authentification d’identité managée est utilisée pour établir la connexion d’une base de données.

> [!NOTE]
>  Pour configurer l’authentification d’identité managée sur les packages existants, la méthode privilégiée consiste à regénérer au moins une fois votre projet SSIS avec le [dernier concepteur SSIS](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt). Redéployez ce projet SSIS sur votre runtime d’intégration Azure-SSIS, afin que la nouvelle propriété du gestionnaire de connexions `ConnectUsingManagedIdentity` soit ajoutée automatiquement à tous les gestionnaires de connexions OLE DB dans votre projet SSIS. L’autre méthode consiste à utiliser directement une substitution de propriété avec le chemin de propriété **\Package.Connections[{nom de votre gestionnaire de connexions}].Properties[ConnectUsingManagedIdentity]** au moment de l’exécution.

## <a name="see-also"></a>Voir aussi    
 [Source OLE DB](../../integration-services/data-flow/ole-db-source.md)     
 [Destination OLE DB](../../integration-services/data-flow/ole-db-destination.md)     
 [Tache d'exécution de requêtes SQL](../../integration-services/control-flow/execute-sql-task.md)     
 [Connexions Integration Services &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)    
    
  
