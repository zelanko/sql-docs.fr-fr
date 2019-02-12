---
title: Installer ou désinstaller le complément Services Reporting pour SharePoint (SharePoint 2010 et SharePoint 2013) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: c2804a9a-08ea-4f4a-805d-a2c19c68733d
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: c7369ac2da7dd8b7f93ec02ef240d78e76967d92
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56033000"
---
# <a name="install-or-uninstall-the-reporting-services-add-in-for-sharepoint-sharepoint-2010-and-sharepoint-2013"></a>Installer ou désinstaller le complément Reporting Services pour SharePoint (SharePoint 2010 et SharePoint 2013)
  Exécutez le package d’installation du complément [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint (rsSharePoint.msi) sur les serveurs SharePoint pour activer les fonctionnalités [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans un déploiement SharePoint. Ces fonctionnalités incluent Power View, un composant WebPart visionneuse de rapports, un point de terminaison de proxy d'URL, des types de contenu et des pages d'application qui vous permettent de créer, d'afficher et de gérer des rapports, des modèles de rapport, des sources de données et tout autre contenu du serveur de rapports sur un site SharePoint. Le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint est un composant requis pour un serveur de rapports qui s'exécute en mode SharePoint. Le complément peut être installé à partir de l'Assistant Installation [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou en téléchargeant le fichier rsSharePoint.msi du Feature Pack [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Pour obtenir la liste des versions du complément et les pages de téléchargement, consultez [Où trouver le complément Reporting Services pour les produits SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010|  
  
 **Dans cette rubrique :**  
  
-   [Conditions préalables](#bkmk_prereq)  
  
-   [Quel est le complément installe ?](#bkmk_whatinstalled)  
  
-   [Vue d’ensemble des méthodes d’Installation](#bkmk_3ways_to_install)  
  
-   [Installer le complément à l’aide du fichier d’installation rsSharePoint.msi](#bkmk_install_rssharepoint)  
  
    -   [Installation de fichiers uniquement](#bkmk_files_only_installation)  
  
-   [Procédure de suppression de la création de rapports Services Add-in](#bkmk_remove_addin)  
  
-   [Comment réparer rssharepoint.msi à partir de la ligne de commande](#bkmk_repair)  
  
-   [Fichiers journaux d’installation](#bkmk_logfiles)  
  
-   [Upgrade](#bkmk_upgrade)  
  
-   [RsCustomAction.exe](#bkmk_rscustomaction)  
  
##  <a name="bkmk_prereq"></a> Conditions préalables  
 L'installation du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est l'une des nombreuses étapes nécessaires pour intégrer un serveur de rapports à une instance d'un produit SharePoint. Pour plus d'informations sur l'ensemble des conditions requises pour l'utilisation du mode SharePoint, consultez [Hardware and Software Requirements for Reporting Services in SharePoint Mode](../../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md). Pour plus d'informations sur l'installation et la configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez [Install Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).  
  
-   Si vous intégrez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à une batterie de serveurs SharePoint qui possède plusieurs applications Web frontales, installez le complément sur chaque ordinateur de la batterie de serveurs qui possède un serveur Web frontal. Effectuez cette opération uniquement pour les serveurs Web frontaux qui seront utilisés pour accéder à du contenu de serveur de rapports.  
  
-   Pour installer le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vous devez être administrateur sur l'ordinateur. Par exemple, si vous exécutez le fichier rsSharePoint.msi à l'invite de commandes, vous devez ouvrir l'invite de commandes avec des privilèges d'administrateur à l'aide de l'option **Exécuter en tant qu'administrateur** .  
  
-   Pour installer le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vous devez être membre du groupe Administrateur de batterie de serveurs SharePoint.  
  
-   Vous devez être administrateur de collection de sites pour activer la fonctionnalité d'intégration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   Pour consulter des exemples de schéma de déploiement avec le complément, consultez [Deployment Topologies for SQL Server BI Features in SharePoint](../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).  
  
##  <a name="bkmk_whatinstalled"></a> Qu'est-ce que le complément installe ?  
 Le processus d'installation du complément est composé de deux phases qui sont effectuées automatiquement lorsque vous exécutez une installation par défaut :  
  
-   La première étape consiste à installer les fichiers dans les dossiers appropriés. Les dossiers sont standard pour les déploiements SharePoint. L'un des fichiers qui est installé est rsCustomAction.exe.  
  
-   La deuxième partie de l'installation consiste à exécuter un jeu d'actions personnalisées pour enregistrer les fichiers [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à l'aide de SharePoint. Les actions personnalisées sont exécutées à partir de rsCustomAction.exe. Le fichier exe est supprimé lorsque l'installation en deux étapes complète est terminée. Vous pouvez exécuter une installation de **fichiers uniquement** et rsCustomAction.exe ne s'exécute pas à l'issue de l'installation et est conservé sur le disque.  
  
## <a name="the-reporting-services-installation-order"></a>Ordre d'installation de Reporting Services  
 Le complément peut être installé avant ou après l'installation de SharePoint. Le complément suit les normes de prédéploiement SharePoint et installe les fichiers dans les emplacements utilisés par l'installation SharePoint.  
  
> [!NOTE]  
>  L'avantage de l'installation du complément avant le produit SharePoint est que le complément Reporting Services est configuré et activé par la batterie de serveurs SharePoint à mesure que les nouveaux serveurs sont ajoutés à la batterie.  
  
 **SharePoint 2010**  
  
-   L'Outil de préparation des produits SharePoint 2010 installe la version [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] inclut une nouvelle version du complément qui est requis pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] fonctionnalités.  
  
     Si vous exécutez l'Outil de préparation des produits SharePoint, vous devez installer la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   Si vous installez d'abord la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , lorsque vous exécuterez l'Outil de préparation des produits SharePoint la boîte de dialogue suivante s'affichera, indiquant que l'outil de préparation n'a pas installé la version antérieure du complément, car une version plus récente a été détectée. Ce comportement est attendu.  
  
     ![Le complément SSRS est déjà installé. ](../../../2014/sql-server/install/media/rs-sharepointprereq-complete.gif "Complément SSRS est déjà installé.")  
  
 **SharePoint 2013**  
  
 L'outil de préparation des produits SharePoint 2013 **n'** installe pas le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint.  
  
##  <a name="bkmk_3ways_to_install"></a> Vue d'ensemble des méthodes d'installation  
 Le complément [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint peut être installé en utilisant l’une des deux méthodes suivantes :  
  
-   **L’Assistant installation :** ![Remarque](../../../2014/reporting-services/media/rs-fyinote.png "Remarque")New avec [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], le complément peut être installé par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant installation. Choisissez **Complément Reporting Services pour les produits SharePoint** dans la page **Sélection de fonctionnalités** de l’Assistant.  
  
-   **rsSharepoint.msi:** le complément peut être installé directement à partir du support d'installation ou téléchargé et installé. Le fichier rsSharepoint.msi prend en charge à la fois une interface utilisateur graphique et une installation à partir de la ligne de commande. Vous devez exécuter le fichier .msi avec les privilèges d'administrateur ; pour ce faire, commencez par ouvrir une fenêtre d'invite de commandes avec des autorisations élevées, puis exécutez rsSharepoint.msi à partir de la ligne de commande. Pour plus d’informations sur le téléchargement du complément, consultez [Où trouver le complément Reporting Services pour les produits SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
    > [!NOTE]  
    >  Si vous utilisez le commutateur **/q** pour une installation silencieuse à partir de la ligne de commande, le Contrat de Licence Utilisateur Final ne sera pas affiché. Quelle que soit la méthode d'installation, l'utilisation de ce logiciel est régie par un contrat de licence et vous devez respecter les termes contractuels de ce contrat.  
  
##  <a name="bkmk_install_rssharepoint"></a> Installer le complément à l'aide du fichier d'installation rsSharePoint.msi  
 Cette section concerne l'installation du fichier rssharepoint.msi directement, en exécutant l'Assistant Installation .msi ou une installation à partir de la ligne de commande. Si vous avez installé le complément à l'aide de l'Assistant Installation de SQL Server, vous n'avez pas besoin de suivre ces étapes.  
  
 Vous pouvez afficher la liste complète des commutateurs de ligne de commande en exécutant la commande suivante :  
  
```  
Rssharepoint.msi /?  
```  
  
1.  Télécharger le programme d’installation (`rsSharepoint.msi`) pour le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in. Pour plus d’informations sur le téléchargement du complément, consultez [Où trouver le complément Reporting Services pour les produits SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
2.  En tant qu'administrateur, lancez `rsSharepoint.msi` pour exécuter l'Assistant Installation. L'Assistant affiche une page d'accueil, les termes du contrat de licence logiciel et une page d'information relative à l'inscription. L'installation crée des dossiers sous le chemin d'accès suivant et copie des fichiers vers ces dossiers :  
  
     `%program files%\common files\Microsoft Shared\Web Server Extensions\14\`  
  
     ou Gestionnaire de configuration  
  
     `%program files%\common files\Microsoft Shared\Web Server Extensions\15\`  
  
3.  Configurez les paramètres du serveur de rapports et l'activation de fonctionnalités dans l'Administration centrale de SharePoint. . Pour en savoir plus sur l’installation et la configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint, consultez la section [Installer le mode SharePoint de Reporting Services pour SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
###  <a name="bkmk_files_only_installation"></a> Installation de fichiers uniquement  
 Pour installer les fichiers mais ignorer la phase d'installation Actions personnalisées, exécutez le fichier rssharepoint.msi à partir de la ligne de commande avec l'option SKIPCA :  
  
1.  Ouvrez une invite de commandes **avec des autorisations d'administrateur**.  
  
2.  Exécutez la commande suivante :  
  
    ```  
    Msiexec.exe /i rsSharePoint.msi SKIPCA=1  
    ```  
  
 L'interface utilisateur du programme d'installation s'ouvre et s'exécute normalement et le fichier `rsCustomAction.exe` est installé. Toutefois, le fichier .exe ne sera pas exécuté à la fin de l'installation et `rsCustomAction.exe` sera conservé sur l'ordinateur.  
  
### <a name="use-a-two-step-installation-to-troubleshoot-installation-issues-or-install-the-content-types"></a>Utiliser une installation en deux étapes pour résoudre les problèmes d'installation ou installer des types de contenu  
 Si vous obtenez des erreurs pendant l'installation ou si les types de contenu [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne s'affichent pas dans les paramètres de la bibliothèque de documents, vous pouvez exécuter le programme d'installation en tant que processus en deux étapes à partir de la ligne de commande :  
  
1.  Ouvrez une invite de commandes **avec des autorisations d'administrateur** et exécutez une installation de fichiers uniquement comme le décrit la section précédente.  
  
2.  Exécutez l'exécutable d'actions personnalisées :  
  
    1.  Naviguez vers le dossier qui contient le fichier `rsCustomAction.exe`. Ce fichier est copié sur votre ordinateur pendant l'installation des fichiers seuls du complément. `rsCustomAction.exe` se trouve dans le **%temp%** directory. Pour naviguer jusqu'au fichier, entrez ce qui suit à partir de l'invite de commandes :  
  
         **CD %temp%**.  
  
         Le fichier doit se trouver à l’emplacement suivant : **\Users\\<votre_nom\>\AppData\Local\Temp**  
  
    2.  Tapez la commande suivante : Cette étape de configuration nécessitera plusieurs minutes. Le service W3SVC est redémarré pendant ce processus. Plusieurs messages d'état s'affichent à mesure que le programme copie les fichiers, inscrit les composants et exécute l'Assistant Configuration de produit SharePoint.  
  
        ```  
        rsCustomAction.exe /i  
        ```  
  
    3.  Le temps requis pour que les modifications soient appliquées peut varier, selon votre environnement serveur. Vous pouvez également exécuter **iisreset** pour forcer une mise à jour plus rapide.  
  
### <a name="quiet-installation-for-scripting"></a>Installation silencieuse de script  
 Vous pouvez utiliser le commutateur **/q** ou **/quiet** pour une installation « silencieuse » qui n’affiche pas de boîtes de dialogue ni d’avertissements. L'installation silencieuse est utile si vous souhaitez écrire un script d'installation du complément.  
  
> [!NOTE]  
>  Si vous utilisez le commutateur **/q** pour une installation silencieuse à partir de la ligne de commande, le Contrat de Licence Utilisateur Final ne sera pas affiché. Quelle que soit la méthode d'installation, l'utilisation de ce logiciel est régie par un contrat de licence et vous devez respecter les termes contractuels de ce contrat.  
  
 Pour effectuer une installation sans assistance :  
  
1.  Ouvrez une invite de commandes **avec des autorisations d'administrateur**.  
  
2.  Exécutez la commande suivante :  
  
    ```  
    Msiexec.exe /i rsSharePoint.msi /q  
    ```  
  
##  <a name="bkmk_remove_addin"></a> Procédure de suppression du complément Reporting Services  
 Vous pouvez désinstaller le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint à partir du Panneau de configuration [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ou de la ligne de commande.  
  
1.  Le Panneau de configuration vous permet d'effectuer une désinstallation complète des fichiers sur l'ordinateur actuel **ET** de supprimer l'objet ainsi que les fonctionnalités [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de la batterie de serveurs SharePoint. Une fois l'objet et les fonctionnalités [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] supprimés, vous ne pouvez plus vérifier ni mettre à jour les rapports.  
  
2.  Avec la méthode de désinstallation du complément via la ligne de commande, vous pouvez utiliser le paramètre LocalOnly pour supprimer uniquement les fichiers de complément sur l'ordinateur local. L'objet et les fonctionnalités [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de la batterie de serveurs ne sont pas modifiés.  
  
 La désinstallation du complément entraîne la suppression des fonctionnalités d'intégration utilisées pour traiter les rapports sur un serveur de rapports. Elle supprime également les pages [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de l'Administration centrale de SharePoint et d'autres pages personnalisées de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Sur les sites SharePoint affectés, vous pouvez également supprimer tous les rapports et autres éléments de serveur de rapports que vous n'utilisez plus. Ils ne pourront plus être exécutés après la suppression du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Pour désinstaller le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , une installation [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] ou [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] doit être en cours d'exécution. Si vous désinstallez d'abord le programme SharePoint 2010, vous devez le réinstaller pour pouvoir désinstaller le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Les étapes de désinstallation du complément sont identiques pour les serveurs autonomes et les batteries de serveurs. Le programme d'installation supprimera les fichiers de programme et tous les paramètres de configuration qui ont été ajoutés durant l'installation.  
  
 La désinstallation du complément n'entraîne pas la suppression des éléments suivants :  
  
-   Les comptes de connexion créés pour le compte de service Report Server qui étaient utilisés pour accéder aux bases de données de contenu et de configuration SharePoint. Vous devez supprimer les comptes de connexion pour le compte de service Report Server à partir de l'instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilisée pour héberger les bases de données SharePoint.  
  
-   Autorisations ou groupes que vous avez créés pour les utilisateurs de rapports. Si vous avez créé des groupes SharePoint ou des niveaux d'autorisation personnalisés pour accorder l'accès aux fonctionnalités du serveur de rapports, vous devez révoquer toutes les autorisations qui ne sont plus nécessaires.  
  
-   Fichiers de données que vous avez téléchargés vers une bibliothèque SharePoint, y compris les fichiers de définition de rapport (.rdl), de source de données partagée (.rsds) et d'éléments de rapports publiés (.rsc). Ces fichiers ne seront pas supprimés, mais ils ne s'exécuteront plus. Vous devez les supprimer manuellement.  
  
-   Le programme d'installation ne supprimera pas la base de données du serveur de rapports et ne modifiera pas l'instance du serveur de rapports utilisée pour les opérations intégrées.  
  
### <a name="to-uninstall-from-windows-control-panel"></a>Pour désinstaller à partir du Panneau de configuration Windows  
 Pour démarrer l'Assistant à partir du Panneau de configuration [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows et supprimer le complément :  
  
1.  Dans le Panneau de configuration, puis dans **Programmes**, sélectionnez **Désinstaller un programme**  
  
2.  Sélectionnez **Complément Microsoft SQL Server Reporting Services pour SharePoint**. Vous pouvez également démarrer l'Assistant Désinstallation en exécutant **rssharepoint.msi** à partir de l'invite de commandes sans commutateurs.  
  
3.  Cliquez sur **Supprimer**.  
  
### <a name="uninstall-from-the-command-line"></a>Désinstallation à partir de la ligne de commande  
 Pour désinstaller le complément à partir de la ligne de commande :  
  
1.  Ouvrez une invite de commandes **avec des autorisations d'administrateur**.  
  
2.  Exécutez la commande suivante :  
  
    ```  
    msiexec.exe /uninstall rsSharePoint.msi  
    ```  
  
3.  Un message de confirmation s'affiche. Cliquez sur **Oui**.  
  
### <a name="uninstall-the-add-in-from-the-local-server-only"></a>Désinstaller le complément du serveur local uniquement  
 Les méthodes précédentes de désinstallation du complément suppriment les fonctionnalités et l'objet [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de la batterie de serveurs. Si vous avez une batterie de plusieurs serveurs et si vous souhaitez désinstaller le complément uniquement sur l'ordinateur local tout en laissant la batterie de serveurs SharePoint dans un état fonctionnel, procédez comme suit :  
  
1.  Ouvrez une invite de commandes **avec des autorisations d'administrateur**.  
  
2.  Exécutez la commande suivante :  
  
    ```  
    Msiexec.exe /uninstall rsSharePoint.msi LocalOnly=1  
    ```  
  
 Cela annule l'enregistrement des composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de SharePoint et supprime les fichiers, mais pour l'ordinateur local uniquement.  
  
 Si vous souhaitez annuler l'inscription des fonctionnalités [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de SharePoint mais conserver les fichiers sur le disque pour une utilisation ultérieure, procédez comme suit :  
  
1.  Ouvrez une invite de commandes **avec des autorisations d'administrateur**.  
  
2.  Exécutez la commande suivante :  
  
    ```  
    rsCustomAction.exe /p  
    ```  
  
 Les étapes ci-dessus supposent que vous avez effectué une installation du fichier .msi avec SkipCA=1 et que le fichier rscusstomaction.exe est disponible. Pour plus d'informations, consultez la section décrivant l'installation de fichiers uniquement.  
  
##  <a name="bkmk_repair"></a> Procédure : réparer rssharepoint.msi à partir de la ligne de commande  
 Pour réparer ou désinstaller le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à partir de la ligne de commande, procédez comme suit :  
  
1.  Ouvrez une invite de commandes **avec des autorisations d'administrateur**.  
  
2.  Exécutez la commande suivante :  
  
    ```  
    msiexec.exe /f rssharepoint.msi  
    ```  
  
##  <a name="bkmk_logfiles"></a> Fichiers journaux d'installation  
 Durant son exécution, le programme d’installation enregistre des informations dans un fichier journal, dans le dossier **%temp%** de l’utilisateur qui installe le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Par exemple, **c:\Users\\\<nom_utilisateur\>\AppData\Local\Temp**. Le nom de fichier est **RS_SP_\<numéro>.log**, par exemple **RS_SP_0.log**. Chaque erreur consignée dans ce journal commence par la chaîne « SSRSCustomActionError ».  
  
> [!NOTE]  
>  AppData est un dossier masqué dans le système d'exploitation Windows. Vous devrez peut-être modifier vos paramètres des dossiers de l'Explorateur Windows afin de voir les fichiers masqués et des dossiers.  
  
#### <a name="view-a-log-file-with-windows-notepad"></a>Afficher un fichier journal à l'aide du Bloc-notes Windows  
  
1.  Les commandes suivantes changent le chemin d'accès d'invite de commandes, répertorient les fichiers journaux rs et ouvrent l'un des fichiers à l'aide du Bloc-notes Windows :  
  
    ```  
    cd %temp%  
    ```  
  
    ```  
    Dir rs_sp*.log  
    ```  
  
    ```  
    notepad rs_sp_3.log  
    ```  
  
#### <a name="view-a-log-file-with-powershell"></a>Afficher un journal avec PowerShell  
  
1.  Tapez la commande suivante à partir de SharePoint Management Shell pour retourner une liste filtrée des lignes du fichier, qui contiennent « ssrscustomactionerror » :  
  
    ```  
    Get-content -path C:\Users\<UserName\AppData\Local\Temp\rs_sp_0.log | select-string "ssrscustomactionerror"  
    ```  
  
2.  La sortie ressemble à l'exemple suivant :  
  
     `2011-05-23 12:40:12: SSRSCustomActionError: SharePoint is installed, but not configured`.  
  
##  <a name="bkmk_upgrade"></a> Mise à niveau  
 Si vous avez une installation existante du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vous pouvez effectuer une mise à niveau vers la version actuelle. Le programme d'installation du complément détectera la version existante et vous invitera à confirmer la mise à jour. Le message ressemble au suivant :  
  
 **Une version antérieure de ce produit a été détectée sur votre système. Voulez-vous mettre à niveau votre installation existante ?**  
  
 Si vous confirmez, la version antérieure du complément sera supprimée, puis la nouvelle installée.  
  
 Notez que le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n'est pas dépendant des instances. Vous ne pouvez avoir qu'une seule instance du complément sur un ordinateur. Vous ne pouvez pas exécuter des versions différentes côte à côte avec la version actuelle.  
  
##  <a name="bkmk_rscustomaction"></a> RsCustomAction.exe  
 Le tableau suivant récapitule les commutateurs de rscustomaction.exe :  
  
|Commutateur|Description|  
|------------|-----------------|  
|i|Installe les actions personnalisées. Enregistre les composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans SharePoint. Redémarre W3SVCservice.|  
|r|Repair|  
|u|Uninstall. Annule l'enregistrement des composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de la batterie de serveurs SharePoint mais conserve les fichiers sur le disque. Redémarre W3SVCservice.|  
|p|Désinstallation locale. Annule l'enregistrement des composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de l'ordinateur local uniquement. Les fichiers demeurent sur le disque. Redémarre W3SVCservice.|  
|t|SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005 uniquement. Le commutateur vérifie que le serveur de rapports dispose d'une connexion active à sa base de données.|  
  
## <a name="configuring-reporting-services"></a>configuration de Reporting Services  
 Après avoir installé le complément sur les ordinateurs appropriés, configurez le serveur de rapports à partir de l'Administration centrale de SharePoint. Les étapes nécessaires dépendent de l'ordre dans lequel les différentes technologies ont été installées. Pour plus d’informations, consultez [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) et [Reporting Services Report Server &#40;SharePoint Mode&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Installer le Mode SharePoint de Reporting Services pour SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)   
 [Serveur de rapports Reporting Services &#40;mode SharePoint&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)  
  
  
