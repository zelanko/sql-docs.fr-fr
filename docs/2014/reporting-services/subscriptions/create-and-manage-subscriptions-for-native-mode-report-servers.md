---
title: Créer, modifier et supprimer des abonnements standard (Reporting Services en mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- standard subscriptions [Reporting Services]
- subscriptions [Reporting Services], standard
ms.assetid: 5ab1c661-9bfa-434a-b315-faac34ed12b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c929fd63cb886eaad301697d4eee245ffb30301c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66100991"
---
# <a name="create-modify-and-delete-standard-subscriptions-reporting-services-in-native-mode"></a>Créer, modifier et supprimer les abonnements standard (Reporting Services en mode natif)
  L'abonnement standard est un abonnement créé par des utilisateurs individuels qui souhaitent recevoir des rapports par messagerie électronique ou dans un dossier partagé. Ce type d'abonnement est toujours défini en fonction du rapport sur lequel il est basé.  
  
 Un utilisateur qui crée un abonnement en est le propriétaire. Chaque utilisateur peut modifier ou supprimer les abonnements qu'il possède.  
  
> [!NOTE]  
>  Depuis [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous pouvez transférer par programme la propriété d'un abonnement. Aucune interface utilisateur ne permet de transférer la propriété des abonnements. Pour plus d'informations, consultez <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A>  
  
 Suivant les paramètres du fichier de configuration **RSReportServer.config** , les utilisateurs ont la possibilité d'ajouter des utilisateurs supplémentaires à un abonnement. Un responsable peut ainsi ajouter les adresses de messagerie de ses subordonnés directs pour qu'ils reçoivent une copie du rapport. La prise en charge de ceci varie selon que le champ À : est visible ou non lors de la définition d'abonnements individuels. Pour plus d’informations, consultez [configurer un serveur de rapports pour la remise par messagerie &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
 Cette rubrique fournit des informations sur les abonnements standard qui sont créés et gérés par des utilisateurs individuels. Les abonnements pilotés par les données ne fonctionnent pas de la même façon et sont décrits dans une rubrique distincte. Pour plus d’informations, consultez [créer, modifier et supprimer un abonnement piloté par les données](data-driven-subscriptions.md).  
  
 Dans cette rubrique :  
  
-   [Pour créer un abonnement](#bkmk_create_subscription)  
  
-   [Pour créer un abonnement de partage de fichiers](#bkmk_create_fileshare_subscription)  
  
-   [Pour créer un abonnement par courrier électronique](#bkmk_create_email_subscription)  
  
-   [Pour modifier un abonnement](#bkmk_modify_subscription)  
  
-   [Pour supprimer un abonnement](#bkmk_delete_subscription)  
  
##  <a name="to-create-a-subscription"></a><a name="bkmk_create_subscription"></a>Pour créer un abonnement  
 Pour créer un abonnement, choisissez l'outil et l'approche appropriés au déploiement de votre serveur de rapports :  
  
-   Le contenu de cette rubrique explique comment créer des abonnements sur un serveur de rapports en mode natif à l'aide du Gestionnaire de rapports de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Après avoir défini un abonnement, vous avez la possibilité d'y accéder dans le Gestionnaire de rapports via la page Mes abonnements ou l'onglet **Abonnements** d'un rapport spécifique.  
  
-   [Créer et gérer des abonnements pour les serveurs de rapports en mode SharePoint](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) explique comment utiliser les pages d’application d’un site SharePoint pour vous abonner à des rapports sur un serveur de rapports qui s’exécute en mode intégré SharePoint.  
  
 Cette rubrique détaille la procédure de création d'un abonnement pour une remise par courrier électronique ou dans un partage de fichiers.  
  
-   Pour utiliser la remise par messagerie électronique, le serveur de rapports doit être configuré pour une connexion de passerelle ou de serveur SMTP avant la création de l'abonnement.  
  
-   Si vous souhaitez utiliser la remise par partage de fichiers, le dossier cible doit avoir été défini. Pour plus d’informations, consultez [configurer un serveur de rapports pour la remise par messagerie &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
 Pour que vous puissiez vous abonner à un rapport, la source de données du rapport doit être configurée pour utiliser des informations d'identification stockées ou aucune information d'identification. Pour plus d’informations, consultez [Stocker les informations d’identification dans une source de données Reporting Services](../report-data/store-credentials-in-a-reporting-services-data-source.md). Si aucune information d'identification n'est utilisée, le bouton **Nouvel abonnement** n'est pas disponible.  
  
 Cette rubrique n'explique pas comment créer un abonnement piloté par les données. Pour obtenir des instructions sur la création d’un abonnement piloté par les données, consultez [Créer un abonnement piloté par les données &#40;didacticiel SSRS&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md) ou recherchez la page d’informations relatives à la création d’un abonnement piloté par les données dans l’aide en ligne du Gestionnaire de rapports.  
  
###  <a name="to-create-a-file-share-subscription"></a><a name="bkmk_create_fileshare_subscription"></a>Pour créer un abonnement de partage de fichiers  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Dans le Gestionnaire de rapports, dans la page **Contenu** , naviguez jusqu'au rapport auquel vous voulez vous abonner. Cliquez sur le rapport pour l'ouvrir.  
  
3.  Cliquez sur l'onglet **Abonnements** , puis sur l'option **Nouvel abonnement**.  
  
4.  Dans **Remis par**, sélectionnez **Partage de fichiers Windows**.  
  
5.  Dans **Nom de fichier**, tapez le nom de fichier du rapport.  
  
6.  Sélectionnez **Ajouter une extension de fichier lorsque le fichier est créé**. Cette option ajoute une extension de trois caractères au nom de fichier. L'extension de fichier est déterminée par le format de sortie sélectionné pour le rapport.  
  
7.  Dans la zone de texte **chemin d’accès** , tapez un chemin d’accès UNC (Universal Naming Convention) vers un dossier existant dans lequel vous souhaitez remettre les \\ \\ rapports (\> \\ par exemple\>,<ServerName<MyReports). Insérez deux barres obliques inverses au début du chemin d'accès. Ne spécifiez pas de barre oblique de fin.  
  
8.  Dans Format du rendu, sélectionnez un format de sortie du rapport pour la remise de fichier. Choisissez un format qui correspond à l'application bureautique qui sera utilisée pour ouvrir le rapport. Évitez les formats qui n'effectuent pas le rendu d'un rapport en un seul flux ou qui introduisent une interactivité non prise en charge dans un fichier statique (par exemple le format HTML 4.0).  
  
9. Dans les zones de texte **Nom d’utilisateur** et **Mot de passe**, indiquez les informations d’identification nécessaires pour accéder au partage de fichiers en respectant le format *\<domaine>* \\ *\<nom_utilisateur>* pour le nom d’utilisateur.  
  
10. Spécifiez les options de remplacement. En activant l'option **Ne pas remplacer le fichier si une version précédente existe**, vous empêchez la remise d'avoir lieu si un fichier existant est détecté. Si vous cliquez sur **Incrémenter les noms des fichiers au fur et à mesure que des versions plus récentes sont ajoutées**, le serveur de rapports ajoute un numéro au nom du fichier pour le distinguer des fichiers existants qui portent le même nom.  
  
11. Indiquez quand le rapport devra être remis :  
  
    -   Pour planifier une heure de remise, cliquez sur **Lorsque l'exécution planifiée du rapport est terminée** , puis cliquez sur le bouton **Sélectionner une planification** . Une page de planification s'ouvre.  
  
    -   Pour sélectionner une planification partagée prédéfinie qui comporte déjà les informations de date, d'heure et de périodicité que vous souhaitez utiliser, cliquez sur **Suivant une planification partagée**, puis sélectionnez la planification à utiliser.  
  
    -   Pour remettre le rapport quand un instantané de rapport est mis à jour avec une nouvelle version, cliquez sur**Lors de l’actualisation du contenu du rapport**. Si vous vous abonnez à un rapport qui récupère des données à des intervalles planifiés, la planification utilisée pour actualiser les données détermine le moment où votre abonnement sera traité.  
  
        > [!NOTE]  
        >  Cette option n'est disponible que pour les instantanés déjà associés à une planification de mise à jour.  
  
12. Pour les rapports paramétrables, spécifiez les paramètres à utiliser pour le rapport correspondant à cet abonnement. Les paramètres peuvent différer de ceux utilisés pour l'exécution du rapport à la demande ou de ceux mis en œuvre dans d'autres opérations planifiées.  
  
 Le rapport est remis sous forme de fichier statique. Si le rapport comprend des fonctionnalités interactives (par exemple des liens vers des lignes et colonnes supplémentaires), ces fonctionnalités ne sont pas disponibles.  
  
###  <a name="to-create-an-e-mail-subscription"></a><a name="bkmk_create_email_subscription"></a>Pour créer un abonnement par courrier électronique  
  
1.  Dans le Gestionnaire de rapports, dans la page **Contenu** , naviguez jusqu'au rapport auquel vous voulez vous abonner. Cliquez sur le rapport pour l'ouvrir.  
  
2.  Cliquez sur l'onglet **Abonnements** , puis sur l'option **Nouvel abonnement**.  
  
3.  Dans **Remis par**, sélectionnez **Messagerie électronique**. Si ce type de remise n'est pas disponible, votre serveur de rapports n'est pas configuré pour les abonnements par messagerie électronique.  
  
4.  Dans la zone de texte **À** , le nom du destinataire dans le champ À : est renseigné automatiquement à l'aide de votre compte d'utilisateur de domaine. Les paramètres de configuration du serveur de rapports déterminent si le champ **À** est renseigné automatiquement à l'aide de votre compte d'utilisateur. Pour plus d’informations sur la modification des paramètres de configuration des adresses de messagerie, consultez [configurer un serveur de rapports pour la remise par messagerie &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
    > [!NOTE]  
    >  En fonction de vos autorisations, vous pouvez taper l'adresse de messagerie à laquelle le rapport doit être remis. Si vous spécifiez plusieurs adresses, séparez-les par des points-virgules (;). Vous pouvez aussi taper des adresses e-mail supplémentaires dans les zones de texte **Cc**, **Cci**et **Répondre à** . Pour cela, vous devez disposer de l'autorisation de gestion de tous les abonnements.  
  
5.  Sélectionnez les options de remise comme suit :  
  
    -   Pour incorporer ou joindre un exemplaire du rapport, sélectionnez **Inclure un rapport**. Le format du rapport est déterminé par le format de rendu sélectionné. Ne choisissez pas cette option si vous pensez que la taille du rapport peut dépasser la limite définie pour votre système de messagerie.  
  
    -   Pour insérer une URL pointant vers le rapport dans le corps du courrier électronique, sélectionnez **Inclure un lien**.  
  
    > [!NOTE]  
    >  Si vous désactivez ces deux options, seul le texte de notification de la ligne Objet est envoyé.  
  
6.  Choisissez un format de rendu dans la zone de liste **Format du rendu** . Cette option est disponible si vous sélectionnez **Inclure un rapport** pour incorporer ou joindre une copie du rapport.  
  
    -   Pour incorporer le rapport au corps du message électronique, sélectionnez **Archive Web**.  
  
    -   Pour envoyer le rapport sous forme de pièce jointe, choisissez le format de rendu de votre choix.  
  
7.  Dans la zone de liste **Priorité** , sélectionnez une priorité. Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange, ce paramètre définit un indicateur en rapport avec le niveau d’importance du message électronique.  
  
8.  Indiquez quand le rapport devra être remis :  
  
    -   Pour planifier une heure de remise, cliquez sur **Lorsque l'exécution planifiée du rapport est terminée** , puis cliquez sur **Sélectionner une planification**. Une page de planification s'ouvre.  
  
    -   Pour sélectionner une planification partagée prédéfinie qui comporte déjà les informations de date, d'heure et de périodicité que vous souhaitez utiliser, cliquez sur **Suivant une planification partagée**, puis sélectionnez la planification à utiliser.  
  
    -   Pour remettre le rapport quand un instantané de rapport est mis à jour avec une nouvelle version, cliquez sur**Lors de l’actualisation du contenu du rapport**. Si vous vous abonnez à un rapport qui récupère des données à des intervalles planifiés, la planification utilisée pour actualiser les données détermine le moment où votre abonnement sera traité.  
  
    > [!NOTE]  
    >  Cette option n'est disponible que pour les instantanés déjà associés à une planification de mise à jour.  
  
9. Pour les rapports paramétrables, spécifiez les paramètres à utiliser pour le rapport correspondant à cet abonnement. Les paramètres spécifiés peuvent différer de ceux utilisés pour exécuter le rapport à la demande ou de ceux mis en œuvre dans les autres opérations planifiées.  
  
##  <a name="to-modify-a-subscription"></a><a name="bkmk_modify_subscription"></a>Pour modifier un abonnement  
 Vous pouvez modifier un abonnement à tout moment. Lorsque vous modifiez un abonnement lors de son traitement, les paramètres mis à jour sont utilisés s'ils sont enregistrés dans la base de données du serveur de rapports avant que l'extension de remise ne reçoive les données d'abonnement. Dans le cas contraire, les paramètres existants sont utilisés.  
  
 Pour localiser un abonnement, utilisez la page **Mes abonnements** ou affichez les définitions d'abonnement associées à un rapport. Vous ne pouvez pas rechercher directement les abonnements, pas plus que vous ne pouvez rechercher un abonnement par nom de propriétaire, informations de déclencheur, informations d'état, etc.  
  
 Les abonnements peuvent également être modifiés ou supprimés par les administrateurs des serveurs de rapports.  
  
> [!NOTE]  
>  Un administrateur de serveur de rapports ne peut pas centraliser la gestion de tous les abonnements individuels en cours d'utilisation sur un serveur de rapports donné. Il peut toutefois accéder à chaque abonnement pour le modifier ou le supprimer.  
  
##  <a name="to-delete-a-subscription"></a><a name="bkmk_delete_subscription"></a>Pour supprimer un abonnement  
 Pour supprimer un abonnement  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Dans le Gestionnaire de rapports, cliquez sur **Mes abonnements** dans la barre d'outils globale et parcourez l'arborescence jusqu'à l'abonnement à modifier ou à supprimer.  
  
3.  Vous pouvez également, si le rapport est ouvert, afficher l'onglet **Abonnements** pour rechercher la description que vous souhaitez modifier ou supprimer. Effectuez une des opérations suivantes :  
  
    1.  Pour procéder à une modification sur un abonnement, cliquez sur **Modifier**.  
  
    2.  Pour supprimer un abonnement, activez la case à cocher située en regard de cet abonnement, puis cliquez sur **Supprimer**.  
  
 Cette rubrique n'explique pas comment annuler un abonnement en cours de traitement sur le serveur de rapports. Pour plus d’informations sur l’annulation des abonnements, consultez [gérer un processus en cours d’exécution](manage-a-running-process.md) .  
  
 Si vous voulez mettre fin à un abonnement et si vous n'arrivez pas à le localiser facilement, prenez note du rapport que vous recevez et faites une recherche sur son nom. Une fois que vous accédez au rapport, vous pouvez vous retirer de l'abonnement. Si vous n'arrivez pas à localiser l'abonnement, celui-ci est peut-être de type piloté par les données. Pour plus d'informations, contactez l'administrateur de votre serveur de rapports.  
  
 Un abonnement est supprimé automatiquement lorsque le rapport sous-jacent est supprimé. Si vous supprimez un abonnement lors de son traitement, l'abonnement s'arrête lorsque la suppression intervient avant que l'extension de remise n'ait reçu les données d'abonnement. Dans le cas contraire, le traitement de l'abonnement se poursuit.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et autorisations](../security/tasks-and-permissions.md)   
 [Create and Manage Subscriptions for SharePoint Mode Report Servers](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md)   
 [Créer et gérer des abonnements pour les serveurs de rapports en mode natif](../create-manage-subscriptions-native-mode-report-servers.md)   
 [Data-Driven Subscriptions](data-driven-subscriptions.md)   
 [Abonnements et remise &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md)   
 [Utiliser Mes abonnements](use-my-subscriptions-native-mode-report-server.md)  
  
  
