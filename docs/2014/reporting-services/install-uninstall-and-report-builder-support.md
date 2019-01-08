---
title: Installer, désinstaller et prise en charge du Générateur de rapports | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- administering Report Builder
ms.assetid: 2c9a5814-17bf-4947-8fb3-6269e7caa416
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 216623bca9dbbc086a600578c174a60d1797a2f4
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53377511"
---
# <a name="install-uninstall-and-report-builder-support"></a>Installer, désinstaller et prendre en charge le Générateur de rapports
  Le Générateur de rapports est un outil de création de rapports permettant de créer, mettre à jour et partager des rapports, des parties de rapports et des datasets partagés. Le Générateur de rapports est disponible dans deux versions : autonome et [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. La version autonome est installée sur votre ordinateur par vos propres soins ou par un administrateur. La version [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] est installée automatiquement avec [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] et téléchargée sur votre ordinateur à partir du Gestionnaire de rapports ou d'un site SharePoint intégré à [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
 La version autonome du Générateur de rapports n'est pas installée avec [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Vous devez la télécharger et l'installer séparément à partir du [Générateur de rapports Microsoft® SQL Server® 2012](https://go.microsoft.com/fwlink/?LinkId=401502).  
  
> [!NOTE]  
>  Il n'est pas possible d'installer le Générateur de rapports sur des ordinateurs Itanium. Cela s'applique aux versions [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] et autonome du Générateur de rapports.  
  
 En règle générale, un administrateur installe et configure [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], et accorde l'autorisation d'utiliser la version [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] du Générateur de rapports ; en outre, il gère les dossiers et les autorisations d'accès aux rapports, parties de rapports et datasets partagés enregistrés sur le serveur de rapports. Pour plus d’informations sur [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] administration, consultez [Reporting Services Report Server &#40;en Mode natif&#41; ](report-server/reporting-services-report-server-native-mode.md) dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [la documentation en ligne](https://go.microsoft.com/fwlink/?LinkId=154888) sur msdn.microsoft.com.  
  
##  <a name="Installing"></a> Installation du Générateur de rapports  
 Le Générateur de rapports est disponible en version autonome et en version [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Vous ou votre administrateur devez télécharger et installer la version autonome sur votre ordinateur, alors que la version [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] est installée avec [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]. Vous pouvez télécharger le Générateur de rapports à partir du [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?LinkID=186083).  
  
> [!NOTE]  
>  Il n'est pas possible d'installer le Générateur de rapports sur les ordinateurs Itanium 64. Cela s'applique aux versions [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] et autonome du Générateur de rapports.  
  
 Avant d'installer l'une ou l'autre des versions du Générateur de rapports, vérifiez la configuration requise et installez les éléments requis.  
  
### <a name="system-requirements"></a>Configuration système requise  
 Le Générateur de rapports requiert que la version 3.5 de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] soit installée sur l'ordinateur local. Si le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] n'est pas installé sur l'ordinateur local lorsque vous installez le Générateur de rapports, vous êtes invité à l'installer pour pouvoir continuer et terminer l'installation.  
  
 .NET Framework 3.5 est gratuit. Vous pouvez télécharger .NET Framework 3.5 à partir du [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?LinkID=110520).  
  
 Vous pouvez installer le Générateur de rapports sur tout système d'exploitation [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows qui prend en charge le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.5. Vous pouvez par exemple installer le Générateur de rapports sur Windows Vista ou Windows 7.  
  
 Il est recommandé que les ordinateurs qui exécutent le Générateur de rapports disposent de 512 Mo de RAM. Toutefois, en fonction de la complexité des rapports exécutés, il peut falloir plus ou moins de RAM.  
  
### <a name="installing-the-stand-alone-version-of-report-builder-directly-on-your-computer"></a>Installation de la version autonome du Générateur de rapports directement sur votre ordinateur  
 Soit vous installez le Générateur de rapports à partir du site de téléchargement, [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?LinkID=186083), soit un administrateur met à disposition le fichier ReportBuilder3.msi (package Windows Installer du Générateur de rapports) sur un partage à partir duquel vous pouvez l'installer.  
  
 Vous pouvez également effectuer une installation à partir de la ligne de commande et inclure des options telles que l'installation silencieuse et l'écriture de fichiers journaux d'installation. La documentation de Windows Installer, qui exécute les fichiers .msi, fournit des informations concernant les options disponibles.  
  
 Pour plus d’informations, consultez [installer la Version autonome du Générateur &#40;Générateur de rapports&#41;](install-windows/install-report-builder.md).  
  
 Un administrateur peut également utiliser un logiciel tel que Microsoft Systems Manager Server (SMS) pour placer le programme sur votre ordinateur par transmission de type push. Pour savoir comment utiliser des logiciels spécifiques pour installer le Générateur de rapports, consultez la documentation des logiciels en question.   
  
### <a name="installing-the-clickonce-version-of-report-builder-on-your-computer"></a>Installation de la version ClickOnce du Générateur de rapports sur votre ordinateur  
 La version [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] du Générateur de rapports est installée avec [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]. Elle est installée via l'installation native et l'installation intégrée SharePoint de [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)].  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] est une technologie Microsoft pour le déploiement d'applications Windows. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] permet aux utilisateurs d'installer et d'exécuter une application Windows telle que le Générateur de rapports en cliquant sur un lien dans une page Web. Pour plus d'informations sur le déploiement des applications [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , sur la mise en œuvre de la sécurité pour les applications [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ou sur l'exécution des applications [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dans la zone Internet, consultez le site Web [!INCLUDE[msCoName](../includes/msconame-md.md)] Developer Network, à l'adresse [www.microsoft.com/msdn](https://www.microsoft.com/msdn), les articles, éventuellement en anglais, consacrés au déploiement de ClickOnce pour les applications Windows Forms, à la sécurité dans l'approche générale de Windows Forms ou à la présentation générale du déploiement des applications approuvées.  
  
 La version [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] du Générateur de rapports se trouve sur le serveur de rapports et est installée sur votre ordinateur lorsque vous cliquez sur le bouton **Générateur de rapports** dans le Gestionnaire de rapports, ou sur l'option **Rapport du Générateur de rapports** dans le menu **Nouveau document** d'une bibliothèque SharePoint.  
  
> [!NOTE]  
>  Si le menu **Nouveau document** ne répertorie pas les options **Rapport du Générateur de rapports**, **Modèle du générateur de rapports**et **Source de données du rapport** , leurs types de contenus doivent être ajoutés à la bibliothèque SharePoint.   
  
 Vous pouvez ouvrir le Générateur de rapports à partir du Gestionnaire de rapports ou d'une bibliothèque SharePoint. Pour plus d’informations sur l’ouverture du Générateur de rapports, consultez [démarrer le Générateur de &#40;Générateur de rapports&#41;](report-builder/start-report-builder.md).  
  
### <a name="report-builder-languages"></a>Langues du Générateur de rapports  
 Le Générateur de rapports est disponible en 21 langues, en plus de l'anglais. Lors du téléchargement de la version autonome du Générateur de rapports, sélectionnez la version linguistique à installer. Vous devez répéter le téléchargement pour chaque version linguistique à utiliser.  
  
 Pour la version [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , toutes les versions linguistiques sont installées sur le serveur de rapports lorsque vous installez [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]. La culture de l'ordinateur de l'utilisateur détermine la version linguistique qui est installée sur l'ordinateur. Si la culture ne correspond pas à une langue disponible pour le Générateur de rapports, la version anglaise est installée.  
  
 Le tableau suivant contient des informations sur les versions linguistiques disponibles.  
  
|LCID|Langue|Culture|  
|----------|--------------|-------------|  
|1028|Chinois (traditionnel)|zh-TW|  
|1029|Czech|cs-CZ|  
|1030|Danish|da-DK|  
|1031|German|de-DE|  
|1032|Greek|el-GR|  
|1033|Anglais|en-US|  
|1035|Finlandais|fi-FI|  
|1036|Français|fr-FR|  
|1038|Hongrois|hu-HU|  
|1040|Italien|it-IT|  
|1041|Japonais|ja-JP|  
|1042|Coréen|ko-KR|  
|1043|Néerlandais|nl-NL|  
|1044|Norvégien (Bokmal)|nb-NO|  
|1045|Polonais|pl-PLl|  
|1046|Portugais (Brésil)|pt-BR|  
|1049|Russe|ru-RU|  
|1053|Suédois|sv-SE|  
|1055|Turc|tr-TR|  
|2052|Chinois (simplifié)|zh-CN|  
|2070|Portugais (Portugal)|pt-PT|  
|3082|Espagnol (Espagne)|es-ES|  
  
  
##  <a name="Uninstalling"></a> Désinstallation du Générateur de rapports  
 Vous pouvez désinstaller la version autonome du Générateur de rapports à partir du Panneau de configuration ou de la ligne de commande. Cela s'applique uniquement à la version autonome du Générateur de rapports. La version [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] du Générateur de rapports ne peut pas être désinstallée séparément. Elle est toujours installée et désinstallée avec [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
 Pour plus d’informations, consultez [désinstaller la Version autonome du Générateur &#40;Générateur de rapports&#41;](install-windows/uninstall-report-builder.md).  
  
  
##  <a name="Supporting"></a> Prise en charge du Générateur de rapports  
 Pour assurer la prise en charge des auteurs de rapports, un administrateur est responsable de la gestion des dossiers, des rapports et des éléments liés aux rapports sur le serveur de rapports ; en outre, il est chargé d'accorder les autorisations relatives aux ressources du serveur de rapports et de configurer l'accès à ce dernier.  
  
### <a name="folders-reports-and-report-related-items"></a>Dossiers, rapports et éléments liés aux rapports  
 Les dossiers, rapports et éléments liés aux rapports suivants sont gérés sur le serveur de rapports :  
  
-   Dossiers dans lesquels vous stockez les rapports, sources de données partagées, modèles, etc.  
  
-   Mes rapports, dossier privé dans lequel vous stockez vos rapports et éléments liés aux rapports.  
  
-   Sources de données partagées qui permettent aux auteurs de rapports d'utiliser des sources de données stockées à l'extérieur des rapports.  
  
-   Datasets partagés qui peuvent fournir des données interrogées prêtes à l'emploi dans plusieurs rapports pour plusieurs utilisateurs.  
  
-   Parties de rapports telles que les tableaux et graphiques, qui permettent aux utilisateurs d'améliorer et de réutiliser certaines parties de rapports, créées par d'autres personnes, dans un environnement de collaboration.  
  
-   Modèles de rapport qui peuvent simplifier et faciliter la récupération des données des rapports à partir de sources de données complexes.  
  
-   Images telles que les images et logos d'arrière-plan qui peuvent être utilisés dans plusieurs rapports et sont stockés hors des rapports pour en faciliter la maintenance.  
  
 Pour plus d’informations, consultez [gestion de contenu de serveur de rapports &#40;SSRS en Mode natif&#41; ](report-server/report-server-content-management-ssrs-native-mode.md) dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [la documentation en ligne](https://go.microsoft.com/fwlink/?LinkId=154888) sur msdn.microsoft.com.  
  
### <a name="permissions"></a>Autorisations  
 L'administrateur octroie les autorisations relatives au serveur de rapports. En tant qu'utilisateur du Générateur de rapports, vous devez disposer des autorisations nécessaires pour accéder au contenu et aux fonctionnalités du serveur de rapports. Par exemple, vous pouvez utiliser des parties de rapports stockées sur le serveur de rapports, mettre à jour les rapports et les réenregistrer sur le serveur de rapports, et exécuter des rapports dans le Gestionnaire de rapports. Selon vos besoins et les tâches que vous effectuez, des autorisations de niveau inférieur ou supérieur peuvent être accordées. Par exemple, des autorisations avec un faible niveau de privilège sont accordées aux utilisateurs qui n'ont besoin que d'ouvrir des rapports partagés, par opposition à ceux qui doivent les modifier.  
  
 Lorsque [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] est installé en mode natif, un administrateur peut effectuer les tâches suivantes :  
  
-   Activer la fonctionnalité Mes rapports afin de vous fournir un dossier privé dédié à la création et l'enregistrement de vos propres rapports.  
  
-   Utiliser le rôle Générateur de rapports sur des dossiers publics pour vous permettre d'ouvrir une copie d'un rapport partagé, puis d'enregistrer une version modifiée dans un dossier privé.  
  
-   Utiliser le rôle Serveur de publication pour vous permettre de gérer des rapports et des sources de données partagées dans des dossiers publics. Ce rôle est accordé aux utilisateurs plus expérimentés.  
  
 Lorsque [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] est installé en mode intégré SharePoint, un administrateur peut effectuer les tâches suivantes :  
  
-   Utiliser le niveau d'autorisation Lecture, accordé par défaut au groupe Visiteurs, pour vous permettre d'ouvrir une copie d'un rapport dans un dossier public, puis d'enregistrer la version modifiée du rapport dans un dossier privé ou sur votre ordinateur.  
  
-   Utiliser le niveau d'autorisation Collaboration, accordé par défaut aux groupes Membres, pour vous permettre de gérer des rapports et des sources de données partagées dans des dossiers publics. Ce niveau d'autorisation est accordé aux utilisateurs plus expérimentés.  
  
 Pour obtenir des informations d'ordre général sur les autorisations, ainsi que sur la création et l'utilisation des rôles, consultez la documentation relative au moteur de base de données SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] dans la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [documentation en ligne](https://go.microsoft.com/fwlink/?LinkId=154888) sur msdn.microsoft.com.  
  
### <a name="configuration-of-report-server"></a>Configuration du serveur de rapports  
 Lorsque vous créez des rapports dans le Générateur de rapports et que vous vous connectez à une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installée sur Windows Vista, Windows Server 2008 ou Windows 7, vous pouvez rencontrer une erreur de refus d'accès lorsque vous tentez d'accéder au serveur de rapports pour ouvrir ou enregistrer un rapport. Ceci est dû au fait que la fonctionnalité de sécurité Contrôle de compte d'utilisateur dans Windows Vista, Windows Server 2008 et Windows 7 limite l'utilisation abusive des autorisations élevées en supprimant les autorisations administrateur lors de l'accès aux applications.  
  
 Toutefois, après une configuration supplémentaire, le serveur de rapports est accessible aux utilisateurs du Générateur de rapports version. Vous pouvez ajouter des URL [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] aux sites approuvés. Par défaut, Internet Explorer 7.0 ou version ultérieure s'exécute en mode protégé sur Windows Vista, Windows Server 2008 et Windows 7. Le mode protégé est une fonctionnalité qui empêche les requêtes du navigateur d'atteindre les processus de niveau supérieur qui s'exécutent sur le même ordinateur. Vous pouvez désactiver le mode protégé pour les applications du serveur de rapports en les ajoutant comme Sites de confiance. Vous devez disposer d'une autorisation d'administrateur pour apporter cette modification.  
  
 Pour plus d’informations sur la configuration [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], consultez [Gestionnaire de Configuration de Reporting Services &#40;del&#41; ](/sql/2014/sql-server/install/reporting-services-configuration-manager-native-mode) dans le [documentation de Reporting Services](https://go.microsoft.com/fwlink/?linkid=121312) sur msdn.microsoft.com.  
  
  
##  <a name="SampleDatabases"></a> Bases de données exemple SQL Server  
 La famille d'exemples de bases de données Adventure Works fournit des données que vous pouvez utiliser pour apprendre à créer des rapports et écrire des exemples de rapports.  
  
 Les bases de données sont disponibles dans les versions suivantes :  
  
-   La base de données Adventure Works OLTP prend en charge des scénarios standard de traitement transactionnel en ligne pour une entreprise fictive de fabrication de vélos (Adventure Works Cycles). Les scénarios incluent la fabrication, les ventes, l'achat, la gestion des produits, la gestion des contacts et les ressources humaines.  
  
-   La base de données [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] montre comment générer un entrepôt de données.  
  
-   Le projet [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] peut être utilisé afin de créer une base de données AS pour les scénarios de décisionnel.  
  
 Les exemples de bases de données ne sont pas inclus dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] et ne sont pas installés lorsque vous installez [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] ou la version autonome du Générateur de rapports. À la place, vous téléchargez les exemples de bases de données de [CodePlex](https://go.microsoft.com/fwlink/?LinkId=87843). Toutes les versions des exemples de bases de données sont téléchargées ensemble. Vous pouvez également télécharger des versions de bases de données antérieures disponibles avec [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]et [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)].  
  
 Pour connaître les éléments requis et les instructions spécifiques au téléchargement et à l'installation des exemples de bases de données [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] , consultez [Conditions préalables d'installation pour les exemples de bases de données SQL Server 2008](https://go.microsoft.com/fwlink/?LinkId=166648) et [Installation les exemples de bases de données](https://go.microsoft.com/fwlink/?LinkId=166649) sur CodePlex.  
  
  
##  <a name="HowTo"></a> Rubriques de procédures  
 Cette section répertorie les procédures qui vous montrent comment installer et désinstaller le Générateur de rapports.  
  
 [Installer la Version autonome du Générateur de rapports &#40;Générateur de rapports&#41;](install-windows/install-report-builder.md)  
  
 [Désinstaller la Version autonome du Générateur de rapports &#40;Générateur de rapports&#41;](install-windows/uninstall-report-builder.md)  
  
 [Démarrer le Générateur de &#40;Générateur de rapports&#41;](report-builder/start-report-builder.md)  
  
  
## <a name="see-also"></a>Voir aussi  
 [Générateur de rapports dans SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
