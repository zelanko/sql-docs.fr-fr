---
title: "Revendications au Service d’émission de jeton Windows (c2WTS) et Reporting Services | Documents Microsoft"
ms.custom: 
ms.date: 06/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- c2wts.exe.config
- SharePoint mode
- C2WTS
- WSS_WPG
ms.assetid: 4d380509-deed-4b4b-a9c1-a9134cc40641
caps.latest.revision: 17
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2ab5f4b5d2774d9dc944ad17bb55063388b70a6d
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Service d’émission de jetons Revendications vers Windows (C2WTS) et Reporting Services

[!INCLUDE[ssrs-appliesto-sql2016-xpreview](../../includes/ssrs-appliesto-sql2016-xpreview.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

  Le service d’émission de jetons Revendications SharePoint vers Windows (C2WTS) est nécessaire avec le mode SharePoint de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , si vous souhaitez utiliser l’authentification Windows pour les sources de données situées hors de la batterie de serveurs SharePoint. Ceci vaut même si l’utilisateur accède aux sources de données avec l’authentification Windows, car la communication entre le serveur web frontal (WFE) et le service partagé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] s’effectue toujours via l’Authentification de réclamations.  
  
 C2WTS est nécessaire même si votre ou vos sources de données résident sur le même ordinateur que le service partagé. Toutefois dans ce scénario, la délégation contrainte n'est pas nécessaire.  
  
 Les jetons créés par C2WTS ne fonctionnent qu’avec la délégation contrainte (pour certains services uniquement) et l’option de configuration « avec n’importe quel protocole d’authentification ». Comme indiqué précédemment, si vos sources de données sont sur le même ordinateur que le service partagé, la délégation contrainte n'est pas nécessaire.  
  
 Si votre environnement utilise la délégation contrainte Kerberos, le service SharePoint server et les sources de données externes doivent résider dans le même domaine Windows. Tout service qui s’appuie sur le service d’émission de jetons Revendications vers Windows (C2WTS) doit utiliser la délégation **contrainte** Kerberos pour permettre à C2WTS d’utiliser une transition de protocole Kerberos dans la conversion de revendications en informations d’identification Windows. Ces exigences s'appliquent à tous les services partagés SharePoint. Pour plus d’informations, consultez [Planifier l’authentification Kerberos dans SharePoint 2013](http://technet.microsoft.com/library/ee806870.aspx).  
  
 La procédure est résumée dans cette rubrique.

## <a name="prerequisites"></a>Conditions préalables

> [!NOTE]
>  Remarque : certaines étapes de configuration peuvent changer, ou peuvent ne pas fonctionner dans certaines topologies de batteries de serveurs. Par exemple, l’installation d’un serveur ne prend pas en charge les services C2WTS Windows Identity Foundation. C’est pourquoi les scénarios de délégation de jetons Windows ne sont pas possibles avec cette configuration de batterie de serveurs.

> [!IMPORTANT]
> Si vous utilisez Power View pour travailler sur des classeurs PowerPivot, vous devez effectuer une configuration supplémentaire (consultez [Vue d’ensemble d’Office Online Server](https://technet.microsoft.com/library/jj219437\(v=office.16\).aspx)). Pour plus d’informations, consultez les livres blancs suivants. 
>
> - [Déploiement de SQL Server 2016 PowerPivot et de Power View dans SharePoint 2016](../../analysis-services/instances/install-windows/deploying-sql-server-2016-powerpivot-and-power-view-in-sharepoint-2016.md)
> 
> - [Déploiement de SQL Server 2016 PowerPivot et de Power View dans une batterie de serveurs SharePoint 2016 à plusieurs niveaux](../../analysis-services/instances/install-windows/deploy-powerpivot-and-power-view-multi-tier-sharepoint-2016-farm.md)
  
### <a name="basic-steps-needed-to-configure-c2wts"></a>Étapes de base nécessaires pour configurer C2WTS  
  
1.  Configurez le compte de service C2WTS. Ajoutez le compte de service au groupe Administrateurs local sur chaque serveur d’applications exécutant C2WTS. De plus, vérifiez que le compte possède les droits de stratégie de sécurité locale suivants :  
  
    -   Agir en tant que partie du système d'exploitation  
  
    -   Emprunter l'identité d'un client après authentification  
  
    -   Ouvrir une session en tant que service  
  
2.  Configurez la délégation pour le compte de service C2WTS. Le compte a besoin de la délégation contrainte avec transition de protocole et d’autorisations de déléguer aux services avec lesquelles il doit communiquer (par exemple, SQL Server Engine, SQL Server Analysis Services). Pour configurer la délégation, vous pouvez utiliser le composant logiciel enfichable Utilisateurs et ordinateurs Active Directory.  

    > [!IMPORTANT]
    > Les paramètres que vous configurez pour le compte de service C2WTS, sous l’onglet Délégation, doivent correspondre au compte de service Reporting Services. Par exemple, si vous autorisez le compte de service C2WTS à déléguer à un service SQL, vous devez faire de même sur le compte de service Reporting Services.
  
    1.  Cliquez avec le bouton droit sur chaque compte de service et ouvrez la boîte de dialogue des propriétés. Dans la boîte de dialogue, cliquez sur l'onglet **Délégation** .  
  
        > [!NOTE]  
        >  Remarque : l’onglet Délégation est visible uniquement si l’objet a un SPN (Service Prinicpal Name) qui lui est affecté. c2WTS ne nécessite pas de SPN sur le compte c2WTS, mais sans SPN, l’onglet **Délégation** ne sera pas visible. Une autre façon de configurer la délégation contrainte consiste à utiliser un utilitaire tel que **ADSIEdit**.  
  
    2.  Les options de configuration principales dans l'onglet Délégation sont les suivantes :  
  
        -   Sélectionnez « N'approuver cet utilisateur que pour la délégation aux services spécifiés »  
  
        -   Sélectionnez « Utiliser tout protocole d'authentification »  

    3. Sélectionnez **Ajouter** pour ajouter un service auquel déléguer.
    
    4. Sélectionnez **utilisateurs ou ordinateurs...** * et entrez le compte qui héberge le service. Par exemple, si un serveur SQL Server s’exécute sous un compte nommé *sqlservice*, entrez `sqlservice`.
    
    5. Sélectionnez la liste des services. Les SPN disponibles sur ce compte s’affichent. Si vous ne voyez pas le service sur ce compte, il est peut-être manquant ou placé sur un autre compte. Vous pouvez utiliser l’utilitaire SetSPN pour ajuster les SPN.
    
    6. Cliquez sur OK pour fermer les boîtes de dialogue.
  
3.  Configurer les « appelants autorisés » dans C2WTS  
  
     C2WTS requiert que les identités des appelants soient explicitement répertoriées dans le fichier de configuration, **c2WTShost.exe.config**. C2WTS n’accepte pas les demandes de tous les utilisateurs authentifiés dans le système, sauf s’il est configuré pour cela. Dans ce cas l'appelant est le groupe Windows WSS_WPG. Le fichier c2wtshost.exe.confi est enregistré à l’emplacement suivant :  
     
     > [!NOTE]
     > La modification du compte de service dans l’Administration centrale de SharePoint, pour le service C2WTS, ajoute ce compte au groupe WSS_WPG.
  
     **\Program Files\Windows Identity Foundation\v3.5\c2WTShost.exe.config**  
  
     L'exemple suivant montre le fichier de configuration :  
  
    ```  
    <configuration>  
      <windowsTokenService>  
        <!--  
            By default no callers are allowed to use the Windows Identity Foundation Claims To NT Token Service.  
            Add the identities you wish to allow below.  
          -->  
        <allowedCallers>  
          <clear/>  
          <add value="WSS_WPG" />  
        </allowedCallers>  
      </windowsTokenService>  
    </configuration>  
    ```    
4.  Démarrer les revendications SharePoint vers Windows Token Service : Démarrez les revendications SharePoint vers Windows Token Service via l'Administration centrale de SharePoint sur la page **Gérer les ervices sur le serveur** . Le service doit être démarré sur le serveur qui effectuera l'action. Par exemple si vous avez un serveur Web frontal et un serveur d’applications exécutant le service partagé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , il vous suffit de démarrer C2WTS sur le serveur d’applications. C2WTS n’est pas nécessaire sur le serveur Web frontal.

## <a name="next-steps"></a>Étapes suivantes

[Vue d'ensemble du service d'émission de jetons Revendications vers Windows (c2WTS)](http://msdn.microsoft.com/library/ee517278.aspx)   
[Planifier l’authentification Kerberos dans SharePoint 2013](http://technet.microsoft.com/library/ee806870.aspx)  

D’autres questions ? [Essayez de poser le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
