---
title: Revendications au Service d’émission de jeton Windows (C2WTS) et Reporting Services | Documents Microsoft
ms.custom: ''
ms.date: 03/25/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- c2wts.exe.config
- SharePoint mode
- C2WTS
- WSS_WPG
ms.assetid: 4d380509-deed-4b4b-a9c1-a9134cc40641
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 479be89681f7c34558c5a7e89d54023feb110d60
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041300"
---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Service d'émission de jetons Revendications vers Windows (C2WTS) et Reporting Services
  Les revendications SharePoint vers Windows Token Service (c2WTS) est requises avec [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mode SharePoint si vous souhaitez utiliser l’authentification windows pour les Sources de données qui sont en dehors de la batterie de serveurs SharePoint. Ceci s'applique même si les utilisateurs accèdent aux sources de données à l'aide de l'authentification Windows, car la communication entre le serveur Web frontal (WFE) et le service partagé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] se fera toujours via l'authentification basée sur les revendications.  
  
 C2WTS est nécessaire même si votre ou vos sources de données résident sur le même ordinateur que le service partagé. Toutefois dans ce scénario, la délégation contrainte n'est pas nécessaire.  
  
 Les jetons créés par C2WTS ne fonctionnent qu’avec la délégation contrainte (pour certains services uniquement) et l’option de configuration « avec n’importe quel protocole d’authentification ». Comme indiqué précédemment, si vos sources de données sont sur le même ordinateur que le service partagé, la délégation contrainte n'est pas nécessaire.  
  
 Si votre environnement utilise la délégation contrainte Kerberos, le service SharePoint server et les sources de données externes doivent résider dans le même domaine Windows. Tout service qui s’appuie sur le service d’émission de jetons Revendications vers Windows (C2WTS) doit utiliser la délégation **contrainte** Kerberos pour permettre à C2WTS d’utiliser une transition de protocole Kerberos dans la conversion de revendications en informations d’identification Windows. Ces exigences s'appliquent à tous les services partagés SharePoint. Pour plus d’informations, consultez [vue d’ensemble de l’authentification Kerberos pour les produits Microsoft SharePoint 2010 (http://technet.microsoft.com/library/gg502594.aspx)](http://technet.microsoft.com/library/gg502594.aspx).  
  
 La procédure est résumée dans cette rubrique.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010|  
  
## <a name="prerequisites"></a>Prérequis  
  
> [!NOTE]  
>  Remarque : certaines étapes de configuration peuvent changer, ou peuvent ne pas fonctionner dans certaines topologies de batteries de serveurs. Par exemple, l’installation d’un serveur ne prend pas en charge les services C2WTS Windows Identity Foundation. C’est pourquoi les scénarios de délégation de jetons Windows ne sont pas possibles avec cette configuration de batterie de serveurs.  
  
### <a name="basic-steps-needed-to-configure-c2wts"></a>Étapes de base nécessaires pour configurer C2WTS  
  
1.  Configurez le compte de service C2WTS. Ajoutez le compte de service au groupe Administrateurs local sur chaque serveur d’applications exécutant C2WTS. De plus, vérifiez que le compte possède les droits de stratégie de sécurité locale suivants :  
  
    -   Agir en tant que partie du système d'exploitation  
  
    -   Emprunter l'identité d'un client après authentification  
  
    -   Ouvrir une session en tant que service  
  
     Également, le compte que vous utilisez pour c2WTS doit être configuré pour la délégation contrainte avec transition de protocole et a besoin d’autorisations de déléguer aux Services qu’il est nécessaire pour communiquer avec (autrement dit, SQL Server Engine, SQL Server Analysis Services). Pour configurer la délégation, vous pouvez utiliser le composant logiciel enfichable utilisateurs Active Directory et l’ordinateur.  
  
    1.  Cliquez avec le bouton droit sur chaque compte de service et ouvrez la boîte de dialogue des propriétés. Dans la boîte de dialogue, cliquez sur l'onglet **Délégation** .  
  
        > [!NOTE]  
        >  Remarque : l'onglet Délégation est visible uniquement si l'objet a un SPN qui lui est affecté. c2WTS ne nécessite pas de SPN sur le compte c2WTS, mais sans SPN, l’onglet **Délégation** ne sera pas visible. Une autre façon de configurer la délégation contrainte consiste à utiliser un utilitaire tel que **ADSIEdit**.  
  
    2.  Les options de configuration principales dans l'onglet Délégation sont les suivantes :  
  
        -   Sélectionnez « N'approuver cet utilisateur que pour la délégation aux services spécifiés »  
  
        -   Sélectionnez « Utiliser tout protocole d'authentification »  
  
         Pour plus d'informations, consultez la rubrique relative à la configuration de la délégation contrainte Kerberos pour les ordinateurs et les comptes de service dans le livre blanc suivant : [Configuration de l'authentification Kerberos pour les produits SharePoint 2010 et SQL Server 2008 R2](http://blogs.technet.com/b/tothesharepoint/archive/2010/07/22/whitepaper-configuring-kerberos-authentication-for-sharepoint-2010-and-sql-server-2008-r2-products.aspx)  
  
2.  Configurer les « appelants autorisés » dans C2WTS  
  
     c2WTS requiert que les identités 'appelants' explicitement répertoriées dans le fichier de configuration **c2wtshost.exe.config**. c2WTS n’accepte pas les demandes de tous les utilisateurs authentifiés dans le système, sauf si elle est configurée pour ce faire. Dans ce cas l'appelant est le groupe Windows WSS_WPG. Le fichier c2wtshost.exe.confi est enregistré à l'emplacement suivant :  
  
     **\Program Files\Windows identité Foundation\v3.5\c2wtshost.exe.config**  
  
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
  
3.  Démarrez le service C2WTS du système d’exploitation :  
  
    1.  Configurez le service pour utiliser le compte de service que vous avez configuré à l'étape précédente.  
  
    2.  Changez le type de démarrage en**Automatique**et démarrez le service.  
  
4.  Démarrer les revendications SharePoint vers Windows Token Service : Démarrez les revendications SharePoint vers Windows Token Service via l'Administration centrale de SharePoint sur la page **Gérer les ervices sur le serveur** . Le service doit être démarré sur le serveur qui effectuera l'action. Par exemple si vous avez un serveur Web frontal et un serveur d’applications exécutant le service partagé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , il vous suffit de démarrer C2WTS sur le serveur d’applications. C2WTS n’est pas nécessaire sur le serveur Web frontal.  
  
## <a name="see-also"></a>Voir aussi  
 [Prétend (de la vue d’ensemble du Service d’émission de jeton Windows (c2WTS)http://msdn.microsoft.com/library/ee517278.aspx)](http://msdn.microsoft.com/library/ee517278.aspx)   
 [Vue d’ensemble de l’authentification Kerberos pour les produits Microsoft SharePoint 2010)http://technet.microsoft.com/library/gg502594.aspx)](http://technet.microsoft.com/library/gg502594.aspx)  
  
  