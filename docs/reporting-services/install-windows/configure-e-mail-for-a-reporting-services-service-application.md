---
title: Configurer l’e-mail pour une application de service Reporting Services | Microsoft Docs
ms.date: 05/10/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint
ms.topic: conceptual
ms.assetid: 38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016 <=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 29b5ba7b28781351232ba1a51ad20b6b84fbfce7
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050861"
---
# <a name="configure-e-mail-for-a-reporting-services-service-application"></a>Configurer la messagerie électronique pour une application de service Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] L’alerte de données Reporting Services envoie des messages électroniques d’alerte. Pour envoyer du courrier électronique, vous devrez peut-être configurer votre application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et modifier l'extension de remise par messagerie pour l'application de service. Les paramètres de messagerie sont également requis si vous prévoyez d'utiliser l'extension de remise par messagerie pour la fonctionnalité d'abonnement de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  

> [!NOTE]
> L’intégration de Reporting Services à SharePoint n’est plus disponible après SQL Server 2016.
  
### <a name="to-configure-e-mail-for-the-shared-service"></a>Pour configurer la messagerie pour le service partagé  
  
1.  Dans l'Administration centrale de SharePoint, cliquez sur **Gestion des applications**.  
  
2.  Dans le groupe **Applications de service** , cliquez sur **Gérer les applications de service**.  
  
3.  Dans la liste **Nom** , cliquez sur le nom de votre application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
4.  Cliquez sur **Paramètres de messagerie** dans la page **Gérer l’application Reporting Services** .  
  
5.  Sélectionnez **Utiliser le serveur SMTP**.  
  
6.  Dans la zone **Serveur SMTP sortant** , tapez le nom d'un serveur SMTP.  
  
7.  Dans la zone **Adresse de provenance** , tapez une adresse de messagerie.  
  
     Cette adresse est l'expéditeur de tous les messages électroniques d'alerte.  
  
     Le compte de l'utilisateur spécifié dans **Adresse de provenance** doit être un compte géré que vous avez spécifié lors de la configuration du pool d'applications pour l'application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Si vous en avez l'autorisation, vous pouvez afficher une liste des comptes gérés existants dans la page Comptes de service dans l'Administration centrale de SharePoint.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="ntlm-authentication"></a>Authentification NTLM  
  
1.  Si votre environnement de messagerie requiert l'authentification NTLM et n'autorise pas l'accès anonyme, vous devez modifier la configuration d'extension de remise par messagerie de vos applications de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Par exemple, si vous voyez le message suivant pour **Derniers résultats** sur la page **Gérer les abonnements** .  
  
    -   Échec de l’envoi du message électronique : le serveur SMTP requiert une connexion sécurisée ou le client n’était pas authentifié. La réponse du serveur était : 5.7.1 Le client n’était pas authentifié. Le message ne sera pas renvoyé.  
  
     Modifiez **SMTPAuthenticate** pour utiliser une valeur de 2. Cette valeur ne peut pas être modifiée à partir de l'interface utilisateur. L'exemple de script PowerShell suivant met à jour la configuration complète pour l'extension de remise du courrier électronique par le serveur de rapports pour l'application de service nommée SSRS_TESTAPPLICATION. Notez que certains nœuds répertoriés dans le script peuvent également être définis à partir de l'interface utilisateur, par exemple l'adresse « De ».  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRS_TESTAPPLICATION *"}  
    $emailCfg = Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml   
    $emailXml = [xml]$emailCfg   
    $emailXml.SelectSingleNode("//SMTPServer").InnerText = “your email server name"  
    $emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
    $emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
    $emailXml.SelectSingleNode("//From").InnerText = “your FROM email address”  
    Set-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
    ```  
  
2.  Si vous devez vérifier le nom de votre application de service, exécutez **l’applet de commande Get-SPRSServiceApplication**.  
  
    ```  
    get-sprsserviceapplication  
    ```  
  
3.  L'exemple suivant retourne les valeurs actuelles de l'extension de messagerie pour l'application de service nommée SSRS_TESTAPPLICATION.  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRSTEST_APPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
    ```  
  
4.  L'exemple suivant crée un nouveau fichier nommé emailconfig.txt contenant les valeurs actuelles de l'extension de messagerie pour l'application de service nommée SSRS_TESTAPPLICATION  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRS_TESTAPPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml | out-file c:\emailconfig.txt  
    ```  
  
  
D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
