---
title: Page nouvel abonnement ou modifier l’abonnement (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e02d6529-ce67-4305-b7f0-433997e99c21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 968362b2835c0e76f2a44c44e6cd427af863e8e4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108138"
---
# <a name="new-subscription-or-edit-subscription-page-report-manager"></a>Page Nouvel abonnement ou Modifier l’abonnement (Gestionnaire de rapports)
  La page Nouvel abonnement ou Modifier l'abonnement permet de créer un abonnement ou de modifier un abonnement existant à un rapport. Les options de cette page varient selon votre attribution de rôle. Les utilisateurs qui possèdent des autorisations avancées peuvent utiliser des options supplémentaires.  
  
 Les abonnements sont pris en charge pour les rapports qui peuvent s'exécuter sans assistance. Les rapports doivent utiliser au minimum des informations d'identification stockées ou aucune information d'identification. Si le rapport utilise des paramètres, une valeur par défaut doit être spécifiée. Les abonnements peuvent devenir inactifs si vous modifiez les paramètres d'exécution de rapport ou que vous supprimez les valeurs par défaut utilisées par les propriétés de paramètres. Pour plus d’informations, consultez [Créer et gérer des abonnements pour les serveurs de rapports en mode natif](../../2014/reporting-services/create-manage-subscriptions-native-mode-report-servers.md).  
  
> [!NOTE]  
>  Cette fonctionnalité n'est pas disponible dans toutes les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
### <a name="to-open-the-new-subscription-or-edit-subscription-page"></a>Pour ouvrir la page Nouvel abonnement ou Modifier l'abonnement  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le rapport pour lequel vous souhaitez ajouter un abonnement.  
  
2.  Pointez sur le rapport et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, effectuez l'une des opérations suivantes :  
  
    -   Cliquez sur **Gérer**. La page des propriétés générales pour le rapport s'ouvre. Sélectionnez ensuite l’onglet **abonnements** . Dans la barre d’outils, cliquez sur **nouvel abonnement**ou sélectionnez un abonnement existant, puis cliquez sur **modifier**.  
  
    -   Cliquez sur **S'abonner**. Ainsi, vous ouvrez la page **Nouvel abonnement** pour le rapport.  
  
## <a name="options"></a>Options  
 **Remis par**  
 Sélectionnez l'extension de remise à utiliser pour distribuer le rapport. Selon l'extension de remise choisie, les paramètres suivants s'affichent :  
  
-   Les abonnements par messagerie contiennent des champs qui sont familiers aux utilisateurs de messagerie (les champs **À**, **Objet**et **Priorité** , par exemple). Spécifiez **Inclure un rapport** pour incorporer ou joindre le rapport, ou **Inclure un lien** pour inclure une URL dans le rapport. Sélectionnez **Format du rendu** pour choisir un format de présentation pour le rapport joint ou incorporé.  
  
-   Les abonnements aux partages de fichiers fournissent des champs qui vous permettent de spécifier un emplacement cible. Vous pouvez remettre n'importe quel rapport dans un partage de fichiers. Toutefois, les rapports qui prennent en charge des fonctionnalités interactives (notamment les rapports de matrice qui prennent en charge l'extraction vers le bas pour les lignes et les colonnes) sont rendus sous forme de fichiers statiques. Vous ne pouvez pas afficher les lignes et les colonnes extraites d'un fichier statique. Le nom du partage de fichiers doit être spécifié au format UNC (Uniform Naming Convention) (par \\exemple, \mycomputer\public\myreportfiles). N'incluez pas de barre oblique inverse à la fin du chemin d'accès. Le fichier de rapport sera remis dans un format de fichier qui est basé sur le format de rendu (si vous choisissez **Excel**, par exemple, le fichier sera remis en tant que fichier .xls).  
  
 La disponibilité d'une extension de remise varie selon qu'elle est installée et configurée sur le serveur de rapports. La messagerie Report Server est l'extension de remise par défaut, mais elle doit être configurée avant de pouvoir être utilisée. La remise de partage de fichiers ne requiert aucune configuration, mais vous devez définir un dossier partagé pour pouvoir l'utiliser.  
  
## <a name="subscription-processing-options"></a>Options de traitement d'abonnement  
 Utilisez ces paramètres pour définir les conditions qui entraînent le traitement d'un abonnement. Certaines des options sont disponibles uniquement pour les rapports qui utilisent des paramètres ou qui s'exécutent en tant qu'instantanés d'exécution de rapport.  
  
 **Lorsque le contenu du rapport est actualisé**  
 Sélectionnez cette option pour vous abonner à un instantané de rapport qui est actualisée suivant une planification. Cette option est visible uniquement lorsque vous vous abonnez à un rapport qui s'exécute en tant qu'instantané d'exécution de rapport. Le contenu d'un instantané d'exécution de rapport est généralement actualisé suivant une planification. Pour les rapports qui s'exécutent dans ce mode, vous pouvez définir qu'un abonnement se produit lorsque l'instantané est actualisé.  
  
 **Lorsque l'exécution planifiée du rapport est terminée**  
 Créer une planification qui détermine à quel moment l'abonnement est traité.  
  
 **Suivant une planification partagée**  
 Sélectionnez une planification prédéfinie pour traiter l'abonnement.  
  
 **Entrer des valeurs de paramètres**  
 Utilisez cette option lorsque vous vous abonnez à un rapport qui contient des paramètres. Cette option est disponible uniquement pour les rapports paramétrés. Lors de l'abonnement à un rapport paramétré, vous pouvez spécifier les valeurs de paramètres utilisées pour créer la version du rapport qui est remis via l'abonnement. Par exemple, vous pouvez spécifier un code de région pour sélectionner les données des ventes relatives à une région en particulier. Si vous ne spécifiez aucune valeur, la valeur par défaut est utilisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un serveur de rapports pour la remise par messagerie &#40;SSRS Configuration Manager&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md)   
 [Aide F1 du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
