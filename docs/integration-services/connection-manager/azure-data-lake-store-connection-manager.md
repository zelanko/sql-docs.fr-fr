---
title: "Gestionnaire de connexions Azure Data Lake Store | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SQL13.DTS.DESIGNER.AFPADLSCM.F1"
  - "sql14.dts.designer.afpadlscm.f1"
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Gestionnaire de connexions Azure Data Lake Store
  Le **gestionnaire de connexions Azure Data Lake Store** permet à un package SSIS de se connecter à un service Azure Data Lake Store par le biais de deux types d’authentification : Identité de l’utilisateur Azure AD et Identité du service Azure AD.  
  
 Le **gestionnaire de connexions Azure Data Lake Store** est un composant de SQL Server Integration Services (SSIS) Feature Pack pour Azure pour SQL Server 2016. Le Feature Pack est disponible en téléchargement [ici](http://go.microsoft.com/fwlink/?LinkID=626967).  

>   [!NOTE] Pour que le gestionnaire de connexions Azure Data Lake Store et les composants qui l’utilisent, notamment la source Azure Data Lake Store et la destination Azure Data Lake Store, puissent se connecter aux services, veillez à télécharger la dernière version du Feature Pack Azure [ici](https://www.microsoft.com/download/details.aspx?id=49492). 
 
## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Configurer le gestionnaire de connexions Azure Data Lake Store

 
1.  Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS**, sélectionnez **AzureDataLake**, puis cliquez sur **Ajouter**.  
  
2.  Dans la boîte de dialogue Éditeur du gestionnaire de connexions Azure Data Lake Store, tapez l’URL de l’hôte Azure Data Lake Store dans le champ **Hôte ADLS**. Par exemple : https://test.azuredatalakestore.net ou test.azuredatalakestore.net.
  
3.  Choisissez le type d’authentification correspondant pour accéder aux données Azure Data Lake Store.

    1.  Si vous avez sélectionné l’option d’authentification **Identité de l’utilisateur Azure AD**, procédez comme suit :
        1. Spécifiez des valeurs pour les champs **Nom d’utilisateur** et **Mot de passe**. 
    
        2. Cliquez sur le bouton **Tester la connexion** pour tester la connexion. Si vous et votre administrateur locataire n’avez pas déjà autorisé SSIS à accéder à vos données Azure Data Lake Store, vous devez cliquer sur le bouton **Accepter** pour autoriser SSIS à accéder à vos données Azure Data Lake Store dans la boîte de dialogue indépendante. Pour plus d’informations sur cette procédure de consentement, consultez [Intégration d’applications dans Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-integrating-applications#updating-an-application).
    
        >   [!NOTE] Pour l’option d’authentification Identité de l’utilisateur Azure AD, l’authentification multifacteur avec un compte Microsoft n’est PAS prise en charge.
    
    2. Si vous avez sélectionné l’option d’authentification **Identité du service Azure AD**, procédez comme suit :
        1. Créez une application AAD et un principal du service qui peuvent accéder aux ressources Azure Data Lake.
    
        2. Affectez à cette application AAD les autorisations correspondantes pour accéder à vos ressources Azure Data Lake. Pour plus d’informations sur cette option d’authentification, consultez [Utiliser le portail pour créer une application Active Directory et un principal du service qui peuvent accéder aux ressources](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal).
    
        3. Spécifiez des valeurs pour les champs **ID client**, **Clé secrète** et **Nom du locataire**.
    
        4. Cliquez sur le bouton **Tester la connexion** pour tester la connexion.  
  
6.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
    Les propriétés du gestionnaire de connexions que vous avez créées apparaissent dans la fenêtre **Propriétés** .  
  
  