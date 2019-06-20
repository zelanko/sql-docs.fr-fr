---
title: Remise par courrier électronique dans Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], e-mail
- e-mail [Reporting Services]
- mail [Reporting Services]
ms.assetid: fda2f130-97b9-4258-9dbb-e93a70f4d08a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 68024e36dd5f8188097ebcc673056c1b6d11e59b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66100884"
---
# <a name="e-mail-delivery-in-reporting-services"></a>Remise par courrier électronique dans Reporting Services
  SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] comprend une extension de remise par e-mail qui permet d’envoyer par e-mail des rapports à des utilisateurs individuels ou à des groupes. Vous pouvez configurer l'extension de remise par messagerie à l'aide du Gestionnaire de configuration de Reporting Services et en modifiant les fichiers de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Pour distribuer ou recevoir un rapport par courrier électronique, vous devez définir un abonnement standard ou piloté par les données. Vous pouvez vous abonner ou effectuer la remise que d'un seul rapport à la fois. Vous ne pouvez pas créer d'abonnement qui distribue plusieurs rapports dans un seul message électronique. Pour plus d’informations sur les abonnements, consultez [créer, modifier et supprimer des abonnements Standard &#40;Reporting Services en Mode natif&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Mode SharePoint &#124; SharePoint 2010 et SharePoint 2013<br /><br /> **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif|  
  
## <a name="e-mail-delivery-options"></a>Options de remise des rapports par messagerie  
 La remise de rapports par messagerie du serveur de rapports s'effectue de différentes manières :  
  
-   Envoi d'une notification et d'un lien hypertexte vers le rapport généré.  
  
-   Envoi d'une notification dans la ligne Objet d'un message électronique. Par défaut, la ligne Objet de la définition d'abonnement contient les variables suivantes qui sont remplacées par des informations spécifiques au rapport lors du traitement de l'abonnement.  
  
     **@ReportName** spécifie le nom du rapport.  
  
     **@ExecutionTime** spécifie l'heure d'exécution du rapport.  
  
     Vous pouvez combiner ces variables avec du texte statique ou modifier le texte dans la ligne Objet de chaque abonnement.  
  
-   Envoi d'un rapport incorporé ou joint. Le format de rendu et le navigateur déterminent si le rapport est incorporé ou joint.  
  
     Si votre navigateur prend en charge les formats HTML 4.0 et MHTML et si vous choisissez le format de rendu Archive Web, le rapport est incorporé au message. Tous les autres formats de rendu (CSV, PDF, etc.) remettent les rapports sous forme de pièces jointes. Vous pouvez désactiver cette fonction dans le fichier de configuration RSReportServer.  
  
     [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne vérifie pas la taille de la pièce jointe ou du message avant d'envoyer le rapport. Si la pièce jointe ou le message dépasse la limite maximale autorisée par votre serveur de messagerie, le rapport n'est pas remis. Choisissez une des autres options de remise (URL ou notification) si le rapport est volumineux.  
  
 C'est au moment de la création de l'abonnement que vous définissez les options de remise d'un rapport. Par exemple, si vous sélectionnez **Inclure un lien** dans l'abonnement, le message électronique contient un lien hypertexte vers le rapport.  
  
## <a name="role-based-e-mail-settings"></a>Paramètres de messagerie basés sur les rôles  
 Lorsque vous vous abonnez à un rapport, les paramètres de remise par messagerie que vous utilisez varient en fonction de votre rôle qui englobe soit la tâche « Gérer les abonnements individuels », soit la tâche « Gérer tous les abonnements ».  
  
|Tâche|Paramètres disponibles|  
|----------|------------------------|  
|Gérer les abonnements individuels|Affiche les champs qui permettent à un utilisateur d'automatiser et de se remettre un rapport. Dans ce mode, les champs qui acceptent les adresses de messagerie ne sont pas disponibles.|  
|Gérer tous les abonnements|Affiche les champs qui prennent en charge une plus large distribution, notamment À, Cc, Cci et Répondre à, qui offrent des moyens supplémentaires d'acheminer un rapport vers des abonnés plus nombreux. La disponibilité des champs d'alias de messagerie électronique est définie par le biais des paramètres du fichier de configuration RSReportServer.|  
  
## <a name="specifying-e-mail-addresses-in-a-subscription"></a>Spécification d'adresses électroniques dans un abonnement  
 Si vous effectuez la distribution des rapports au sein d'un intranet et si vous utilisez une passerelle SMTP vers un serveur [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange, tapez les alias de messagerie (comme si vous envoyiez du courrier électronique à un collègue). Si la remise est destinée à un compte de messagerie externe, tapez l'adresse de messagerie complète. Si vous spécifiez des adresses de messagerie supplémentaires pour ajouter d'autres personnes à votre abonnement, les abonnés reçoivent une copie exacte du rapport qui est produit à partir de cet abonnement.  
  
 Le serveur de rapports n'obtient ni ne valide les adresses de messagerie d'un serveur de messagerie. Vous devez connaître à l'avance les adresses de messagerie qui seront utilisées. Par défaut, vous pouvez envoyer des rapports par courrier électronique à n'importe quel compte de messagerie valide à l'intérieur ou à l'extérieur de votre organisation. Des paramètres de configuration peuvent toutefois être utilisés pour limiter la remise par messagerie électronique aux hôtes du serveur de courrier que vous identifiez par leur nom. Vous pouvez spécifier des hôtes supplémentaires si vous voulez prendre en charge la remise par messagerie à des personnes ne faisant pas partie de votre organisation.  
  
 Le message électronique utilisé pour remettre le rapport doit être envoyé depuis un compte de messagerie défini sur le serveur de messagerie. Un paramètre de configuration spécifie le compte de messagerie. Le compte de messagerie est utilisé pour tous les rapports remis par l'extension de remise par messagerie. Vous ne pouvez pas spécifier plusieurs comptes ou changer de compte en fonction des rapports.  
  
## <a name="e-mail-server-configuration"></a>Configuration du serveur de messagerie  
 Le serveur de rapports se connecte à un serveur de messagerie à l'aide d'une connexion standard. Il n'utilise pas le chiffrement SSL (Secure Sockets Layer) pour ses communications. Le serveur de messagerie doit être un serveur SMTP (Simple Mail Transport Protocol) local ou distant situé sur le même réseau que le serveur de rapports.  
  
 Pour plus d'informations sur la configuration d'un serveur de rapports en mode natif, consultez :  
  
-   [Configurer un serveur de rapports pour la remise du courrier électronique &#40;Gestionnaire de Configuration de SSRS&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
  
-   [Paramètres de messagerie - Gestionnaire de Configuration &#40;SSRS en Mode natif&#41;](../install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md)  
  
 Pour plus d'informations sur la configuration d'un serveur de rapports en mode SharePoint, consultez :  
  
-   [Configurer la messagerie électronique pour une application de service Reporting Services &#40;SharePoint 2010 et SharePoint 2013&#41;](../install-windows/configure-e-mail-for-a-reporting-services-service-application.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et autorisations](../security/tasks-and-permissions.md)   
 [Abonnements et remise &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md)   
 [Abonnements pilotés par les données](data-driven-subscriptions.md)   
 [Attributions de rôles](../security/role-assignments.md)  
  
  
