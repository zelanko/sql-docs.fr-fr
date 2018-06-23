---
title: Configurer la messagerie électronique pour l’Application de Service (SharePoint 2010 et SharePoint 2013) pour Reporting Services | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 0e12d4d1c630dcc1e46492cf93582ab5b882e3af
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041769"
---
# <a name="configure-e-mail-for-a-reporting-services-service-application-sharepoint-2010-and-sharepoint-2013"></a>Configurer la messagerie électronique pour une application de service Reporting Services (SharePoint 2010 et SharePoint 2013)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] L’alerte de données Reporting Services envoie des messages électroniques d’alerte. Pour envoyer du courrier électronique, vous devrez peut-être configurer votre application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et modifier l'extension de remise par messagerie pour l'application de service. Les paramètres de messagerie sont également requis si vous prévoyez d'utiliser l'extension de remise par messagerie pour la fonctionnalité d'abonnement de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Mode SharePoint &#124; SharePoint 2010 et SharePoint 2013.|  
  
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
  
1.  Si votre environnement de messagerie requiert l'authentification NTLM et n'autorise pas l'accès anonyme, vous devez modifier la configuration d'extension de remise par messagerie de vos applications de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Modifiez **SMTPAuthenticate** pour utiliser une valeur de 2. Cette valeur ne peut pas être modifiée à partir de l'interface utilisateur. L'exemple de script PowerShell suivant met à jour la configuration complète pour l'extension de remise du courrier électronique par le serveur de rapports pour l'application de service nommée SSRS_TESTAPPLICATION. Notez que certains nœuds répertoriés dans le script peuvent également être définis à partir de l'interface utilisateur, par exemple l'adresse « De ».  
  
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
  
  