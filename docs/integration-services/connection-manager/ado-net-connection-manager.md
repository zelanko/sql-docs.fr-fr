---
title: Gestionnaire de connexions ADO.NET | Microsoft Docs
description: Un gestionnaire de connexions ADO.NET permet à un package d’accéder à des sources de données à l’aide d’un fournisseur .NET.
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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d3cf4e302df6e28d898a2790d928cf40085f7915
ms.sourcegitcommit: 7183735e38dd94aa3b9bab2b73ccab54c916ff86
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74687276"
---
# <a name="adonet-connection-manager"></a>Gestionnaire de connexions ADO.NET

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] permet à un package d'accéder à des sources de données à l'aide d'un fournisseur .NET. En général, vous utilisez ce gestionnaire de connexions pour accéder à des sources de données telles que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez également accéder à des sources de données exposées via OLE DB et XML dans des tâches personnalisées écrites en code managé dans un langage comme C#.  
  
Lorsque vous ajoutez un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] à un package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui sera résolu en connexion [!INCLUDE[vstecado](../../includes/vstecado-md.md)] au moment de l’exécution. Il définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection **Connections** du package.  
  
La propriété `ConnectionManagerType` du gestionnaire de connexions a pour valeur `ADO.NET`. La valeur de `ConnectionManagerType` est qualifiée de façon à inclure le nom du fournisseur .NET utilisé par le gestionnaire de connexions.  
  
## <a name="adonet-connection-manager-troubleshooting"></a>Résolution des problèmes liés au gestionnaire de connexions ADO.NET  
Vous pouvez consigner les appels que le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] effectue vers les fournisseurs de données externes. Vous pouvez alors résoudre les problèmes liés aux connexions établies par le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] avec des sources de données externes. Pour journaliser les appels faits par le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] aux fournisseurs de données externes, activez la journalisation des packages et sélectionnez l’événement **Diagnostic** au niveau du package. Pour plus d’informations, consultez [Outils de dépannage pour l’exécution des packages](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
Quand elles sont lues par un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)], les données de certains types de données de date [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génèrent les résultats présentés dans le tableau ci-après.  
  
|Type de données SQL Server|Résultats|  
|--------------------------|------------|  
|**time**, **datetimeoffset**|Le package échoue s'il n'utilise pas de commandes SQL paramétrables. Pour utiliser des commandes SQL paramétrables, utilisez la tâche d'exécution SQL dans votre package. Pour plus d’informations, consultez [Tâche d’exécution de requêtes SQL](../../integration-services/control-flow/execute-sql-task.md) et [Paramètres et codes de retour dans la tâche d’exécution SQL](https://msdn.microsoft.com/library/a3ca65e8-65cf-4272-9a81-765a706b8663).|  
|**datetime2**|Le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] tronque les millisecondes.|  
  
> [!NOTE]  
>  Pour plus d’informations sur les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et leur mappage aux types de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md) et [Types de données d’Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="adonet-connection-manager-configuration"></a>Configuration du gestionnaire de connexions ADO.NET  
  
Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
-   Fournissez une chaîne de connexion spécifique configurée de façon à satisfaire les exigences du fournisseur .NET sélectionné.  
  
-   Selon le fournisseur, incluez le nom de la source de données à laquelle se connecter.  
  
-   Fournissez les informations d'identification de sécurité nécessaires selon le fournisseur sélectionné.  
  
-   Indiquez si la connexion créée à partir du gestionnaire de connexions est conservée au moment de l’exécution.  
  
De nombreuses options de configuration du gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] dépendent du fournisseur .NET utilisé par le gestionnaire de connexions.  
  
Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], consultez [Configurer le gestionnaire de connexions ADO.NET](../../integration-services/connection-manager/configure-ado-net-connection-manager.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
### <a name="configure-adonet-connection-manager"></a>Configurer le gestionnaire de connexions ADO.NET
Utilisez la boîte de dialogue **Configurer le gestionnaire de connexions ADO.NET** pour ajouter une connexion à une source de données accessible à l’aide d’un fournisseur de données .NET Framework. Par exemple, un tel fournisseur est le fournisseur SqlClient. Le gestionnaire de connexions peut utiliser une connexion existante, ou vous pouvez en créer une nouvelle.  
  
 Pour en savoir plus sur le gestionnaire de connexions ADO.NET, consultez [ADO.NET Connection Manager](../../integration-services/connection-manager/ado-net-connection-manager.md).  
  
#### <a name="options"></a>Options  
**Connexions de données**  
Sélectionnez une connexion de données ADO.NET existante dans la liste.  
  
**Propriétés des connexions de données**  
Indique les propriétés et les valeurs pour la connexion de données ADO.NET sélectionnée.  
  
**Nouveau**  
Permet de créer une connexion de données ADO.NET via la boîte de dialogue **Gestionnaire de connexions** .  
  
**Supprimer**  
Sélectionnez une connexion, puis supprimez-la en sélectionnant **Supprimer**.  
  
#### <a name="managed-identities-for-azure-resources-authentication"></a>Identités managées pour l’authentification des ressources Azure
Lors de l’exécution de packages SSIS sur le [runtime d’intégration Azure-SSIS dans Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime), vous pouvez utiliser l’[identité managée](https://docs.microsoft.com/azure/data-factory/connector-azure-sql-database#managed-identity) associée à votre fabrique de données pour l’authentification Azure SQL Database (ou de l’instance gérée). La fabrique en question peut accéder à votre base de données et copier des données depuis ou vers celle-ci à l’aide de cette identité.

> [!NOTE]
>  Quand vous utilisez l’authentification Azure Active Directory (Azure AD), y compris l’authentification d’identité managée, pour vous connecter à Azure SQL Database (ou à l’instance managée), vous pouvez rencontrer un problème lié à un échec d’exécution de package ou à un changement de comportement inattendu. Pour plus d’informations, consultez [Fonctionnalités et limitations d’Azure AD](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication#azure-ad-features-and-limitations).

Pour utiliser l’authentification d’identité managée pour Azure SQL Database, suivez ces étapes afin de configurer votre base de données :

1. [Provisionnez un administrateur Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#provision-an-azure-active-directory-administrator-for-your-azure-sql-database-server) pour votre serveur Azure SQL sur le portail Azure, si ce n’est pas déjà fait. L’administrateur Azure AD peut être un utilisateur Azure AD ou un groupe Azure AD. Si vous accordez au groupe détenant l’identité managée un rôle d’administrateur, ignorez les étapes 2 et 3. L’administrateur a un accès complet à la base de données.

1. [Créer des utilisateurs de base de données autonome](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#create-contained-database-users-in-your-database-mapped-to-azure-ad-identities) pour l’identité managée de Data Factory. Connectez-vous à la base de données depuis ou vers laquelle vous souhaitez copier des données à l’aide d’outils tels que SSMS, avec une identité Azure AD qui a au moins l’autorisation ALTER ANY USER. Exécutez la commande T-SQL suivante : 
    
    ```sql
    CREATE USER [your data factory name] FROM EXTERNAL PROVIDER;
    ```

1. Accordez les autorisations requises par l’identité managée Data Factory comme vous le feriez d’habitude pour des utilisateurs SQL et autres. Pour connaître les rôles appropriés, consultez [Rôles au niveau de la base de données](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles). Exécutez le code suivant. Pour plus d’options, consultez [ce document](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql).

    ```sql
    EXEC sp_addrolemember [role name], [your data factory name];
    ```

Pour utiliser l’authentification d’identité managée pour l’instance managée Azure SQL Database, effectuez les étapes suivantes afin de configurer votre base de données :
    
1. [Provisionnez un administrateur Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#provision-an-azure-active-directory-administrator-for-your-managed-instance) pour votre instance managée sur le portail Azure, si ce n’est pas déjà fait. L’administrateur Azure AD peut être un utilisateur Azure AD ou un groupe Azure AD. Si vous accordez au groupe détenant l’identité managée un rôle d’administrateur, ignorez les étapes 2 à 4. L’administrateur a un accès complet à la base de données.

1. [Créez des connexions](https://docs.microsoft.com/sql/t-sql/statements/create-login-transact-sql?view=azuresqldb-mi-current) pour le l’identité managée Data Factory. Dans SQL Server Management Studio (SSMS), connectez-vous à votre instance managée à l’aide d’un compte SQL Server qui est un **sysadmin**. Dans la base de données de **référence**, exécutez le code T-SQL suivant :

    ```sql
    CREATE LOGIN [your data factory name] FROM EXTERNAL PROVIDER;
    ```

1. [Créer des utilisateurs de base de données autonome](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#create-contained-database-users-in-your-database-mapped-to-azure-ad-identities) pour l’identité managée de Data Factory. Connectez-vous à la base de données à partir de laquelle ou vers laquelle vous souhaitez copier des données, puis exécutez la commande T-SQL suivante : 
  
    ```sql
    CREATE USER [your data factory name] FROM EXTERNAL PROVIDER;
    ```

1. Accordez les autorisations requises par l’identité managée Data Factory comme vous le feriez d’habitude pour des utilisateurs SQL et autres. Exécutez le code suivant. Pour plus d’options, consultez [ce document](https://docs.microsoft.com/sql/t-sql/statements/alter-role-transact-sql?view=azuresqldb-mi-current).

    ```sql
    ALTER ROLE [role name e.g., db_owner] ADD MEMBER [your data factory name];
    ```

Enfin, configurez l’authentification d’identité managée pour le gestionnaire de connexions ADO.NET. Les options disponibles sont les suivantes :
    
- **Configurez au moment de la conception.** Dans le concepteur SSIS, cliquez avec le bouton droit sur le gestionnaire de connexions ADO.NET et sélectionnez **Propriétés**. Mettez à jour la propriété `ConnectUsingManagedIdentity` en spécifiant `True`.
    > [!NOTE]
    >  La propriété du gestionnaire de connexions `ConnectUsingManagedIdentity` ne prend pas effet (ce qui indique que l’authentification d’identité managée ne fonctionne pas) quand vous exécutez le package SSIS dans le concepteur SSIS ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server.
    
- **Configurez au moment de l’exécution.** Quand vous exécutez le package via [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/integration-services/ssis-quickstart-run-ssms) ou l’[activité d’exécution d’un package SSIS dans Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity), recherchez le gestionnaire de connexions ADO.NET. Mettez à jour sa propriété `ConnectUsingManagedIdentity` en spécifiant `True`.
    > [!NOTE]
    >  Dans le runtime d’intégration Azure-SSIS, toutes les autres méthodes d’authentification (par exemple, l’authentification intégrée et le mot de passe) préconfigurées sur le gestionnaire de connexions ADO.NET sont remplacées quand l’authentification d’identité managée est utilisée pour établir la connexion d’une base de données.

> [!NOTE]
>  Pour configurer l’authentification d’identité managée sur les packages existants, la méthode privilégiée consiste à regénérer au moins une fois votre projet SSIS avec le [dernier concepteur SSIS](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt). Redéployez ce projet SSIS sur votre runtime d’intégration Azure-SSIS, afin que la nouvelle propriété du gestionnaire de connexions `ConnectUsingManagedIdentity` soit ajoutée automatiquement à tous les gestionnaires de connexions ADO.NET dans votre projet SSIS. L’autre méthode consiste à utiliser directement une substitution de propriété avec le chemin de propriété **\Package.Connections[{nom de votre gestionnaire de connexions}].Properties[ConnectUsingManagedIdentity]** au moment de l’exécution.

## <a name="see-also"></a>Voir aussi  
 [Connexions Integration Services &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
