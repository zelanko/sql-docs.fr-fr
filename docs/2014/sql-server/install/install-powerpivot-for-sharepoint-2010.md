---
title: Installer PowerPivot pour SharePoint 2010 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: eec38696-5e26-46fa-bc83-aa776f470ce8
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: b7d478761a1051114e0189c7fd11eddafcef086b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "78172339"
---
# <a name="install-powerpivot-for-sharepoint-2010"></a>Installer PowerPivot pour SharePoint 2010
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] est une collection de services de couche intermédiaire et de services principaux qui fournissent l'accès aux données PowerPivot dans une batterie de serveurs SharePoint 2010. Si votre organisation utilise l'application cliente, [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour Excel 2010, pour créer des classeurs qui contiennent des données analytiques, vous devez disposer de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] pour accéder à ces données dans un environnement serveur. Cette rubrique vous guide tout au long de la procédure d'installation de base et propose des liens vers des rubriques supplémentaires pour vous aider à configurer PowerPivot.

||
|-|
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010|

 

 Pour obtenir des instructions sur l' [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de et sur le même serveur, consultez [liste de vérification du déploiement : Reporting Services, Power View et PowerPivot pour SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md).

## <a name="prerequisites"></a>Prérequis

1.  Vous devez être administrateur local pour exécuter le programme d'installation de SQL Server.

2.  SharePoint Server 2010 Enterprise Edition est requis pour [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. Vous pouvez également utiliser l'édition Enterprise Evaluation.

3.  SharePoint Server 2010 SP2 doit être installé. Sans lui, vous ne pouvez pas configurer la batterie de serveurs pour utiliser les fonctionnalités de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .

4.  L'ordinateur doit être attaché à un domaine.

5.  Vous devez avoir un compte d'utilisateur de domaine pour configurer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Dans une installation de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] , le compte de service Analysis Services doit être un compte d'utilisateur de domaine afin de le gérer à partir de l'Administration centrale. Vous allez saisir le compte et les informations d'identification sur la page **Configuration du serveur** dans le cadre de la procédure décrite dans ce document.

6.  Le nom de l'instance [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] doit être disponible. Vous ne pouvez pas avoir une instance nommée existante [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sur l'ordinateur d'installation de PowerPivot pour SharePoint.

7.  L'instance [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] ne peut pas faire partie d'un cluster de basculement SQL Server. Utilisez les fonctionnalités haute disponibilité du produit SharePoint. Par exemple, Excel Services gère l'équilibrage de charge de plusieurs serveurs PowerPivot pour SharePoint. Pour plus d’informations, consultez [gérer les paramètres de modèle de données Excel Services (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx) (https://technet.microsoft.com/library/jj219780.aspx).

8.  Si vous installez [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] sur une batterie de serveurs existante, vous devez avoir une ou plusieurs applications Web SharePoint configurées pour l'authentification en mode classique. L'accès aux données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] fonctionne uniquement si l'application Web prend en charge l'authentification en mode classique. Pour plus d'informations sur les exigences du mode classique, consultez [PowerPivot Authentication and Authorization](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-authentication-and-authorization).

9. Consultez les rubriques supplémentaires suivantes pour comprendre les exigences du système et des versions :

    -   [Instructions d'utilisation des fonctionnalités BI de SQL Server dans une batterie de serveurs SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)

##  <a name="step-1-install-powerpivot-for-sharepoint"></a><a name="InstallSQL"></a>Étape 1 : installer PowerPivot pour SharePoint
 Dans cette étape, vous exécutez le programme d'installation de SQL Server pour installer [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. Dans une étape suivante, vous configurerez le serveur en tant que tâche consécutive à l'installation.

1.  Insérez le support d'installation ou ouvrez un dossier qui contient les fichiers d'installation de SQL Server, puis double-cliquez sur **setup.exe**.

2.  Cliquez sur **Installation** dans le volet de navigation gauche.

3.  Cliquez sur **Nouvelle installation autonome SQL Server ou ajout de fonctionnalités à une installation existante**.

4.  Dans la page **Clé de produit** , indiquez l'édition d'évaluation ou entrez une clé de produit pour une copie sous licence de l'édition entreprise.

     Cliquez sur **Suivant**.

5.  Acceptez les conditions du contrat de licence logiciel Microsoft. Nous vous serions également reconnaissants si vous pouviez également activer la création de rapports d'erreurs et de rapports sur l'expérience utilisateur. Cliquez sur **Suivant**.

6.  Mettez à jour les fichiers d'installation si vous êtes invité à le faire.

7.  Sur la page **Règles d'installation** , le programme d'installation identifie tous les problèmes susceptibles d'empêcher l'installation. Examinez la liste pour déterminer si le programme d'installation a détecté des problèmes potentiels sur le système.

    > [!NOTE]
    >  Puisque le Pare-feu Windows est activé, un avertissement vous indiquera d'ouvrir les ports pour permettre l'accès à distance. En règle générale, cet avertissement ne s'applique pas aux installations [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Les connexions aux services et aux fichiers de données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sont établies à l'aide des ports SharePoint qui sont déjà ouverts pour la communication entre services de SharePoint.

     Cliquez sur **Suivant**. Attendez la fin de l'installation des fichiers programme d'installation de SQL Server sur le serveur.

8.  Dans la page **Rôle d'installation** , sélectionnez **SQL Server PowerPivot pour SharePoint**.

9. Éventuellement, vous pouvez ajouter une instance du moteur de base de données à votre installation. Vous pouvez effectuer cette opération si vous configurez une nouvelle batterie de serveurs et que vous avez besoin d’un serveur de base de données pour exécuter la configuration et les bases de données de contenu de la batterie de serveurs. SI vous ajoutez le moteur de base de données, il sera installé en tant qu'instance nommée PowerPivot. Chaque fois que vous devez spécifier une connexion à cette instance (par exemple, dans l’Assistant Configuration de batterie de serveurs si vous utilisez cet Assistant pour configurer la batterie), entrez le nom de la base `servername` de données au format suivant : <> \powerpivot.

     ![GMNI_SetupUI_FeatureRole](../../../2014/sql-server/install/media/gmni-setupui-featurerole.gif "GMNI_SetupUI_FeatureRole")

10. Cliquez sur **Suivant**.

11. Dans la page **Sélection de fonctionnalités** , une liste en lecture seule des fonctionnalités qui seront installées est affichée à titre d'information. Vous ne pouvez pas ajouter ou supprimer des éléments présélectionnés pour ce rôle. Cliquez sur **Suivant**.

12. Sur la page **Règles de fonctionnalité** , cliquez sur **Suivant**. Cette page peut être ignorée.

13. Dans la page **Configuration de l'instance** , un nom d'instance en lecture seule de PowerPivot est affiché à titre d'information. Le nom d'instance de **POWERPIVOT** est **obligatoire et ne peut pas être modifié**. Toutefois, vous pouvez entrer un ID d'instance unique pour spécifier un nom de répertoire descriptif et des clés de Registre. Cliquez sur **Suivant**.

14. Dans la page **Configuration du serveur** , entrez les informations de compte appropriées.

     Pour SQL Server Analysis Services, vous devez spécifier un compte d'utilisateur de domaine. Ne spécifiez pas un compte intégré. Les comptes de domaine sont requis pour gérer le compte de service Analysis Services comme un *compte géré* dans l'Administration centrale de SharePoint.

     ![Configuration de SSAS Server](../../../2014/sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "Configuration de SSAS Server")

     Si vous avez ajouté le Moteur de base de données SQL Server et l'Agent SQL Server, vous pouvez configurer les services à exécuter sous des comptes d'utilisateur de domaine ou sous un compte virtuel par défaut.

     N'utilisez jamais votre propre compte d'utilisateur de domaine pour configurer un service. Cela aurait pour conséquence d'accorder aux ressources du réseau les mêmes autorisations que celles dont vous bénéficiez. Si le serveur était compromis par un utilisateur malveillant, cet utilisateur se connecterait sous vos informations d'identification de domaine, pouvant ainsi télécharger ou utiliser les mêmes données et applications que vous.

15. Cliquez sur **Suivant**.

16. Si vous installez le moteur de base de données, la page Configuration du moteur de base de données s'affiche. Dans Configuration du moteur de base de données, cliquez sur **Ajouter l'utilisateur actuel** pour accorder vos autorisations d'administrateur de compte d'utilisateur sur l'instance du moteur de base de données. Cliquez sur **Ajouter** pour ajouter des comptes supplémentaires. Cliquez sur **Suivant**.

17. Dans la page **Configuration d'Analysis Services** , cliquez sur **Ajouter l'utilisateur actuel** pour accorder vos autorisations administratives au compte d'utilisateur. Vous devrez avoir des autorisations d'administrateur pour configurer le serveur une fois l'installation terminée.

18. Dans la même page, ajoutez le compte d'utilisateur Windows de toute personne qui a aussi besoin d'autorisations d'administration. Par exemple, tout utilisateur qui souhaite se connecter à l'instance du [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] dans SQL Server Management Studio, pour résoudre des problèmes de connexion de base de données ou obtenir des informations sur la version, doit avoir des autorisations d'administrateur système sur le serveur. Ajoutez le compte d'utilisateur de toute personne susceptible de devoir dépanner ou administrer le serveur.

19. Cliquez sur **Suivant**.

20. Cliquez sur **Suivant** dans chacune des pages restantes, jusqu'à atteindre la page Prêt pour l'installation.

21. Cliquez sur **Installer**.

> [!TIP]
>  Si vous devez dépanner l'installation de SQL Server, consultez [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).

##  <a name="step-2-configure-the-server"></a><a name="bkmk_config"></a>Étape 2 : configurer le serveur

> [!IMPORTANT]
>  SharePoint 2010 SP2 doit être installé avant de pouvoir configurer [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] ou une batterie de serveurs SharePoint qui utilise un serveur de base de données [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Si vous n'avez pas encore installé le Service Pack, faites-le maintenant avant de commencer la configuration du serveur.

 L'installation n'est pas terminée tant que le serveur n'est pas configuré. Dans cette version, la configuration du serveur est toujours effectuée comme une tâche consécutive à l'installation, en utilisant l'une des approches suivantes : Outil de configuration de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , Administration centrale ou PowerShell. Pour continuer, choisissez l'une des méthodes suivantes :

-   [Configurez ou réparez PowerPivot pour SharePoint 2010 &#40;outil de configuration de PowerPivot&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md)

-   [Administration et configuration d’un serveur PowerPivot dans l’Administration centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration)

-   [Configuration de PowerPivot à l’aide de Windows PowerShell](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell)

 **Connexion à l'instance du moteur de base de données** Lorsque vous avez installé [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], le programme d'installation de SQL Server vous a donné la possibilité d'ajouter une instance du moteur de base de données à votre installation. Vous avez peut-être ajouté une instance de Moteur de base de données à votre installation si vous configurez une nouvelle batterie de serveurs et que vous avez besoin d’un serveur de base de données pour exécuter la configuration et les bases de données de contenu de la batterie de serveurs. Si vous avez ajouté le moteur de base de données, il a été installé en tant qu'instance nommée [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Chaque fois que vous devez spécifier une connexion à cette instance (par exemple, dans l’Assistant Configuration de batterie de serveurs si vous utilisez cet Assistant pour configurer la batterie), n’oubliez pas d’entrer le nom de `servername` la base de données au format suivant : <> \powerpivot.

##  <a name="step-3-install-analysis-services-ole-db-providers-on-excel-services-application-servers"></a><a name="bkmk_redist"></a>Étape 3 : installer les fournisseurs de OLE DB Analysis Services sur les serveurs d’applications Excel Services
 Des étapes de configuration supplémentaires sont requises si vous exécutez les services de calcul Excel et [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sur des serveurs d'applications distincts. Sur les serveurs d'applications exécutant les services de calcul Excel, installez la version appropriée du fournisseur OLE DB Analysis Services (MSOLAP).

-   La version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de MSOLAP est incluse dans le programme d'installation de SQL Server ; par conséquent, l'installation explicite de la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de MSOLAP n'est nécessaire que si votre serveur d'applications n'est pas un serveur d'applications PowerPivot.

    > [!NOTE]
    >  Le serveur d'applications des services de calcul Excel a également besoin d'une instance du fichier **Microsoft.AnalysisServices.Xmla.dll** dans l'assembly global. Pour installer le fichier .dll sur le serveur d'applications, installez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Sélectionnez « outils de gestion-terminés » sur la page **sélection de fonctionnalités** de l’Assistant installation de SQL Server.

-   Si vous souhaitez que le serveur d'applications prenne en charge les classeurs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] antérieurs, vous devez installer la version SQL Server 2008 R2 de MSOLAP.

 Pour plus d'informations sur l'installation du fournisseur, y compris les étapes de vérification, consultez [Install the Analysis Services OLE DB Provider on SharePoint Servers](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).

##  <a name="step-4-verify-the-installation"></a><a name="bkmk_verify"></a>Étape 4 : vérifier l’installation
 Au cours de cette dernière étape, vous allez vérifier que SharePoint 2010 et [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] sont complètement fonctionnels. Pour obtenir des instructions, consultez [Verify a PowerPivot for SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation).

## <a name="see-also"></a>Voir aussi
 Liste de vérification du déploiement de [l’installation de PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md) [: Reporting Services, Power View et PowerPivot pour SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) [liste de vérification du déploiement : montée en puissance parallèle en ajoutant des serveurs PowerPivot à la](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md) [liste de vérification du déploiement d’une batterie de serveurs SharePoint 2010 : installation multiserveur de PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/deployment-checklist-multiserver-installation-powerpivot-sharepoint-2010.md)


