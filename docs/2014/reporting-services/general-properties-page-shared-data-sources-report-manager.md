---
title: Page propriétés générales, partagé des Sources de données (Gestionnaire de rapports) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b344449-6f7c-47d2-a737-972d88c0faf8
caps.latest.revision: 29
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 0a570567691692f008f6f71966b5ee0b01921dab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043544"
---
# <a name="general-properties-page-shared-data-sources-report-manager"></a>Page Propriétés générales, Sources de données partagées (Gestionnaire de rapports)
  La page Propriétés générales vous permet d'afficher ou de modifier les propriétés d'un élément de source de données partagée. Toutes les modifications que vous apportez aux propriétés sont prises en compte pour tous les rapports qui font référence à l'élément lorsque vous cliquez sur **Appliquer**.  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-general-properties-page-for-a-shared-data-source"></a>Pour ouvrir la page Propriétés générales pour une source de données partagée  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez la source de données partagée pour laquelle vous souhaitez consulter des propriétés.  
  
2.  Pointez sur la source de données et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**. Ainsi, vous ouvrez la page des propriétés générales pour la source de données partagée.  
  
## <a name="options"></a>Options  
 **Nom**  
 Spécifie le nom de la source de données partagée qui est utilisé pour identifier l'élément dans l'espace de noms du serveur de rapports.  
  
 **Description**  
 Fournit des informations sur la source de données partagée. Cette description apparaît dans la page Contenu.  
  
 **Masquer en mode liste**  
 Activez cette option pour masquer la source de données partagée pour les utilisateurs qui utilisent le mode de visualisation sous forme de listes dans le Gestionnaire de rapports. Le mode Liste est le format d'affichage par défaut lorsque vous parcourez l'arborescence des dossiers du serveur de rapports. En mode Liste, les noms et les descriptions des éléments sont affichés sur la largeur de la page. Un autre format d'affichage, le mode Détails, est également disponible. En mode Détails, les descriptions ne sont pas affichées, mais cette vue fournit d'autres informations sur l'élément. Vous pouvez masquer un élément en mode Liste, mais pas en mode Détails. Pour restreindre l'accès à un élément, vous devez créer une attribution de rôle.  
  
 **Activer cette source de données**  
 Sélectionnez cette option pour activer ou désactiver la source de données partagée. Vous pouvez désactiver la source de données partagée pour empêcher le traitement des rapports, des modèles de rapport et des abonnements pilotés par les données qui font référence à l'élément.  
  
 **Type de source de données**  
 Spécifie l'extension pour le traitement des données utilisée pour traiter les données de la source de données. Le serveur de rapports inclut des extensions de traitement des données pour [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], Oracle, XML, SAP, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], ODBC et OLE DB. Des extensions supplémentaires peuvent être disponibles auprès d'éditeurs tiers.  
  
 Notez que, si vous utilisez [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] Edition with Advanced Services, vous ne pouvez choisir que des sources de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **Chaîne de connexion**  
 Spécifiez la chaîne de connexion utilisée par le serveur de rapports pour se connecter à la source de données. Le type de connexion détermine la syntaxe à utiliser. Par exemple, une chaîne de connexion pour une extension pour le traitement des données XML est une URL vers un document XML. Dans la plupart des cas, une chaîne de connexion type spécifie le serveur de bases de données et un fichier de données. L’exemple suivant illustre une chaîne de connexion utilisée pour se connecter à la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] base de données :  
  
```  
data source=<a SQL Server instance>;initial catalog=AdventureWorks2012  
```  
  
 **Se connecter à l’aide de**  
 Spécifie les options qui déterminent de quelle façon les informations d'identification sont obtenues.  
  
> [!IMPORTANT]  
>  Si les informations d'identification sont fournies dans la chaîne de connexion, les options et les valeurs indiquées dans cette section sont ignorées. Notez que si vous spécifiez les informations d'identification sur la chaîne de connexion, les valeurs sont affichées en texte en clair et sont visibles par tous les utilisateurs qui affichent cette page.  
  
 **Informations d’identification fournies par l’utilisateur qui exécute le rapport**  
 Chaque utilisateur doit fournir un nom d'utilisateur et un mot de passe pour accéder à la source de données. Vous pouvez définir le texte de l'invite qui demande les informations d'identification aux utilisateurs. La chaîne de texte par défaut est la suivante : « Entrer un nom d'utilisateur et un mot de passe pour accéder à la source de données ».  
  
 Activez la case à cocher **Utiliser en tant qu’informations d’identification Windows lors de la connexion à la source de données** si les informations d’identification fournies par l’utilisateur sont des informations d’identification de l’authentification Windows. N'activez pas cette case à cocher si vous utilisez une authentification par base de données, telle qu'une authentification SQL Server.  
  
 **Informations d’identification stockées en sécurité dans le serveur de rapports**  
 Stocke un nom d'utilisateur et un mot de passe chiffrés dans la base de données du serveur de rapports. Sélectionnez cette option pour exécuter un rapport sans assistance (par exemple, des rapports qui sont démarrés par des planifications ou des événements au lieu des actions utilisateur). Si vous utilisez la sécurité par défaut, le nom d'utilisateur doit être un compte de domaine Windows. Spécifiez le compte sous ce format : \<domaine >\\< nom d’utilisateur\>. Le compte que vous spécifiez doit disposer d'autorisations d'ouverture d'une session locale sur l'ordinateur qui héberge la source de données utilisée par le rapport.  
  
 Activez la case à cocher **Utiliser en tant qu'informations d'identification Windows lors de la connexion à la source de données** si les informations d'identification sont des informations d'identification de l'authentification Windows. Ne sélectionnez pas cette case à cocher si vous utilisez l’authentification de base de données (par exemple, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] authentification).  
  
 Si vous utilisez l'authentification dans la base de données, sélectionnez **Emprunter l'identité de l'utilisateur authentifié une fois la connexion établie à la source de données (Se connecter avec)** pour autoriser la délégation des informations d'identification de la base de données, mais uniquement si un serveur de base de données prend en charge l'emprunt d'identité. Pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bases de données, cette option définit la fonction SETUSER.  
  
 **Sécurité intégrée de Windows**  
 Utilise les informations d'identification Windows de l'utilisateur actuel pour accéder à la source de données. Sélectionnez cette option lorsque les informations d'identification utilisées pour accéder à la source de données sont identiques à celles utilisées pour ouvrir une session sur le domaine réseau. Cette option est plus adaptée lorsque Kerberos est activé pour votre domaine ou que la source de données se trouve sur le même ordinateur que le serveur de rapports. Si Kerberos n'est pas activé, les informations d'identification Windows peuvent être transmises à un autre ordinateur. Si des connexions supplémentaires à des ordinateurs sont requises, vous obtiendrez une erreur à la place des données attendues.  
  
 Un administrateur du serveur de rapports peut désactiver l'utilisation de la sécurité intégrée de Windows pour accéder aux sources de données de rapports. Si cette valeur est grisée, la fonctionnalité n'est pas disponible.  
  
 N'utilisez pas cette option si vous projetez de planifier ce rapport ou de vous y abonner. Le traitement de rapports sans assistance ou planifié requiert des informations d'identification qui peuvent être obtenues sans entrée d'utilisateur ou le contexte de sécurité d'un utilisateur actuel. Seules les informations d'identification stockées fournissent cette fonction. Pour cette raison, le serveur de rapports vous empêche de planifier le traitement d'un rapport ou d'un abonnement si le rapport est configuré pour le type d'informations d'identification de sécurité intégrée de Windows. Si vous choisissez cette option pour un rapport qui fait déjà l'objet d'un abonnement ou pour lequel des opérations sont planifiées, les abonnements et opérations planifiées s'arrêteront.  
  
 **Informations d’identification ne sont pas requises**  
 Spécifie que les informations d'identification ne sont pas requises pour accéder à la source de données. Notez que si la source de données nécessite une ouverture de session d'utilisateur, cette option est sans effet. Vous devez choisir cette option uniquement si la connexion de source de données ne nécessite pas d'informations d'identification des utilisateurs.  
  
 Pour utiliser cette option, vous devez avoir configuré précédemment le compte d'exécution sans assistance pour le déploiement du serveur de rapports. Le compte d'exécution sans assistance est utilisé pour se connecter aux sources de données externes lorsque les autres sources d'informations d'identification ne sont pas disponibles. Si vous spécifiez cette option et que le compte n'est pas configuré, la connexion à la source de données de rapports échouera et le traitement de rapports ne se produira pas. Pour plus d’informations sur ce compte, consultez [configurer le compte d’exécution sans assistance &#40;Gestionnaire de Configuration de SSRS&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
 **Appliquer**  
 Cliquez pour enregistrer vos modifications.  
  
 **Supprimer**  
 Cliquez pour supprimer la source de données partagée. La suppression d'une source de données partagée désactive les rapports, les modèles et les abonnements pilotés par les données qui l'utilisent. Pour réactiver les rapports, les modèles et les abonnements, vous devez ouvrir chacun d'eux et mettre à jour les propriétés de la source de données correspondante afin d'utiliser une source de données partagée différente. Pour les rapports et les abonnements, vous pouvez spécifier les informations de connexion à la source de données sous la forme de valeurs de propriétés Source de données.  
  
 **Déplacer**  
 Cliquez pour déplacer la source de données partagée vers un emplacement différent dans l'espace de noms du dossier du serveur de rapports.  
  
 **Générer le modèle**  
 Cliquez pour créer un modèle basé sur la source de données partagée.  
  
## <a name="see-also"></a>Voir aussi  
 [Le Gestionnaire de rapports &#40;SSRS en Mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Page Nouvelle source de données &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/new-data-source-page-report-manager.md)   
 [Aide (F1) de gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)   
 [Spécifier des informations d'identification et de connexion pour les sources de données de rapports](report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  