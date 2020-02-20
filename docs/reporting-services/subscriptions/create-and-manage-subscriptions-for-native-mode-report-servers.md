---
title: Créer et gérer des abonnements pour les serveurs de rapports en mode natif | Microsoft Docs
ms.date: 05/28/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: subscriptions
ms.topic: conceptual
helpviewer_keywords:
- standard subscriptions [Reporting Services]
- subscriptions [Reporting Services], standard
ms.assetid: 5ab1c661-9bfa-434a-b315-faac34ed12b1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 69cc078dc5ce605f1d7bf55d872c2a4629eb3301
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "66403256"
---
# <a name="create-and-manage-subscriptions-for-native-mode-report-servers"></a>Créer et gérer des abonnements pour les serveurs de rapports en mode natif
  L'abonnement standard est un abonnement créé par des utilisateurs individuels qui souhaitent recevoir des rapports par messagerie électronique ou dans un dossier partagé. Cette rubrique fournit des informations sur les abonnements standard qui sont créés et gérés par des utilisateurs individuels. Les abonnements pilotés par les données ne fonctionnent pas de la même façon et sont décrits dans une rubrique distincte. Pour plus d’informations, consultez [Créer, modifier ou supprimer des abonnement pilotés par les données](../../reporting-services/subscriptions/create-modify-and-delete-data-driven-subscriptions.md).  
  
 **Dans cet article :**  
  
-   [Spécifications générales pour les abonnements](#bkmk_create_subscription)  
  
-   [Pour créer un abonnement pour un partage de fichiers](#bkmk_create_fileshare_subscription)  
  
-   [Pour créer un abonnement par e-mail](#bkmk_create_email_subscription)  
  
-   [Pour modifier un abonnement](#bkmk_modify_subscription)  
  
-   [Pour supprimer un abonnement](#bkmk_delete_subscription)  
  
##  <a name="bkmk_create_subscription"></a> Spécifications générales pour les abonnements  
 Le contenu de cet article explique comment créer des abonnements sur un serveur de rapports en mode natif à l'aide du portail web dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Après avoir défini un abonnement, vous avez la possibilité d'y accéder dans le portail web via la page Mes abonnements ou l'onglet **Abonnements** d'un rapport spécifique.  
  
 [Créer et gérer des abonnements pour des serveurs de rapports en mode SharePoint](../../reporting-services/subscriptions/create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) explique comment utiliser les pages d’application d’un site SharePoint pour vous abonner aux rapports d’un serveur de rapports en mode SharePoint.  
  
-   Pour utiliser la remise par messagerie électronique, le serveur de rapports doit être configuré pour une connexion de passerelle ou de serveur SMTP avant la création de l'abonnement. Pour plus d’informations, consultez [Remise par courrier électronique dans Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md).  
  
-   Si vous souhaitez utiliser la remise par partage de fichiers, le dossier cible doit avoir été défini. Pour plus d’informations, consultez [Paramètres d’abonnement et compte de partage de fichiers (Configuration Manager)](../install-windows/subscription-settings-and-a-file-share-account-configuration-manager.md).  
  
 Pour que vous puissiez vous abonner à un rapport, la source de données du rapport doit être configurée pour utiliser des informations d'identification stockées ou aucune information d'identification. Pour plus d’informations, consultez [Stocker les informations d’identification dans une source de données Reporting Services](../../reporting-services/report-data/store-credentials-in-a-reporting-services-data-source.md). Si ce n’est pas le cas, le bouton **Nouvel abonnement** n'est pas disponible.  
  
 Cet article n'explique pas comment créer un abonnement piloté par les données. Pour savoir comment créer un abonnement piloté par les données, consultez [Créer un abonnement piloté par les données &#40;didacticiel SSRS&#41;](../../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md).  
  
###  <a name="bkmk_create_fileshare_subscription"></a> Pour créer un abonnement pour un partage de fichiers  
  
1. Naviguez vers [le portail web d’un serveur de rapports (Mode natif SSRS)](../../reporting-services/web-portal-ssrs-native-mode.md).  
  
2.  Naviguez vers le rapport souhaité. Cliquez avec le bouton de droite sur le rapport, puis sélectionnez **S’abonner**.  
  
3.  **Description** : Entrez une description de l’abonnement du rapport, 512 caractères maximum.  
  
4.  **Propriétaire** : La valeur par défaut du champ Propriétaire est l’utilisateur actuel et ne peut pas être modifiée lors de la création de l’abonnement. Toutefois, une fois l’abonnement enregistré, vous pouvez modifier les propriétés d’abonnement, notamment le propriétaire et la description.  

5. Sous **Type d’abonnement**, sélectionnez la case d’option **Abonnement Standard**.

6. Sous la section **Planification**, sélectionnez :  
   - **Planification partagée**.  
   - **Planification de rapport spécifique**.  

    Pour plus d'informations sur la planification, consultez [Planifications](../../reporting-services/subscriptions/schedules.md).
  
7. Sous **Destination**, sélectionnez **Partage de fichiers Windows**.  
  
8. Sous **options de Remise (partage de fichiers Windows)** , spécifiez :  
   - **Nom de fichier** : Spécifiez un nom de fichier pour le rapport.
   - **Ajouter une extension de fichier lorsque le fichier est créé** : Cette option ajoute une extension de trois caractères au nom de fichier. L'extension de fichier est déterminée par le format de sortie sélectionné pour le rapport.  
   - **Chemin d’accès** : Tapez un chemin d’accès UNC (Universal Naming Convention) menant à un dossier existant qui doit contenir les rapports (par exemple, \\<servername\>\<myreports>). Insérez deux barres obliques inverses au début du chemin d'accès. Ne spécifiez pas de barre oblique de fin.  
  
     ![abonnement au partage de fichiers](../../reporting-services/subscriptions/media/create-and-manage-subscriptions-for-native-mode-report-servers/subscription-file-share-delivery-option.png "abonnement au partage de fichiers")  
  
   - **Format du rendu** : Sélectionnez un format de sortie du rapport pour la remise de fichier. Choisissez un format qui correspond à l'application bureautique qui sera utilisée pour ouvrir le rapport. Évitez les formats qui n'effectuent pas le rendu d'un rapport en un seul flux ou qui introduisent une interactivité non prise en charge dans un fichier statique (par exemple le format HTML 4.0).  
  
   - **Informations d’identification** : Choisissez d’utiliser le compte Partage de fichiers ou des informations d'identification Windows spécifiques. L’option **Utiliser le compte Partage de fichiers** est désactivée si votre administrateur de rapports n’a pas configuré de compte de partage de fichiers. Pour plus d’informations, consultez [Paramètres d’abonnement et compte de partage de fichiers &#40;Gestionnaire de configuration&#41;](../../reporting-services/install-windows/subscription-settings-and-a-file-share-account-configuration-manager.md). Dans les zones de texte **Nom d’utilisateur** et **Mot de passe**, indiquez les informations d’identification nécessaires pour accéder au partage de fichiers en respectant le format *\<domaine>* \\ *\<nom_utilisateur>* pour le nom d’utilisateur.  
  
   - **Options de remplacement**  
     - **Remplacer un fichier existant par une version plus récente**.  
     - Avec**Ne pas remplacer le fichier si une version précédente existe**, vous empêchez la remise d'avoir lieu si un fichier existant est détecté.  
     - Avec**Incrémenter les noms des fichiers au fur et à mesure que des versions plus récentes sont ajoutées**, le serveur de rapports ajoute un numéro au nom du fichier pour le distinguer des fichiers existants qui portent le même nom.  

9. Pour les rapports paramétrables, spécifiez les paramètres à utiliser pour le rapport correspondant à cet abonnement. Les paramètres peuvent différer de ceux utilisés pour l'exécution du rapport à la demande ou de ceux mis en œuvre dans d'autres opérations planifiées.  
  
Le rapport est remis sous forme de fichier statique. Si le rapport comprend des fonctionnalités interactives (par exemple des liens vers des lignes et colonnes supplémentaires), ces fonctionnalités ne sont pas disponibles.  
  
###  <a name="bkmk_create_email_subscription"></a> Pour créer un abonnement par e-mail  
  
1. Naviguez vers [le portail web d’un serveur de rapports (Mode natif SSRS)](../../reporting-services/web-portal-ssrs-native-mode.md).  
  
2. Naviguez vers le rapport souhaité. Cliquez avec le bouton de droite sur le rapport, puis sélectionnez **S’abonner**.  
  
3. **Description** : Entrez une description de l’abonnement du rapport, 512 caractères maximum.  
  
4.  **Propriétaire** : La valeur par défaut du champ Propriétaire est l’utilisateur actuel et ne peut pas être modifiée lors de la création de l’abonnement. Toutefois, une fois l’abonnement enregistré, vous pouvez modifier les propriétés d’abonnement, notamment le propriétaire et la description.  

5. Sous **Type d’abonnement**, sélectionnez la case d’option **Abonnement Standard**.

6. Sous la section **Planification**, sélectionnez :  
   - **Planification partagée**.  
   - **Planification de rapport spécifique**.  

    Pour plus d'informations sur la planification, consultez [Planifications](../../reporting-services/subscriptions/schedules.md).
  
7. Sous **Destination**, sélectionnez **E-mail**.  Si l’option **E-mail** n’est pas disponible, votre serveur de rapports n’est pas configuré pour les abonnements par e-mail. Consultez [Configurer l’e-mail d’une application de service Reporting Services](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md).
  
8. Sous **options de Remise (E-Mail)** , spécifiez :
   - **À** : Le nom de destinataire figurant dans le champ À : est renseigné automatiquement d’après votre compte d’utilisateur de domaine. Vérifiez que le format est [nom d’utilisateur]@[domain.com]. Les paramètres de configuration du serveur de rapports déterminent si le champ **À** est renseigné automatiquement à l'aide de votre compte d'utilisateur. Pour plus d’informations sur la modification des paramètres de configuration pour les adresses électroniques, consultez [Configurer un e-mail pour une application des services de Reporting Services](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)

     >[!NOTE]  
     > En fonction de vos autorisations, vous pouvez taper l'adresse de messagerie à laquelle le rapport doit être remis. Si vous spécifiez plusieurs adresses, séparez-les par des points-virgules (;). Vous pouvez aussi taper des adresses e-mail supplémentaires dans les zones de texte **Cc**, **Cci**et **Répondre à** . Pour cela, vous devez disposer de l'autorisation de gestion de tous les abonnements.  
  
   - **Objet** : A pour valeur par défaut « @ReportName a été exécuté à @ExecutionTime ». Vous pouvez modifier l’objet, mais notez que @ReportName et @ExecutionTime sont les seules variables globales prises en charge dans le champ **Objet**.  
  
     ![abonnement e-mail](../../reporting-services/subscriptions/media/create-and-manage-subscriptions-for-native-mode-report-servers/subscription-e-mail-delivery-option.png "abonnement e-mail")  

   - **Inclure un rapport** : Sélectionnez cette option pour incorporer ou joindre un exemplaire du rapport. Le format du rapport est déterminé par le format de rendu sélectionné. Ne choisissez pas cette option si vous pensez que la taille du rapport peut dépasser la limite définie pour votre système de messagerie.  
  
   - **Inclure un lien** : Sélectionnez cette option pour insérer une URL pointant vers le rapport dans le corps de texte de l’e-mail.  
  
     >[!NOTE]  
     >Si vous désactivez ces deux options, seul le texte de notification de la ligne Objet est envoyé.  
  
   - Choisissez un format de rendu dans la zone de liste **Format du rendu** . Cette option est disponible si vous sélectionnez **Inclure un rapport** pour incorporer ou joindre une copie du rapport.  
      - Pour incorporer le rapport au corps du message électronique, sélectionnez **MHTML (Archive Web)** .  
      - Pour envoyer le rapport sous forme de pièce jointe, choisissez le format de rendu de votre choix.  
  
   - Dans la zone de liste **Priorité** , sélectionnez une priorité. Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange, ce paramètre définit un indicateur en rapport avec le niveau d’importance du message électronique.  
   - Entrez un **Commentaire** si vous le souhaitez.
  
9. Pour les rapports paramétrables, spécifiez les paramètres à utiliser pour le rapport correspondant à cet abonnement. Les paramètres spécifiés peuvent différer de ceux utilisés pour exécuter le rapport à la demande ou de ceux mis en œuvre dans les autres opérations planifiées.  
  
##  <a name="bkmk_modify_subscription"></a> Pour modifier un abonnement  
 Vous pouvez modifier un abonnement à tout moment. Lorsque vous modifiez un abonnement au cours de son traitement, les paramètres mis à jour sont utilisés s'ils sont enregistrés dans le serveur de rapports avant que l'extension de remise ne reçoive les données d'abonnement. Dans le cas contraire, les paramètres existants sont utilisés.  
  
 Un utilisateur qui crée un abonnement en est le propriétaire. Chaque utilisateur peut modifier ou supprimer les abonnements qu'il possède. Vous pouvez modifier le propriétaire du rapport à partir de la page des propriétés d’abonnement ou dans le programme. Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Utiliser PowerShell pour modifier et répertorier les propriétaires d’abonnements Reporting Services, et exécuter un abonnement](../../reporting-services/subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)  
  
-   <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A>  
  
 Pour localiser un abonnement, utilisez la page **Mes abonnements** ou affichez les définitions d'abonnement associées à un rapport. Vous ne pouvez pas rechercher directement les abonnements, pas plus que vous ne pouvez rechercher un abonnement par nom de propriétaire, informations de déclencheur, informations d'état, etc.  
  
 Les abonnements peuvent également être modifiés ou supprimés par les administrateurs des serveurs de rapports.  
  
>[!NOTE]  
> Un administrateur de serveur de rapports ne peut pas centraliser la gestion de tous les abonnements individuels en cours d'utilisation sur un serveur de rapports donné. Il peut toutefois accéder à chaque abonnement pour le modifier ou le supprimer.  
  
##  <a name="bkmk_delete_subscription"></a> Pour supprimer un abonnement  
Pour supprimer un abonnement :  
  
1. Naviguez vers [le portail web d’un serveur de rapports (Mode natif SSRS)](../../reporting-services/web-portal-ssrs-native-mode.md).  
  
2. Dans le portail web, sélectionnez **Mes abonnements** dans la barre d'outils et naviguez jusqu'à l'abonnement à modifier ou à supprimer.  
  
3. Cliquez avec le bouton de droite sur le rapport, puis sélectionnez **Supprimer**.  
  
Pour annuler un abonnement qui est en cours de traitement sur le serveur de rapports, consultez [Gérer un processus en cours d’exécution](../../reporting-services/subscriptions/manage-a-running-process.md).  
  
 Si vous voulez mettre fin à un abonnement et si vous n'arrivez pas à le localiser, prenez note du rapport que vous recevez et faites une recherche sur son nom. Une fois que vous accédez au rapport, vous pouvez vous retirer de l'abonnement. Si vous n'arrivez pas à localiser l'abonnement, celui-ci est peut-être de type piloté par les données. Pour plus d'informations, contactez l'administrateur de votre serveur de rapports.  
  
 Un abonnement est supprimé automatiquement lorsque le rapport sous-jacent est supprimé. Si vous supprimez un abonnement lors de son traitement, l'abonnement s'arrête lorsque la suppression intervient avant que l'extension de remise n'ait reçu les données d'abonnement. Dans le cas contraire, le traitement de l'abonnement se poursuit.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer et gérer des abonnements pour les serveurs de rapports en mode Sharepoint](../../reporting-services/subscriptions/create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md)  
 [Utiliser PowerShell pour modifier et répertorier les propriétaires d’abonnements Reporting Services, et exécuter un abonnement](../../reporting-services/subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)  
 [Abonnements pilotés par les données](../../reporting-services/subscriptions/data-driven-subscriptions.md)  
 [Abonnements et remise &#40;Reporting Services&#41;](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)  
 [Le portail web d’un serveur de rapports (Mode natif SSRS)](../../reporting-services/web-portal-ssrs-native-mode.md)  
 [Utiliser Mes abonnements &#40;serveur de rapports en mode natif&#41;](../../reporting-services/subscriptions/use-my-subscriptions-native-mode-report-server.md)  
  