---
title: Gestionnaire de connexions ADO.NET | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.adonetconnection.f1
helpviewer_keywords:
- connection managers [Integration Services], ADO.NET
- ADO.NET connection manager [Integration Services]
- connections [Integration Services], ADO.NET
ms.assetid: fc5daa2f-0159-4bda-9402-c87f1035a96f
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 32b01cce82cd1fd2af018b002a3c551ea480c000
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67897987"
---
# <a name="adonet-connection-manager"></a>Gestionnaire de connexions ADO.NET

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] permet à un package d'accéder à des sources de données à l'aide d'un fournisseur .NET. Le gestionnaire de connexions est généralement utilisé pour accéder à des sources de données comme [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ainsi qu’à des sources de données exposées via OLE DB et XML dans des tâches personnalisées écrites en code managé dans un langage comme C#.  
  
 Quand vous ajoutez un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] à un package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions résolu en une connexion [!INCLUDE[vstecado](../../includes/vstecado-md.md)] au moment de l’exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection **Connexions** sur le package.  
  
 La propriété **ConnectionManagerType** du gestionnaire de connexions est définie sur **ADO.NET**. La valeur de **ConnectionManagerType** est qualifiée de façon à inclure le nom du fournisseur .NET utilisé par le gestionnaire de connexions.  
  
## <a name="adonet-connection-manager-troubleshooting"></a>Résolution des problèmes liés au gestionnaire de connexions ADO.NET  
 Vous pouvez consigner les appels que le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] effectue vers les fournisseurs de données externes. Vous pouvez utiliser cette fonctionnalité de journalisation pour résoudre les problèmes liés aux connexions établies par le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] avec des sources de données externes. Pour consigner les appels faits par le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] aux fournisseurs de données externes, activez la journalisation des packages et sélectionnez l’événement **Diagnostic** au niveau du package. Pour plus d’informations, consultez [Outils de dépannage pour l’exécution des packages](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
 Quand elles sont lues par un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] , les données de certains types de données date de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génèrent les résultats présentés dans le tableau ci-après.  
  
|Type de données SQL Server|Résultats|  
|--------------------------|------------|  
|**time**, **datetimeoffset**|Le package échoue s'il n'utilise pas de commandes SQL paramétrables. Pour utiliser des commandes SQL paramétrables, utilisez la tâche d'exécution SQL dans votre package. Pour plus d’informations, consultez [Tâche d’exécution de requêtes SQL](../../integration-services/control-flow/execute-sql-task.md) et [Paramètres et codes de retour dans la tâche d’exécution SQL](https://msdn.microsoft.com/library/a3ca65e8-65cf-4272-9a81-765a706b8663).|  
|**datetime2**|Le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] tronque les millisecondes.|  
  
> [!NOTE]  
>  Pour plus d’informations sur les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et leur mappage aux types de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md) et [Types de données d’Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="adonet-connection-manager-configuration"></a>Configuration du gestionnaire de connexions ADO.NET  
 Vous pouvez configurer un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] de plusieurs façons :  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
-   Fournissez une chaîne de connexion spécifique configurée de façon à satisfaire les exigences du fournisseur .NET sélectionné.  
  
-   Selon le fournisseur, incluez le nom de la source de données à laquelle se connecter.  
  
-   Fournissez les informations d'identification de sécurité nécessaires selon le fournisseur sélectionné.  
  
-   Indiquez si la connexion créée à partir du gestionnaire de connexions est conservée au moment de l'exécution.  
  
 De nombreuses options de configuration du gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] dépendent du fournisseur .NET utilisé par le gestionnaire de connexions.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur une des rubriques suivantes :  
  
-   [Configurer le gestionnaire de connexions ADO.NET](../../integration-services/connection-manager/configure-ado-net-connection-manager.md)  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="configure-adonet-connection-manager"></a>Configurer le gestionnaire de connexions ADO.NET
  Utilisez la boîte de dialogue **Configurer le gestionnaire de connexions ADO.NET** pour ajouter une connexion à une source de données accessible à l'aide d'un fournisseur de données .NET Framework, tel que le fournisseur SqlClient. Le gestionnaire de connexions peut utiliser une connexion existante, ou vous pouvez en créer une nouvelle.  
  
 Pour en savoir plus sur le gestionnaire de connexions ADO.NET, consultez [ADO.NET Connection Manager](../../integration-services/connection-manager/ado-net-connection-manager.md).  
  
### <a name="options"></a>Options  
 **Connexions de données**  
 Sélectionnez une connexion de données ADO.NET existante dans la liste.  
  
 **Propriétés des connexions de données**  
 Indique les propriétés et les valeurs pour la connexion de données ADO.NET sélectionnée.  
  
 **Nouveau**  
 Permet de créer une connexion de données ADO.NET via la boîte de dialogue **Gestionnaire de connexions** .  
  
 **Supprimer**  
 Sélectionnez une connexion, puis supprimez-la à l’aide du bouton **Supprimer** .  
  
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

Enfin, **configurez l’authentification d’identité managée** pour le gestionnaire de connexions ADO.NET. Pour ce faire, vous disposez de deux options.
    
1. Effectuez la configuration au moment du design. Dans le concepteur SSIS, cliquez avec le bouton droit sur le gestionnaire de connexions ADO.NET et cliquez sur **Propriétés** pour ouvrir la **fenêtre Propriétés**. Définissez la propriété **ConnectUsingManagedIdentity** sur **True**.
    > [!NOTE]
    >  La propriété du gestionnaire de connexions **ConnectUsingManagedIdentity** NE prend PAS effet (indiquant que l’authentification d’identité managée ne fonctionne pas) quand vous exécutez le package SSIS dans le concepteur SSIS ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server.
    
1. Effectuez la configuration au moment de l’exécution. Quand vous exécutez le package par le biais de [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/integration-services/ssis-quickstart-run-ssms) ou de l’[activité Exécuter le package SSIS d’Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity), recherchez le gestionnaire de connexions ADO.NET et définissez sa propriété **ConnectUsingManagedIdentity** sur **True**.
    > [!NOTE]
    >  Dans le runtime d’intégration Azure-SSIS, toutes les autres méthodes d’authentification (par exemple, authentification intégrée, mot de passe) préconfigurées sur le gestionnaire de connexions ADO.NET sont **remplacées** quand l’authentification d’identité managée est utilisée pour établir la connexion de base de données.

> [!NOTE]
>  Pour configurer l’authentification d’identité managée sur les packages existants, regénérez votre projet SSIS avec le [dernier concepteur SSIS](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) au moins une fois et redéployez ce projet SSIS sur votre runtime d’intégration Azure-SSIS afin que la nouvelle propriété de gestionnaire de connexions **ConnectUsingManagedIdentity** soit automatiquement ajoutée à tous les gestionnaires de connexions ADO.NET dans votre projet SSIS.

## <a name="see-also"></a>Voir aussi  
 [Connexions Integration Services &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
