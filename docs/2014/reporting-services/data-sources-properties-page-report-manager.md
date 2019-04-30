---
title: Sources de données Page de propriétés (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: f37edda0-19e6-489e-b544-8751fa6b6cfb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 00bc66f116a489858d6383d90a17e730792e6325
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63165361"
---
# <a name="data-sources-properties-page-report-manager"></a>Page des propriétés des sources de données (Gestionnaire de rapports)
  La page de propriétés des sources de données permet de définir la connexion du rapport actif à une source de données externe. Vous pouvez remplacer les informations de connexion à la source de données publiées à l'origine avec le rapport. Si plusieurs sources de données sont utilisées avec un rapport, chacune d'elles possède sa propre section dans la page de propriétés. Les sources de données sont répertoriées dans l'ordre dans lequel elles sont définies dans le rapport.  
  
 Lors de la spécification de la source de données à utiliser avec le rapport, vous pouvez choisir une source de données partagée qui est créée et gérée séparément des rapports qui l'utilisent. Si vous ne souhaitez pas utiliser un élément de source de données partagée, vous pouvez définir une connexion à la source de données à utiliser avec le rapport.  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
### <a name="to-open-the-data-sources-properties-page"></a>Pour ouvrir la page de propriétés Sources de données  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le rapport pour lequel vous souhaitez sélectionner une source de données.  
  
2.  Pointez sur le rapport et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**. La page des propriétés **générales** pour le rapport s'ouvre.  
  
4.  Sélectionnez l'onglet **Sources de données** .  
  
## <a name="options"></a>Options  
 **Une source de données partagée**  
 Spécifie une source de données partagée à utiliser avec un rapport. Pour plus d’informations sur la création d’une source de données, consultez [créer, supprimer ou modifier une Source de données partagée &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md).  
  
 **Parcourir**  
 Cliquez sur **Parcourir** pour ouvrir la page de sélection de la source de données qui permet de sélectionner une source de données partagée. Pour plus d’informations, consultez [Page de sélection de Source de données &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/data-source-selection-page-report-manager.md).  
  
 **Source de données personnalisée**  
 Spécifie la façon dont le rapport se connecte à la source de données.  
  
 Les options suivantes permettent de spécifier une connexion à une source de données personnalisée.  
  
 **Type de source de données**  
 Spécifiez l'extension pour le traitement des données utilisée pour traiter les données de la source de données. Pour la liste des extensions de données intégrées, consultez [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md). Des extensions supplémentaires peuvent être disponibles auprès d'éditeurs tiers.  
  
 **Chaîne de connexion**  
 Spécifiez la chaîne de connexion utilisée par le serveur de rapports pour se connecter à la source de données. Le type de connexion détermine la syntaxe à utiliser. Par exemple, une chaîne de connexion pour une extension pour le traitement des données XML est une URL vers un document XML. Dans la plupart des cas, une chaîne de connexion type spécifie le serveur de bases de données et un fichier de données. L'exemple suivant illustre une chaîne de connexion à la base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] appelée MyData :  
  
 `data source=<a SQL Server instance>;initial catalog=MyData`  
  
 Une chaîne de connexion peut être configurée sous la forme d'une expression pour vous permettre de spécifier la source de données lors de l'exécution. Les expressions de sources de données sont définies dans le rapport du Concepteur de rapports. Les expressions de sources de données ne peuvent pas être définies, visualisées ou modifiées dans le Gestionnaire de rapports. Vous pouvez toutefois remplacer une expression de source de données en cliquant sur **Remplacer l'option par défaut** pour entrer une chaîne de connexion statique. Pour revenir à l'expression, cliquez sur **Revenir à la valeur par défaut**. Le serveur de rapports enregistre la chaîne de connexion initiale au cas où vous devriez la restaurer. Pour utiliser les expressions de sources de données, vous devez employer les informations de connexion à la source de données publiées à l'origine dans le rapport. Les sources de données partagées ne prennent pas en charge l'utilisation d'expressions dans la chaîne de connexion.  
  
 **Se connecter à l’aide de**  
 Spécifie les options qui déterminent de quelle façon les informations d'identification sont obtenues.  
  
> [!IMPORTANT]  
>  Si les informations d'identification sont fournies dans la chaîne de connexion, les options et les valeurs indiquées dans cette section sont ignorées. Notez que si vous spécifiez les informations d'identification sur la chaîne de connexion, les valeurs sont affichées en texte en clair et sont visibles par tous les utilisateurs qui affichent cette page.  
  
 **Informations d’identification fournies par l’utilisateur qui exécute le rapport**  
 Chaque utilisateur doit fournir un nom d'utilisateur et un mot de passe pour accéder à la source de données. Vous pouvez définir le texte de l'invite qui demande les informations d'identification aux utilisateurs. La chaîne de texte par défaut est la suivante : « Entrer un nom d'utilisateur et un mot de passe pour accéder à la source de données ».  
  
 Activez la case à cocher **Utiliser en tant qu’informations d’identification Windows lors de la connexion à la source de données** si les informations d’identification fournies par l’utilisateur sont des informations d’identification de l’authentification Windows. N'activez pas cette case à cocher si vous utilisez une authentification dans la base de données (par exemple, l'authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ).  
  
 **Informations d’identification stockées en toute sécurité dans le serveur de rapports**  
 Stocke un nom d'utilisateur et un mot de passe chiffrés dans la base de données du serveur de rapports. Sélectionnez cette option pour exécuter un rapport sans assistance (par exemple, des rapports qui sont démarrés par des planifications ou des événements au lieu des actions utilisateur). Si vous utilisez la sécurité par défaut, le nom d'utilisateur doit être un compte de domaine Windows. Spécifiez le compte sous ce format : \<domaine >\\< nom d’utilisateur\>. Le compte que vous spécifiez doit disposer d'autorisations d'ouverture d'une session locale sur l'ordinateur qui héberge la source de données utilisée par le rapport.  
  
 Activez la case à cocher **Utiliser en tant qu'informations d'identification Windows lors de la connexion à la source de données** si les informations d'identification sont des informations d'identification de l'authentification Windows. N'activez pas cette case à cocher si vous utilisez une authentification dans la base de données (par exemple, l'authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ).  
  
 Sélectionnez **Emprunter l'identité de l'utilisateur authentifié une fois la connexion établie à la source de données** pour autoriser la délégation des informations d'identification, mais uniquement si une source de données prend en charge l'emprunt d'identité. Pour les bases de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , cette option définit la fonction SETUSER.  
  
> [!TIP]  
>  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]prend en charge uniquement les informations d’identification du compte Windows. Sélectionnez donc les deux options Utiliser comme informations d'identification Windows lors de la connexion à la source de données et Emprunter l'identité de l'utilisateur authentifié une fois la connexion établie à la source de données pour une source de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 **Sécurité intégrée de Windows**  
 Utilise les informations d'identification Windows de l'utilisateur actuel pour accéder à la source de données. Sélectionnez cette option lorsque les informations d'identification utilisées pour accéder à la source de données sont identiques à celles utilisées pour ouvrir une session sur le domaine réseau. Cette option convient mieux lorsque l'authentification Kerberos est activée pour votre domaine ou que la source de données se trouve sur le même ordinateur que le serveur de rapports. Si Kerberos n'est pas activé, les informations d'identification Windows peuvent être transmises à un autre ordinateur. Si des connexions supplémentaires à des ordinateurs sont requises, vous obtiendrez une erreur à la place des données attendues.  
  
 Un administrateur du serveur de rapports peut désactiver l'utilisation de la sécurité intégrée de Windows pour accéder aux sources de données de rapports. Si cette valeur est grisée, la fonctionnalité n'est pas disponible.  
  
 N'utilisez pas cette option si vous projetez de planifier ce rapport ou de vous y abonner. Le traitement de rapports sans assistance ou planifié requiert des informations d'identification qui peuvent être obtenues sans entrée d'utilisateur ou le contexte de sécurité d'un utilisateur actuel. Seules les informations d'identification stockées fournissent cette fonction. Pour cette raison, le serveur de rapports vous empêche de planifier le traitement d'un rapport ou d'un abonnement si le rapport est configuré pour le type d'informations d'identification de sécurité intégrée de Windows. Si vous choisissez cette option pour un rapport qui fait déjà l'objet d'un abonnement ou pour lequel des opérations sont planifiées, les abonnements et opérations planifiées s'arrêteront.  
  
 **Informations d’identification ne sont pas requises**  
 Spécifie que les informations d'identification ne sont pas requises pour accéder à la source de données. Notez que si la source de données nécessite une ouverture de session d'utilisateur, cette option est sans effet. Vous devez choisir cette option uniquement si la connexion de source de données ne nécessite pas d'informations d'identification des utilisateurs.  
  
 Pour utiliser cette option, vous devez avoir configuré précédemment le compte d'exécution sans assistance pour le déploiement du serveur de rapports. Le compte d'exécution sans assistance est utilisé pour se connecter aux sources de données externes lorsque les autres sources d'informations d'identification ne sont pas disponibles. Si vous spécifiez cette option et que le compte n'est pas configuré, la connexion à la source de données de rapports échouera et le traitement de rapports ne se produira pas.  Pour plus d’informations sur ce compte, consultez [configurer le compte d’exécution sans assistance &#40;Gestionnaire de Configuration de SSRS&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
 **Appliquer**  
 Cliquez pour enregistrer vos modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer des sources de données de rapports](report-data/manage-report-data-sources.md)   
 [Spécifier des informations d'identification et de connexion pour les sources de données de rapport](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Aide (F1) du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
