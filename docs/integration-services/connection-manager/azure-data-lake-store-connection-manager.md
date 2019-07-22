---
title: Gestionnaire de connexions Azure Data Lake Store | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: maghan
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSCM.F1
- sql14.dts.designer.afpadlscm.f1
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
author: Lingxi-Li
ms.author: lingxl
ms.openlocfilehash: 095865071b3a9ddfcba15635d9e3d857b2dbee20
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67904793"
---
# <a name="azure-data-lake-store-connection-manager"></a>Gestionnaire de connexions Azure Data Lake Store

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Un package SQL Server Integration Services (SSIS) peut utiliser le gestionnaire de connexions Azure Data Lake Store pour se connecter à un compte Azure Data Lake Storage Gen1 avec un des deux types d’authentification suivants :
-   Identité de l’utilisateur Azure AD
-   Identité du service Azure AD 

Le gestionnaire de connexions Azure Data Lake Store est un composant de [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

> [!NOTE]
> Pour que le gestionnaire de connexions Azure Data Lake Store et les composants qui l’utilisent, c’est-à-dire la source Data Lake Storage Gen1 et la destination Azure Data Lake Store Gen1, puissent se connecter aux services, veillez à télécharger la dernière version du Feature Pack Azure [ici](https://www.microsoft.com/download/details.aspx?id=49492). 
 
## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Configurer le gestionnaire de connexions Azure Data Lake Store

1.  Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS**, sélectionnez **AzureDataLake**, puis **Ajouter**. La boîte de dialogue **Éditeur du gestionnaire de connexions Azure Data Lake Store** s’affiche.
  
2.  Dans la boîte de dialogue **Éditeur du gestionnaire de connexions Azure Data Lake Store**, dans le champ **Hôte ADLS**, spécifiez l’URL de l’hôte Azure Data Lake Storage Gen1. Par exemple, `https://test.azuredatalakestore.net` ou `test.azuredatalakestore.net`.
  
3.  Dans le champ **Authentification**, choisissez le type d’authentification adapté pour accéder aux données dans Data Lake Storage Gen1.

    1.  Si vous sélectionnez l’option d’authentification **Identité de l’utilisateur Azure AD**, effectuez les étapes suivantes :
        1. Renseignez les champs **Nom d’utilisateur** et **Mot de passe**. 
    
        2. Sélectionnez **Tester la connexion** pour tester la connexion. Si l’administrateur du locataire ou vous-même n’avez pas préalablement autorisé SSIS à accéder à vos données Data Lake Storage Gen1, sélectionnez **Accepter** quand vous y êtes invité. Pour plus d’informations sur cette procédure de consentement, consultez [Intégration d’applications dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/manage-apps/plan-an-application-integration#integrating-applications-with-azure-ad).
    
        > [!NOTE] 
        > Lorsque vous sélectionnez l’option d’authentification **Identité de l’utilisateur Azure AD**, l’authentification multifacteur et l’authentification de compte Microsoft ne sont pas prises en charge.
    
    2. Si vous sélectionnez l’option d’authentification **Identité du service Azure AD**, effectuez les étapes suivantes :
        1. Créez une application et un principal du service Azure Active Directory (AAD) pour accéder aux données Data Lake Storage Gen1.
    
        2. Affectez les autorisations appropriées pour permettre à cette application AAD d’accéder à vos ressources Data Lake Storage Gen1. Pour plus d’informations sur cette option d’authentification, consultez [Utiliser le portail pour créer une application Active Directory et un principal du service qui peuvent accéder aux ressources](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).
    
        3. Renseignez les champs **ID client**, **Clé secrète** et **Nom du locataire**.
    
        4. Sélectionnez **Tester la connexion** pour tester la connexion.  
  
6.  Sélectionnez **OK** pour fermer la boîte de dialogue **Éditeur du gestionnaire de connexions Azure Data Lake Store**.  

## <a name="view-the-properties-of-the-connection-manager"></a>Afficher les propriétés du gestionnaire de connexions
Les propriétés du gestionnaire de connexions que vous avez créées apparaissent dans la fenêtre **Propriétés** .  
  
  
