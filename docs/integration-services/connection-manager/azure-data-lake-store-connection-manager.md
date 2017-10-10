---
title: Gestionnaire de connexions Azure Data Lake Store | Documents Microsoft
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: douglasl
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSCM.F1
- sql14.dts.designer.afpadlscm.f1
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
caps.latest.revision: 7
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 5acf2de3fccc2f5180358f87bd02591811c59c72
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="azure-data-lake-store-connection-manager"></a>Gestionnaire de connexions Azure Data Lake Store
Un package de SQL Server Integration Services (SSIS) peut utiliser le Gestionnaire de connexions Azure Data Lake Store pour se connecter à un service Azure Data Lake Store avec l’un des deux types d’authentification suivants :
-   Identité d’utilisateur Azure AD
-   Identité de Service Azure AD 

Le Gestionnaire de connexions Azure Data Lake Store est un composant de la [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

>   [!NOTE]
> Pour que le gestionnaire de connexions Azure Data Lake Store et les composants qui l’utilisent, notamment la source Azure Data Lake Store et la destination Azure Data Lake Store, puissent se connecter aux services, veillez à télécharger la dernière version du Feature Pack Azure [ici](https://www.microsoft.com/download/details.aspx?id=49492). 
 
## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Configurer le gestionnaire de connexions Azure Data Lake Store

1.  Dans le **ajouter un gestionnaire de connexions SSIS** boîte de dialogue, sélectionnez **AzureDataLake**, puis sélectionnez **ajouter**. Le **éditeur de gestionnaire de connexions Azure données Lake Store** boîte de dialogue s’ouvre.
  
2.  Dans le **éditeur de gestionnaire de connexions Azure données Lake Store** boîte de dialogue le **ADLS hôte** champ, fournissez l’URL de l’hôte Azure Data Lake Store. Par exemple : `https://test.azuredatalakestore.net` ou `test.azuredatalakestore.net`.
  
3.  Dans le **authentification** champ, choisissez le type d’authentification approprié pour accéder aux données dans Azure Data Lake Store.

    1.  Si vous sélectionnez le **utilisateurs Azure AD Identity** authentification option, procédez comme suit :
        1. Fournir des valeurs pour le **nom d’utilisateur** et **mot de passe** champs. 
    
        2. Pour tester la connexion, sélectionnez **tester la connexion**. Si vous ou l’administrateur du client n’a pas été précédemment consentement permettant de SSIS pour accéder à vos données Azure Data Lake Store, sélectionnez **accepter** lorsque vous y êtes invité. Pour plus d’informations sur cette procédure de consentement, consultez [Intégration d’applications dans Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-integrating-applications#updating-an-application).
    
        >   [!NOTE] 
        > Lorsque vous sélectionnez le **utilisateurs Azure AD Identity** option d’authentification, l’authentification multifacteur et l’authentification de compte Microsoft ne sont pas pris en charge.
    
    2. Si vous sélectionnez le **identité de Service Azure AD** authentification option, procédez comme suit :
        1. Créez une application Azure Active Directory (AAD) et le service principal pour accéder aux données Azure Data Lake.
    
        2. Attribuez les autorisations appropriées pour permettre cette application AAD à accéder à vos ressources Azure Data Lake. Pour plus d’informations sur cette option d’authentification, consultez [Utiliser le portail pour créer une application Active Directory et un principal du service qui peuvent accéder aux ressources](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal).
    
        3. Fournir des valeurs pour le **Id Client**, **clé secrète**, et **nom_client** champs.
    
        4. Pour tester la connexion, sélectionnez **tester la connexion**.  
  
6.  Sélectionnez **OK** pour fermer la **éditeur de gestionnaire de connexions Azure données Lake Store** boîte de dialogue.  
  
Les propriétés du gestionnaire de connexions que vous avez créées apparaissent dans la fenêtre **Propriétés** .  
  
  
