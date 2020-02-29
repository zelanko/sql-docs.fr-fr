---
title: Installer ou désinstaller le complément PowerPivot pour SharePoint (SharePoint 2013) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: fe13ce8b-9369-4126-928a-9426f9119424
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2350d00353188bf2551b00e53f815eeb4c7bc462
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78174358"
---
# <a name="install-or-uninstall-the-powerpivot-for-sharepoint-add-in-sharepoint-2013"></a>Installer ou désinstaller le complément PowerPivot pour SharePoint (SharePoint 2013)
  
  [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] est un ensemble de composants de serveur d’applications et de services principaux qui fournissent l’accès aux données [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] dans une batterie de serveurs [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] . Le complément [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] pour SharePoint (**spPowerpivot.msi**) est un package d’installation utilisé pour installer les composants de serveur d’applications.

-   Ce complément n'est pas requis pour les déploiements SharePoint 2010.

-   Ce complément n'est pas requis dans un déploiement à un seul serveur qui inclut SharePoint 2013 et [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] en mode SharePoint. Les composants installés par le complément sont inclus lorsque vous installez un serveur [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] en mode SharePoint. Pour obtenir des diagrammes d’exemples de déploiement avec le complément, consultez [topologies de déploiement pour SQL Server fonctionnalités bi dans SharePoint](../../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).

 **Remarque :** Cette rubrique décrit l’installation [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] des fichiers de [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] solution et de pour l’outil de configuration de SharePoint 2013. Après l’installation, consultez la rubrique suivante pour plus d’informations sur l’outil de configuration et les fonctionnalités supplémentaires, [configurer PowerPivot et déployer des Solutions &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013).

 Pour plus d'informations sur le téléchargement de **spPowerPivot.msi**, consultez [Microsoft® SQL Server® 2014 PowerPivot® pour Microsoft SharePoint®](https://go.microsoft.com/fwlink/?LinkID=324854).

 **Dans cette rubrique :**

-   [Contexte](#bkmk_background)

-   [Où installer le fichier PowerPivot. msi ?](#bkmk_where_to_install)

-   [Configuration requise et conditions préalables](#bkmk_prereq)

-   [Pour installer PowerPivot pour SharePoint](#bkmk_install)

-   [Déployer les fichiers solution SharePoint avec l'outil de configuration PowerPivot pour SharePoint 2013](#bkmk_deploy_solution)

-   [Désinstaller ou réparer le complément](#bkmk_remove_addin)

##  <a name="bkmk_background"></a> Arrière-plan

-   **Serveur d’applications :** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] les fonctionnalités de SharePoint 2013 incluent l’utilisation de classeurs comme source de données, l’actualisation [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] planifiée des données et le tableau de bord de gestion.

     [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)]est un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] package de Windows Installer (**PowerPivot. msi**) qui déploie Analysis Services bibliothèques clientes et [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] copie les fichiers d’installation sur l’ordinateur. Le programme d'installation ne déploie pas ou ne configure pas de fonctionnalités [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] dans SharePoint. Les composants suivants s'installent par défaut :

    -   
  [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013. Ce composant inclut des scripts PowerShell (fichiers .ps1), des packages de solution SharePoint (.wsp) et l'outil de configuration [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013 pour déployer [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] dans une batterie de serveurs SharePoint 2013.

    -   
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Fournisseur OLE DB pour Analysis Services (MSOLAP).

    -   Fournisseur de données ADOMD.NET.

    -   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .

-   **Services principaux :** Si vous utilisez [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] pour Excel pour créer des classeurs qui contiennent des données analytiques, Excel Services doit être configuré avec un serveur [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] bi s’exécutant en mode SharePoint pour accéder à ces données dans un environnement serveur. Vous pouvez exécuter le programme d'installation de SQL Server sur un ordinateur qui possède un serveur SharePoint 2013 installé, ou sur un autre ordinateur sans logiciel SharePoint. Analysis Services n'a pas de dépendances de SharePoint.

     Pour plus d'informations sur l'installation, la désinstallation et la configuration des services principaux, consultez :

    -   [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)

    -   [Désinstaller PowerPivot pour SharePoint](../../../sql-server/install/uninstall-power-pivot-for-sharepoint.md)

##  <a name="bkmk_where_to_install"></a>Où installer le fichier PowerPivot. msi ?
 La meilleure pratique recommandée consiste à installer **spPowerPivot.msi** sur tous les serveurs de la batterie de serveurs SharePoint pour la cohérence de configuration, y compris les serveurs d’applications et les serveurs Web frontaux. Le package d'installation inclut les fournisseurs de données Analysis Services, ainsi que l'outil de configuration de [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] . Lorsque vous installez **spPowerPivot.msi** , vous pouvez personnaliser l'installation en excluant des composants.

 **Fournisseurs de données :** Plusieurs technologies SharePoint et SQL Server utilisent les fournisseurs de données Analysis Services, notamment Excel Services, PerformancePoint Services et Power View. L'installation de **spPowerPivot.msi** sur tous les serveurs SharePoint garantit que l'ensemble complet des fournisseurs de données Analysis Services et la connectivité PowerPivot sont constamment disponibles dans la batterie de serveurs.

> [!NOTE]
>  Vous devez installer les fournisseurs de données Analysis Services sur un serveur SharePoint 2013 à l'aide de **spPowerPivot.msi**. D'autres packages d'installation disponibles dans le Feature Pack [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] ne sont pas pris en charge, car ils n'incluent pas les fichiers de prise en charge de SharePoint 2013 dont les fournisseurs de données ont besoin dans cet environnement.

 **Outil de configuration :** L’outil de configuration PowerPivot pour SharePoint 2013 est requis sur un seul des serveurs SharePoint. Toutefois, la meilleure pratique recommandée dans les batteries de plusieurs serveurs consiste à installer l'outil de configuration sur au moins deux serveurs de façon à ce que vous ayez accès à l'outil de configuration si un des deux serveurs est hors connexion.

##  <a name="bkmk_prereq"></a>Configuration requise et conditions préalables

-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)]SharePoint Server 2013.

-   le fichier **. msi de PowerPivot** est 64 bits uniquement, conformément aux spécifications des produits et technologies SharePoint.

-   Serveur [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] en mode PowerPivot. Excel Services utilisera l'instance SQL Server Analysis Services en tant que serveur PowerPivot. Analysis Services peut s'exécuter sur un ordinateur local ou distant.

-   **Autorisations :** Pour installer [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)], l’utilisateur actuel doit être un administrateur sur l’ordinateur et un groupe administrateurs de batterie SharePoint.

-   Pour plus d’informations [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] sur la configuration requise et les conditions préalables requises, consultez [configurations matérielle et logicielle requises pour Analysis Services Server en Mode SharePoint &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md).

##  <a name="bkmk_install"></a>Pour installer PowerPivot pour SharePoint
 Le package d’installation **spPowerpivot.msi** prend en charge à la fois une interface utilisateur graphique et une installation en mode ligne de commande. Les deux méthodes d'installation requièrent que vous exécutiez le fichier .msi avec des privilèges d'administrateur. Après l’installation, consultez la rubrique suivante pour plus d’informations sur l’outil de configuration et les fonctionnalités supplémentaires, [configurer PowerPivot et déployer des Solutions &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013).

### <a name="user-interface-installation"></a>Installation de l'interface utilisateur
 Pour installer [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] avec l'interface utilisateur graphique, procédez comme suit :

1.  Exécutez **SpPowerPivot.msi**.

2.  Dans la page Bienvenue, cliquez sur **Suivant**.

3.  Lisez et acceptez le contrat de licence, puis cliquez sur **Suivant**.

4.  Dans la page **Sélection de fonctionnalités** , toutes les fonctionnalités sont sélectionnées par défaut.

5.  Cliquez sur **Suivant**.

6.  Cliquez sur **Installer** pour terminer l'installation.

### <a name="command-line-installation"></a>Installation à partir de la ligne de commande
 Pour une installation à partir de la ligne de commande, ouvrez une invite de commandes avec des autorisations administratives, puis exécutez **spPowerPivot.msi**. Par exemple :

 `Msiexec.exe /i SpPowerPivot.msi`.

 Pour créer un journal d'installation, utilisez les commutateurs d'enregistrement MsiExec standards. L’exemple suivant crée le fichier journal « Install_Log. txt » à l’aide du commutateur de journalisation verbose « v ».

```cmd
Msiexec.exe /i SpPowerPivot.msi /L v c:\test\Install_Log.txt
```

### <a name="quiet-command-line-installation-for-scripting"></a>Installation silencieuse de script à partir de la ligne de commande
 Vous pouvez utiliser le commutateur **/q** ou **/quiet** pour une installation « silencieuse » qui n’affiche pas de boîtes de dialogue ni d’avertissements. L'installation silencieuse est utile si vous souhaitez écrire un script d'installation du complément.

> [!IMPORTANT]
>  Si vous utilisez le commutateur **/q** pour une installation silencieuse à partir de la ligne de commande, le Contrat de Licence Utilisateur Final ne sera pas affiché. Quelle que soit la méthode d'installation, l'utilisation de ce logiciel est régie par un contrat de licence et vous devez respecter les termes contractuels de ce contrat.

#### <a name="to-perform-a-quiet-installation"></a>Pour effectuer une installation silencieuse

1.  Ouvrez une invite **de commandes avec des autorisations d’administrateur**.

2.  Exécutez la commande suivante :

    ```cmd
    Msiexec.exe /i spPowerPivot.msi /q
    ```

### <a name="command-line-installation-to-include-specific-components"></a>Installation à partir de la ligne de commande pour inclure des composants spécifiques
 L'outil de configuration [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] n'est pas requis sur chaque serveur SharePoint, mais il est néanmoins recommandé de l'installer sur au moins deux serveurs de façon à ce qu'il soit disponible lorsque vous en avez besoin.

 Lorsque vous installez le fichier spPowerPivot.msi, vous pouvez utiliser les options de ligne de commande pour installer des éléments spécifiques, comme les fournisseurs de données, et non l'outil de configuration [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] . La ligne de commande suivante est un exemple d'installation de tous les composants, à l'exception de l'outil de configuration :

```
Msiexec /i spPowerPivot.msi AGREETOLICENSE="yes" ADDLOCAL=" SQL_OLAPDM,SQL_ADOMD,SQL_AMO,SQLAS_SP_Common"
```

|Option|Description|
|------------|-----------------|
|Analysis_Server_SP_addin|Configuration PowerPivot|
|SQL_OLAPDM|MSOLAP|
|SQL_ADOMD|fournisseur ADOMD.net|
|SQL_AMO|Fournisseur AMO|
|SQLAS_SP_Common|Composants communs Analysis Services pour SharePoint 2013|

##  <a name="bkmk_deploy_solution"></a>Déployer les fichiers solution SharePoint avec l’outil de configuration PowerPivot pour SharePoint 2013
 Trois des fichiers copiés sur le disque dur par spPowerPivot.msi sont des fichiers solution de SharePoint. L'étendue d'un fichier solution correspond au niveau de l'application Web, alors que l'étendue des autres fichiers correspond au niveau de la batterie de serveurs. Les fichiers sont les suivants :

-   `PowerPivotFarmSolution.wsp`

-   `PowerPivotFarm14Solution.wsp`

-   `PowerPivotWebApplicationSolution.wsp`

 Les fichiers solution sont copiés dans le dossier suivant :

 `C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\SPAddinConfiguration\Resources`

 Après l'installation du fichier .msi, exécutez l'outil de configuration [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] pour configurer et déployer des solutions dans la batterie de serveurs SharePoint.

### <a name="to-start-the-configuration-tool"></a>Pour démarrer l’outil de configuration de 

 Dans l’écran de démarrage de Windows, tapez « Power », puis dans les résultats de la recherche d’applications, cliquez sur **PowerPivot pour SharePoint Configuration 2013**. Notez que les résultats de la recherche peuvent inclure deux liens car le programme d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installe des outils de configuration de [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] distincts pour SharePoint 2010 et SharePoint 2013. Lancez l'outil Configuration de [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] pour SharePoint 2013.

 ![deux outils de configuration PowerPivot](https://docs.microsoft.com/analysis-services/analysis-services/media/as-powerpivot-configtools-bothicons.gif "deux outils de configuration PowerPivot")

 **Ni**

1.  Accédez à **Démarrer**, **Tous les programmes**.

2.  Cliquez sur **Microsoft SQL Server 2014**.

3.  Cliquez sur **Outils de configuration**.

4.  Cliquez sur **Configuration (PowerPivot pour SharePoint 2013)**.

 Pour plus d'informations sur l'outil de configuration, consultez [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md).

##  <a name="bkmk_remove_addin"></a>Désinstaller ou réparer le complément

> [!CAUTION]
>  Si vous désinstallez **spPowerPivot.msi** , les fournisseurs de données et l'outil de configuration sont désinstallés. Désinstaller les fournisseurs de données empêchera le serveur de se connecter à PowerPivot.

 Pour désinstaller ou réparer [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] , procédez selon l'une des méthodes suivantes :

1.  **Panneau de configuration Windows :** Sélectionnez **Microsoft SQL Server 2012 PowerPivot pour SharePoint 2013**. Cliquez sur **Désinstaller** ou **Réparer**.

2.  Exécutez le fichier spPowerPivot.msi et sélectionnez l'option **Supprimer** ou **Réparer** .

 **Ligne de commande :** Pour réparer ou désinstaller PowerPivot pour SharePoint 2013 à l’aide de la ligne de commande, ouvrez une invite **de commandes avec des autorisations d’administrateur** et exécutez l’une des commandes suivantes :

-   Pour réparer, exécutez la commande suivante :

    ```cmd
    msiexec.exe /f spPowerPivot.msi
    ```

 OR

-   Pour désinstaller, exécutez la commande suivante :

    ```cmd
    msiexec.exe /uninstall spPowerPivot.msi
    ```
