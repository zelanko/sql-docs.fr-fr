---
title: Outils de configuration de PowerPivot | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f934c51d-01fe-4e67-971d-cd87d7d7ee51
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 299b40b92b3d2f8c5559a5e10e511f80ab5a5bc9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175658"
---
# <a name="powerpivot-configuration-tools"></a>PowerPivot Configuration Tools
  Configurez, réparez ou [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] supprimez un avec les outils de configuration de PowerPivot.

 L'Assistant Installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installe l'outil de configuration de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint 2010 et un outil de configuration de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint 2013. Cette rubrique décrit l'utilisation générale des outils et ce qui les différencie.

 **[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 | SharePoint 2010

 **Dans cette rubrique :**

-   [Configuration requise pour utiliser les outils de configuration](#bkmk_requirements)

-   [Deux versions de l'outil de configuration](#bkmk_twoversions)

-   [Présentation de l'utilisation d'un outil de configuration de PowerPivot](#bkmk_overview)

-   [Démarrer l'un des outils de configuration PowerPivot](#bmkm_start_tool)

##  <a name="requirements-for-using-the-configuration-tools"></a><a name="bkmk_requirements"></a>Configuration requise pour l’utilisation des outils de configuration

-   Vous devez être un administrateur de la batterie de serveurs.

-   Vous devez être un administrateur de serveur sur l'instance Analysis Services (SharePoint 2010 uniquement).

-   Vous devez être db_owner sur la base de données de configuration de la batterie de serveurs.

-   Il n'y a aucune spécification de port TCP/IP à définir pour les outils de configuration, par conséquent vous n'avez pas besoin de configurer votre pare-feu pour les utiliser. L'outil de configuration suppose que les applications Web et les services partagés sont disponibles dans le cadre de la plateforme SharePoint. Vous devrez peut-être configurer votre pare-feu pour le serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Pour plus d’informations, consultez [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).

##  <a name="two-versions-of-the-configuration-tool"></a><a name="bkmk_twoversions"></a>Deux versions de l’outil de configuration
 L'Assistant Installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installe l'outil de configuration de PowerPivot pour SharePoint 2010 et un outil de configuration de PowerPivot pour SharePoint 2013.

 Les outils ne peuvent être utilisés qu'avec une instance [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. Ne les utilisez pas avec des installations de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] .

|Nom|Version prise en charge de SharePoint|Détails de la configuration|
|----------|-------------------------------------|----------------------------|
|Configuration de PowerPivot pour SharePoint 2013|SharePoint 2013|[Configurez ou réparez PowerPivot pour SharePoint 2013 &#40;outil de configuration de PowerPivot&#41;](configure-or-repair-power-pivot-for-sharepoint-2013.md)|
|Outil de configuration de PowerPivot|SharePoint 2010 avec SharePoint 2010|[Configurez ou réparez PowerPivot pour SharePoint 2010 &#40;outil de configuration de PowerPivot&#41;](../configure-repair-powerpivot-sharepoint-2010.md)|

###  <a name="how-the-two-configuration-tools-are-different"></a><a name="bkmk_sum_differences_betweentools"></a>Différences entre les deux outils de configuration
 Les deux versions de l'outil de configuration sont similaires mais il existe des différences dans les étapes de configuration qu'ils exécutent. Les différences sont dues aux changements entre SharePoint 2010 et SharePoint 2013 ainsi qu'aux différences d'architecture entre la version SQL Server 2012 SP1 de PowerPivot pour SharePoint et la version précédente de PowerPivot pour SharePoint.

 Le tableau suivant décrit les nouvelles fonctionnalités et les fonctionnalités modifiées de l'outil de **Configuration PowerPivot pour SharePoint 2013** . Il décrit également les fonctionnalités de l' **Outil de configuration de PowerPivot** exclues de l'outil de configuration de PowerPivot pour SharePoint 2013. Les lignes du tableau sont dans le même ordre que les onglets dans les outils de configuration.

|Configuration de PowerPivot pour SharePoint 2013|Outil de configuration de PowerPivot|
|--------------------------------------------------|-----------------------------------|
|La page principale est une nouvelle option pour **Serveur PowerPivot pour Excel Services**. L'option prend en charge la nouvelle architecture dans laquelle [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] s'exécute à l'extérieur de la batterie de serveurs SharePoint. Vous pouvez configurer Excel Services afin d'utiliser un ou plusieurs serveurs [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui s'exécutent en mode SharePoint.<br /><br /> ![Serveur PowerPivot dans le nouvel outil de configuration](../media/as-powerpivot-configtool-differences-new-mainpage.gif "Serveur PowerPivot dans le nouvel outil de configuration")||
||L'outil 2010 inclut la page **Inscrire SQL Server Analysis Services (PowerPivot) sur le serveur local** pour configurer une instance locale de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Cette page ne fait pas partie de l'outil 2013 car il n'existe aucune instance locale de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].<br /><br /> ![Compte de service AS dans l'ancien outil de configuration](../media/as-powerpivot-configtool-differences-old-register-as-localserver.gif "Compte de service AS dans l'ancien outil de configuration")|
||La page **Créer une application de service PowerPivot** comporte une option supplémentaire pour **Mettre les classeurs à niveau pour activer l'actualisation des données**. Cette option n'est pas disponible dans l'outil 2013.<br /><br /> ![Mettre à niveau les classeurs dans l'ancien outil de configuration](../media/as-powerpivot-configtool-differences-old-uprgadeworkbooks.gif "Mettre à niveau les classeurs dans l'ancien outil de configuration")|
|L'outil 2013 comprend une nouvelle page **Configurer les serveurs PowerPivot**. Cette page prend en charge la nouvelle architecture dans laquelle [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] s'exécute à l'extérieur de la batterie de serveurs SharePoint. Par défaut, le nom du serveur entré dans la page principale dans la zone de texte **Serveur PowerPivot pour Excel Services**, est également répertorié dans **Configurer les serveurs PowerPivot**.<br /><br /> ![Inscrire le nouvel outil de configuration des serveurs PowerPivot](../media/as-powerpivot-configtool-differences-new-powerpivot-servers.gif "Inscrire le nouvel outil de configuration des serveurs PowerPivot")||
|L'outil 2013 comprend une nouvelle page **Inscrire le complément PowerPivot pour le suivi de l'utilisation d'Excel Services**. Excel Services dans SharePoint 2010 ne suit pas les données d'utilisation de PowerPivot.||
||L'outil 2010 comprend la page **Ajouter MSOLAP.5 en tant que fournisseur approuvé** pour inscrire MSOLAP afin qu'Excel Services dans SharePoint 2010 puisse charger des modèles PowerPivot. Cette page ne fait pas partie de l'outil 2013. Excel Services dans SharePoint 2013 n'utilise pas le fournisseur MSOLAP pour charger les modèles.|

##  <a name="overview-of-using-a-powerpivot-configuration-tool"></a><a name="bkmk_overview"></a>Vue d’ensemble de l’utilisation d’un outil de configuration PowerPivot
 Lorsque vous démarrez l'un des outils de configuration de PowerPivot, ce dernier analyse l'installation existante afin de déterminer les opérations applicables. Lors d'une nouvelle installation, seule la tâche de configuration est disponible. Une fois le serveur configuré, la tâche de suppression s'affiche. Si vous avez démarré avec une instance de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] , la mise à niveau est également activée dans la liste des tâches disponibles.

 Si vous n'êtes pas familiarisé avec l'Administration centrale ou Windows PowerShell, exécutez l'outil de configuration à la place d'une installation de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] .

 De plus, l'outil peut détecter si la batterie de serveurs est configurée ou si des fonctionnalités requises sont manquantes. Si les fichiers programme SharePoint sont installés, mais que la batterie de serveurs n'est pas configurée, l'outil fournit des actions pour configurer la batterie et l'installation de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] .

 Vous pouvez examiner l'onglet **Script** pour apprendre et comprendre la configuration de PowerPivot et SharePoint à l'aide de Windows PowerShell. Pour plus d’informations, consultez les rubriques suivantes :

-   [Configuration de PowerPivot à l’aide de Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)

-   [Référence PowerShell pour PowerPivot pour SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)

> [!NOTE]
>  L'outil ne configure pas Reporting Services. Si vous ajoutez Reporting Services à votre environnement SharePoint, vous devez l'installer et le configurer séparément. Pour plus d’informations, consultez les rubriques suivantes :
> 
>  -   [Installez Reporting Services mode SharePoint pour sharepoint 2013](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).
> -   [Installez Reporting Services mode SharePoint pour sharepoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).

##  <a name="start-one-of-the-powerpivot-configuration-tools"></a><a name="bmkm_start_tool"></a>Démarrer l’un des outils de configuration de PowerPivot

1.  Dans l’écran **Démarrer** , tapez`powerpivot`

     Dans l’écran **Démarrer** , tapez `powerpivot` ou dans le menu **Démarrer** , cliquez sur **tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], sur outils de **configuration**, puis sur l’une des options suivantes :

    -   **Outil de configuration de PowerPivot**.

    -   **OR**

    -   **Configuration de PowerPivot pour SharePoint 2013**.

     ![deux outils de configuration PowerPivot](../media/as-powerpivot-configtools-bothicons.gif "deux outils de configuration PowerPivot")

     **Remarque :** les outils sont disponibles uniquement lorsque [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] est installé sur le serveur local.

2.  Au démarrage, les outils de configuration vérifient l'état de votre installation et fournissent les tâches qui sont valides pour votre installation.

3.  Selon l'état actuel de votre installation, une ou plusieurs tâches peuvent être effectuées, dont :

    1.  Cliquez sur **Configurer ou réparer PowerPivot pour SharePoint** pour terminer les tâches consécutives à l'installation ou pour réparer une installation.

    2.  Cliquez sur **Supprimer des fonctionnalités, des services, des applications et des solutions** pour supprimer des fonctionnalités et des solutions de la batterie de serveurs.

    3.  Cliquez sur **Mettre à niveau des fonctionnalités, des services, des applications et des solutions** pour mettre à niveau les fonctionnalités et les solutions qui ont été installées à l'aide d'une version antérieure de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].

     Par exemple, l'illustration montre la page de démarrage de l'outil de configuration de PowerPivot pour SharePoint 2013.

     ![Outil de configuration PowerPivot pour SharePoint 2013](../media/ssas-powerpivot-configtool-4-sharepoint2013-choosemode.gif "Outil de configuration PowerPivot pour SharePoint 2013")

 Chaque tâche est composée de différentes actions qui concernent un aspect particulier de la configuration du serveur. Par exemple, la tâche de configuration inclut des actions pour déployer des solutions, créer une application de service PowerPivot, activer des fonctionnalités et configurer l'actualisation des données. La liste d'actions varie selon l'état actuel de votre installation. Si une action n'est pas nécessaire, l'outil l'exclut de la liste des tâches.

 Lorsque vous cliquez sur Exécuter, l'outil traite toutes les actions par lots. Bien que chaque action s'affiche en tant qu'élément distinct dans la liste des tâches, toutes les actions incluses dans la tâche sont traitées ensemble. Seules les actions qui réussissent un contrôle de validation sont traitées. Vous devrez peut-être ajouter ou modifier une partie des valeurs d'entrée pour réussir le contrôle de validation.

## <a name="related-content"></a>Contenu associé
 [Upgrade PowerPivot for SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) Décrit le flux de travail qui met à niveau une installation existante dans une batterie de serveurs.

 [Uninstall PowerPivot for SharePoint](../../sql-server/install/uninstall-power-pivot-for-sharepoint.md) Décrit le flux de travail qui supprime des services PowerPivot pour SharePoint, des solutions et des pages d'application dans une batterie de serveurs.

 [Configuration de PowerPivot à l’aide de Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)

 [Administration et configuration d’un serveur PowerPivot dans l’Administration centrale](power-pivot-server-administration-and-configuration-in-central-administration.md)


