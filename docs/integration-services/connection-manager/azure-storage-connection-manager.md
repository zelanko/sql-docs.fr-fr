---
title: Gestionnaire de connexions du Stockage Azure | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpstorageconn.f1
- sql14.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
author: janinezhang
ms.author: janinez
ms.openlocfilehash: f171499471f8f94ad970446d31cf796f4ab55fb7
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028769"
---
# <a name="azure-storage-connection-manager"></a>Gestionnaire de connexions Azure Storage

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

  **Azure Storage Connection Manager** permet à un package SSIS de se connecter à un compte Stockage Azure.
   
 Le **gestionnaire de connexions du stockage Azure** est un composant de [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md). 
  
Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS** , sélectionnez **AzureStorage**, puis cliquez sur **Ajouter**.  
  
Les propriétés suivantes sont disponibles.

- **Service :** spécifie le service de stockage auquel se connecter.
- **Account name (Nom du compte) :** spécifie le nom du compte de stockage.
- **Authentication (Authentification) :** spécifie la méthode d’authentification à utiliser. Les authentifications **AccessKey** et **ServicePrincipal** sont prises en charge.
    - **AccessKey :** pour cette méthode d’authentification, spécifiez la **clé de compte**.
    - **ServicePrincipal :** pour cette méthode d’authentification, spécifiez l’**ID d’application**, la **clé d’application** et l’**ID de locataire** du principal du service.
      Pour que la **connexion de test** fonctionne, le principal de service doit disposer au moins du rôle **Lecteur des données Blob du stockage** pour le compte de stockage.
      Pour plus d’informations, consultez [cette page](https://docs.microsoft.com/azure/storage/common/storage-auth-aad-rbac-portal#assign-rbac-roles-using-the-azure-portal).
- **Environment :** spécifie l’environnement de cloud qui héberge le compte de stockage.

## <a name="managed-identities-for-azure-resources-authentication"></a>Identités managées pour l’authentification des ressources Azure
Lors de l’exécution de packages SSIS sur le [runtime d’intégration Azure-SSIS dans Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime), vous pouvez utiliser l’[identité managée](https://docs.microsoft.com/azure/data-factory/connector-azure-sql-database#managed-identity) associée à votre fabrique de données pour l’authentification du stockage Azure. La fabrique en question peut accéder à votre compte de stockage et copier des données depuis ou vers celle-ci à l’aide de cette identité.

Pour plus d’informations sur l’authentification de Stockage Azure en général, consultez [Authentifier l’accès à Stockage Azure à l’aide d’Azure Active Directory](https://docs.microsoft.com/azure/storage/common/storage-auth-aad). Pour utiliser l’authentification d’identité managée pour le stockage Azure, suivez ces étapes afin de configurer votre compte de stockage :

1. **[Recherchez l’identité managée de la fabrique de données à partir du portail Azure](https://docs.microsoft.com/azure/data-factory/data-factory-service-identity)** . Accédez aux **Propriétés** de votre fabrique de données. Copiez l’**ID d’application de l’identité managée** (pas l’**ID d’objet de l’identité managée**).

1. **Accordez l’autorisation appropriée à l’identité managée dans votre compte de stockage**. Pour plus d’informations sur les rôles, consultez [Gérer les droits d’accès aux données de Stockage Azure avec RBAC](https://docs.microsoft.com/azure/storage/common/storage-auth-aad-rbac-portal).

    - **En tant que source**, dans le contrôle d’accès (IAM), accordez au moins le rôle **Lecteur des données Blob du stockage**.
    - **En tant que destination**, dans le contrôle d’accès (IAM), accordez au moins le rôle **Contributeur aux données Blob du stockage**.

Ensuite, **configurez l’authentification d’identité managée** pour le gestionnaire de connexions de stockage Azure. Pour ce faire, vous disposez de deux options.

1. Effectuez la configuration au moment du design. Dans le concepteur SSIS, double-cliquez sur le gestionnaire de connexions de stockage Azure pour ouvrir l’**Éditeur du gestionnaire de connexions du stockage Azure** et cochez la case **Utiliser l’identité managée pour s’authentifier sur Azure**.
    > [!NOTE]
    >  Actuellement, cette option NE prend PAS effet (indiquant que l’authentification d’identité managée ne fonctionne pas) quand vous exécutez le package SSIS dans le concepteur SSIS ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server.
    
1. Effectuez la configuration au moment de l’exécution. Quand vous exécutez le package par le biais de [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/integration-services/ssis-quickstart-run-ssms) ou de l’[activité Exécuter le package SSIS d’Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity), recherchez le gestionnaire de connexions de stockage Azure et affectez la valeur **True** à sa propriété **ConnectUsingManagedIdentity**.
    > [!NOTE]
    >  Dans le runtime d’intégration Azure-SSIS, toutes les autres méthodes d’authentification (par exemple clé d’accès et principal du service) préconfigurées sur le gestionnaire de connexions de stockage Azure sont **remplacées** quand l’authentification d’identité managée est utilisée pour des opérations de stockage.

> [!NOTE]
>  Pour configurer l’authentification d’identité managée sur des packages existants, il est préférable de regénérer le projet SSIS avec le [dernier concepteur SSIS](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) au moins une fois, et de redéployer ce projet SSIS sur votre runtime d’intégration Azure-SSIS afin que la nouvelle propriété de gestionnaire de connexions **ConnectUsingManagedIdentity** soit automatiquement ajoutée à tous les gestionnaires de connexions de stockage Azure dans votre projet SSIS. L’autre méthode consiste à utiliser directement la substitution de propriété avec le chemin de propriété **\Package.Connections[{nom de votre gestionnaire de connexions}].Properties[ConnectUsingManagedIdentity]** au moment de l’exécution.

## <a name="see-also"></a>Voir aussi  
 [Connexions Integration Services &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)
