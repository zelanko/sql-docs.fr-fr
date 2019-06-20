---
title: Page de paramètres (Gestionnaire de rapports) de site | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4d67a01c-eae4-49ba-a6e8-8e983c0248f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 07fc0207020887d7e3ceb8716ee76c78a55d2bac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66101123"
---
# <a name="site-settings-page-report-manager"></a>Page Paramètres du site (Gestionnaire de rapports)
  Utilisez la page Paramètres du site pour modifier le titre de l'application, définir des valeurs par défaut à l'échelle du serveur pour les limites de l'historique de rapport et les valeurs du délai d'exécution du traitement du rapport, gérer les attributions de rôle au niveau du système et gérer les planifications partagées. Vous devez disposer des autorisations de gestionnaire de contenu et d'administrateur système pour consulter cette page.  
  
> [!NOTE]  
>  Les fonctionnalités suivantes sont disponibles dans chaque édition de SQL Server : historique de rapport, exécution de rapport et planifications partagées. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
### <a name="to-open-the-site-settings-page"></a>Pour ouvrir la page Paramètres du site  
  
1.  Ouvrez le Gestionnaire de rapports.  
  
2.  Cliquez sur **Paramètres du site**en haut de la page. La page des propriétés générales du site s'ouvre.  
  
     **Remarque :** Si vous ne voyez pas le **paramètres du Site** option dans le menu, vous n’avez pas les autorisations requises, pour plus d’informations, consultez la section « Paramètres du site » de [configurer un serveur de rapports en Mode natif pour l’Administration locale &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="options"></a>Options  
 **Nom**  
 Spécifiez le titre à utiliser pour cette instance du Gestionnaire de rapports [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Par défaut, le titre est «[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]».  
  
 **Sélectionnez les paramètres par défaut pour l’historique de rapport**  
 Sélectionnez une valeur par défaut pour déterminer le nombre de copies que l'historique de rapport peut conserver. La valeur par défaut fournit un paramètre initial qui établit les limites de l'historique de rapport. Vous pouvez modifier ces paramètres au niveau des rapports. Pour plus d’informations, consultez [Page de propriétés Options d’instantanés &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md).  
  
 Si vous limitez l'historique de rapport ultérieurement, le serveur de rapports applique la nouvelle limite à l'historique de rapport existant dès que celui-ci la dépasse. Les instantanés de rapport les plus anciens sont supprimés en premier. Si l'historique de rapport est vide ou n'a pas atteint la limite, de nouveaux instantanés de rapport sont ajoutés. Lorsque la limite est atteinte, l'instantané le plus ancien est supprimé dès qu'un nouvel instantané est ajouté.  
  
 **Délai d’exécution de rapport**  
 Spécifie si le traitement d'un rapport expire après un certain nombre de secondes.  
  
 Cette valeur s'applique au traitement du rapport sur le serveur de rapports. Elle n'a aucune incidence sur le traitement des données sur le serveur de base de données qui fournit les données pour le rapport.  
  
 La minuterie du traitement du rapport commence lorsque le rapport est sélectionné et s'arrête lors de l'ouverture du rapport. Lorsque vous définissez cette valeur, spécifiez suffisamment de temps pour terminer le traitement des données et du rapport.  
  
 **URL de lancement du Générateur de rapports personnalisé**  
 Spécifie une URL personnalisée lorsque le serveur de rapports n'utilise pas l'URL par défaut du Générateur de rapports. Ce paramètre est facultatif. Si vous ne spécifiez pas de valeur, l'URL par défaut sera utilisée pour lancer le Générateur de rapports comme une application ClickOnce. L'URL par défaut est l'une des suivantes :  
  
 **Serveur de rapports en mode natif :** Dans une installation en mode natif, l’URL par défaut prendra la forme http://\<*computername*> / reportserver/ReportBuilder/ReportBuilder_3_0_0_0.application.  
  
 Mode intégré SharePoint : L’URL par défaut prendra la forme http://\<*Site_sharepoint*> / _vti_bin/ReportBuilder/ReportBuilder_3_0_0_0.application. »  
  
 **Appliquer**  
 Cliquez pour enregistrer les modifications apportées au serveur de rapports.  
  
 **Sécurité**  
 Cliquez sur ce lien pour ouvrir la page Attributions de rôle système, sur laquelle vous pouvez attribuer des comptes d'utilisateurs et de groupes à des rôles système prédéfinis.  
  
 **Planifications**  
 Cliquez sur ce lien pour ouvrir la page Planifications, sur laquelle vous pouvez prédéfinir les planifications partagées que les utilisateurs peuvent sélectionner pour leurs rapports et abonnements.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Octroi d'autorisations sur un serveur de rapports en mode natif](security/granting-permissions-on-a-native-mode-report-server.md)   
 [Rôles prédéfinis](security/role-definitions-predefined-roles.md)   
 [Aide (F1) du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
