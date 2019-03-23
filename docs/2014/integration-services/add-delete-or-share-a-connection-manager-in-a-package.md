---
title: Ajouter, supprimer ou partager un gestionnaire de connexions dans un Package | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], adding
- adding connection managers
ms.assetid: 6f2ba4ea-10be-4c40-9e80-7efcf6ee9655
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fdcc6285ba1a75827f91f856319d296c0cbbff5d
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58391687"
---
# <a name="add-delete-or-share-a-connection-manager-in-a-package"></a>Ajouter, supprimer ou partager un gestionnaire de connexions dans un package
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] inclut différents types de gestionnaires de connexions pour la connexion à différentes sources de données, telles que bases de données relationnelles, bases de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et fichiers au format CSV et XML. Un gestionnaire de connexions peut être créé au niveau du package ou au niveau du projet. Le gestionnaire de connexions créé au niveau du projet est disponible pour tous les packages du projet. Le gestionnaire de connexions créé au niveau du package n'est, quant à lui, disponible que pour ce seul package.  
  
 Pour partager des connexions aux sources, vous utilisez les gestionnaires de connexions créés au niveau du projet au lieu des sources de données. Pour ajouter un gestionnaire de connexions au niveau du projet, le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] doit utiliser le modèle de déploiement de projet. Quand un projet est configuré pour utiliser ce modèle, le dossier **Gestionnaires de connexions** apparaît dans **l’Explorateur de solutions**et le dossier **Sources de données** est supprimé de **l’Explorateur de solutions**.  
  
> [!NOTE]  
>  Si vous souhaitez utiliser des sources de données dans votre package, vous devez convertir le projet en modèle de déploiement de package.  
>   
>  Pour plus d’informations sur les deux modèles, consultez [Déploiement de projets et de packages](packages/deploy-integration-services-ssis-projects-and-packages.md). Pour plus d’informations sur la conversion d’un projet en modèle de déploiement de projet, consultez [Déployer des projets sur le serveur Integration Services](../../2014/integration-services/deploy-projects-to-integration-services-server.md).  
  
 Les procédures suivantes s'appliquent à tous les types de gestionnaires de connexions et expliquent comment effectuer les tâches suivantes :  
  
-   [Pour ajouter un gestionnaire de connexions lors de la création d’un package](#wizard)  
  
-   [Pour ajouter un gestionnaire de connexions à un package existant](#package)  
  
-   [Pour ajouter un gestionnaire de connexions au niveau du projet](#project)  
  
-   [Pour créer un paramètre pour une propriété de gestionnaire de connexions](#parameter)  
  
-   [Pour supprimer un gestionnaire de connexions d’un package](#DeletePackageLevel)  
  
-   [Pour supprimer un gestionnaire de connexions partagé (Gestionnaire de connexions de niveau projet)](#DeleteProjectLevel)  
  
##  <a name="wizard"></a> Pour ajouter un gestionnaire de connexions lors de la création d’un package  
  
-   Utiliser l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
     En plus de créer et configurer un gestionnaire de connexions, cet Assistant vous aide également à créer et configurer les sources et destinations qui utilisent le gestionnaire de connexions. Pour plus d'informations, consultez [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md).  
  
##  <a name="package"></a> Pour ajouter un gestionnaire de connexions à un package existant  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l’Explorateur de solutions, double-cliquez sur le package pour l’ouvrir.  
  
3.  Dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , cliquez sur l’onglet **Flux de contrôle** , **Flux de données** ou **Gestionnaire d’événements** pour rendre la zone **Gestionnaires de connexions** disponible.  
  
4.  Cliquez avec le bouton droit n’importe où dans la zone **Gestionnaires de connexions** , puis effectuez l’une des opérations suivantes :  
  
    -   Cliquez sur le type du gestionnaire de connexions à ajouter au package.  
  
         -ou-  
  
    -   Si le type que vous voulez ajouter ne figure pas dans la liste, cliquez sur **Nouvelle connexion** pour ouvrir la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS** , sélectionnez un type de gestionnaire de connexions, puis cliquez sur **OK**.  
  
     La boîte de dialogue personnalisée pour le type de gestionnaire de connexions sélectionné s'ouvre. Pour plus d'informations sur les types de gestionnaire de connexions et les options disponibles, reportez-vous au tableau d'options suivant.  
  
    |Gestionnaire de connexions|Options|  
    |------------------------|-------------|  
    |[Gestionnaire de connexions ADO](connection-manager/ado-connection-manager.md)|[Configurer le gestionnaire de connexions OLE DB](configure-ole-db-connection-manager.md)|  
    |[Gestionnaire de connexions ADO.NET](connection-manager/ado-net-connection-manager.md)|[Configurer le gestionnaire de connexions ADO.NET](configure-ado-net-connection-manager.md)|  
    |[Gestionnaire de connexions Analysis Services](connection-manager/analysis-services-connection-manager.md)|[Référence de l’interface utilisateur de la boîte de dialogue Ajout d’un gestionnaire de connexions Analysis Services](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)|  
    |[Gestionnaire de connexions Excel](connection-manager/excel-connection-manager.md)|[Éditeur du gestionnaire de connexions Excel](../../2014/integration-services/excel-connection-manager-editor.md)|  
    |[Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md)|[Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)|  
    |[Gestionnaire de connexions de fichiers multiples](connection-manager/multiple-files-connection-manager.md)|[Référence de l’interface utilisateur de la boîte de dialogue Ajouter un gestionnaire de connexions de fichiers](connection-manager/add-file-connection-manager-dialog-box-ui-reference.md)|  
    |[Gestionnaire de connexions de fichiers plats](connection-manager/flat-file-connection-manager.md)|[Éditeur du gestionnaire de connexions de fichiers plats &#40;page Général&#41;](general-page-of-integration-services-designers-options.md)<br /><br /> [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Colonnes&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)<br /><br /> [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Avancé&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)<br /><br /> [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Aperçu&#41;](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)|  
    |[Gestionnaire de connexions de fichiers plats multiples](connection-manager/multiple-flat-files-connection-manager.md)|[Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Général&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-general-page.md)<br /><br /> [Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Colonnes&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md)<br /><br /> [Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Avancé&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md)<br /><br /> [Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Aperçu&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)|  
    |[Gestionnaires de connexions FTP](connection-manager/ftp-connection-manager.md)|[Éditeur du gestionnaire de connexions FTP](../../2014/integration-services/ftp-connection-manager-editor.md)|  
    |[Gestionnaire de connexions HTTP](connection-manager/http-connection-manager.md)|[Éditeur du gestionnaire de connexions HTTP &#40;page Serveur&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)<br /><br /> [Éditeur du gestionnaire de connexions HTTP &#40;page Proxy&#41;](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)|  
    |[Gestionnaire de connexions MSMQ](connection-manager/msmq-connection-manager.md)|[Éditeur du gestionnaire de connexions MSMQ](../../2014/integration-services/msmq-connection-manager-editor.md)|  
    |[Gestionnaire de connexions ODBC](connection-manager/odbc-connection-manager.md)|[Informations de référence sur l’interface utilisateur du gestionnaire de connexions ODBC](../../2014/integration-services/odbc-connection-manager-ui-reference.md)|  
    |[Gestionnaire de connexions OLE DB](connection-manager/ole-db-connection-manager.md)|[Configurer le gestionnaire de connexions OLE DB](configure-ole-db-connection-manager.md)|  
    |[Gestionnaire de connexions SMO](connection-manager/smo-connection-manager.md)|[Éditeur du gestionnaire de connexions SMO](../../2014/integration-services/smo-connection-manager-editor.md)|  
    |[Gestionnaire de connexions SMTP](connection-manager/smtp-connection-manager.md)|[Éditeur du gestionnaire de connexions SMTP](../../2014/integration-services/smtp-connection-manager-editor.md)|  
    |[Gestionnaire de connexions de SQL Server Compact Edition](connection-manager/sql-server-compact-edition-connection-manager.md)|[Éditeur du gestionnaire de connexions SQL Server Compact Edition &#40;page Connexion&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)<br /><br /> [Éditeur du gestionnaire de connexions SQL Server Compact Edition &#40;page Tout&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-all-page.md)|  
    |[Gestionnaire de connexions WMI](connection-manager/wmi-connection-manager.md)|[Éditeur du gestionnaire de connexions WMI](../../2014/integration-services/wmi-connection-manager-editor.md)|  
  
     La zone **Gestionnaires de connexions** répertorie le gestionnaire de connexions ajouté.  
  
5.  Vous pouvez aussi cliquer avec le bouton droit sur le gestionnaire de connexions, cliquer sur **Renommer**, puis modifier le nom par défaut du gestionnaire de connexions.  
  
6.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer l’élément sélectionné** dans le menu **Fichier** .  
  
##  <a name="project"></a> Pour ajouter un gestionnaire de connexions au niveau du projet  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
2.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Gestionnaires de connexions**, puis cliquez sur **Nouveau gestionnaire de connexions**.  
  
3.  Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS** , sélectionnez le type de gestionnaire de connexions, puis cliquez sur **Ajouter**.  
  
     La boîte de dialogue personnalisée pour le type de gestionnaire de connexions sélectionné s'ouvre. Pour plus d'informations sur les types de gestionnaire de connexions et les options disponibles, reportez-vous au tableau d'options suivant.  
  
    |Gestionnaire de connexions|Options|  
    |------------------------|-------------|  
    |[Gestionnaire de connexions ADO](connection-manager/ado-connection-manager.md)|[Configurer le gestionnaire de connexions OLE DB](configure-ole-db-connection-manager.md)|  
    |[Gestionnaire de connexions ADO.NET](connection-manager/ado-net-connection-manager.md)|[Configurer le gestionnaire de connexions ADO.NET](configure-ado-net-connection-manager.md)|  
    |[Gestionnaire de connexions Analysis Services](connection-manager/analysis-services-connection-manager.md)|[Référence de l’interface utilisateur de la boîte de dialogue Ajout d’un gestionnaire de connexions Analysis Services](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)|  
    |[Gestionnaire de connexions Excel](connection-manager/excel-connection-manager.md)|[Éditeur du gestionnaire de connexions Excel](../../2014/integration-services/excel-connection-manager-editor.md)|  
    |[Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md)|[Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)|  
    |[Gestionnaire de connexions de fichiers multiples](connection-manager/multiple-files-connection-manager.md)|[Référence de l’interface utilisateur de la boîte de dialogue Ajouter un gestionnaire de connexions de fichiers](connection-manager/add-file-connection-manager-dialog-box-ui-reference.md)|  
    |[Gestionnaire de connexions de fichiers plats](connection-manager/flat-file-connection-manager.md)|[Éditeur du gestionnaire de connexions de fichiers plats &#40;page Général&#41;](general-page-of-integration-services-designers-options.md)<br /><br /> [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Colonnes&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)<br /><br /> [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Avancé&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)<br /><br /> [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Aperçu&#41;](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)|  
    |[Gestionnaire de connexions de fichiers plats multiples](connection-manager/multiple-flat-files-connection-manager.md)|[Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Général&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-general-page.md)<br /><br /> [Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Colonnes&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md)<br /><br /> [Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Avancé&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md)<br /><br /> [Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Aperçu&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)|  
    |[Gestionnaires de connexions FTP](connection-manager/ftp-connection-manager.md)|[Éditeur du gestionnaire de connexions FTP](../../2014/integration-services/ftp-connection-manager-editor.md)|  
    |[Gestionnaire de connexions HTTP](connection-manager/http-connection-manager.md)|[Éditeur du gestionnaire de connexions HTTP &#40;page Serveur&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)<br /><br /> [Éditeur du gestionnaire de connexions HTTP &#40;page Proxy&#41;](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)|  
    |[Gestionnaire de connexions MSMQ](connection-manager/msmq-connection-manager.md)|[Éditeur du gestionnaire de connexions MSMQ](../../2014/integration-services/msmq-connection-manager-editor.md)|  
    |[Gestionnaire de connexions ODBC](connection-manager/odbc-connection-manager.md)|[Informations de référence sur l’interface utilisateur du gestionnaire de connexions ODBC](../../2014/integration-services/odbc-connection-manager-ui-reference.md)|  
    |[Gestionnaire de connexions OLE DB](connection-manager/ole-db-connection-manager.md)|[Configurer le gestionnaire de connexions OLE DB](configure-ole-db-connection-manager.md)|  
    |[Gestionnaire de connexions SMO](connection-manager/smo-connection-manager.md)|[Éditeur du gestionnaire de connexions SMO](../../2014/integration-services/smo-connection-manager-editor.md)|  
    |[Gestionnaire de connexions SMTP](connection-manager/smtp-connection-manager.md)|[Éditeur du gestionnaire de connexions SMTP](../../2014/integration-services/smtp-connection-manager-editor.md)|  
    |[Gestionnaire de connexions de SQL Server Compact Edition](connection-manager/sql-server-compact-edition-connection-manager.md)|[Éditeur du gestionnaire de connexions SQL Server Compact Edition &#40;page Connexion&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)<br /><br /> [Éditeur du gestionnaire de connexions SQL Server Compact Edition &#40;page Tout&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-all-page.md)|  
    |[Gestionnaire de connexions WMI](connection-manager/wmi-connection-manager.md)|[Éditeur du gestionnaire de connexions WMI](../../2014/integration-services/wmi-connection-manager-editor.md)|  
  
     Le gestionnaire de connexions que vous avez ajouté apparaîtra sous le nœud **Gestionnaires de connexions** dans **l’Explorateur de solutions**. Il figurera aussi sous l’onglet **Gestionnaires de connexions** de la fenêtre **Concepteur SSIS** pour tous les packages du projet. Le nom du gestionnaire de connexions de cet onglet aura un préfixe **(project)** afin de distinguer ce gestionnaire de connexions de niveau projet des gestionnaires de connexions de niveau package.  
  
4.  Le cas échéant, cliquez avec le bouton droit sur le gestionnaire de connexions dans la fenêtre **Explorateur de solutions** sous le nœud **Gestionnaires de connexions** (ou) sous l’onglet **Gestionnaires de connexions** de la fenêtre **Concepteur SSIS** , cliquez **Renommer**, puis modifiez le nom par défaut du gestionnaire de connexions.  
  
    > [!NOTE]  
    >  Sous l’onglet **Gestionnaires de connexions** de la fenêtre **Concepteur SSIS**, vous ne pouvez pas remplacer le préfixe **(project)** dans le nom du gestionnaire de connexions. C'est la procédure normale.  
  
##  <a name="parameter"></a> Pour créer un paramètre pour une propriété de gestionnaire de connexions  
  
1.  Dans la zone **Gestionnaires de connexions** , cliquez avec le bouton droit sur le gestionnaire de connexions pour lequel vous souhaitez créer un paramètre, puis cliquez sur **Paramétrer**.  
  
2.  Configurez les paramètres dans la boîte de dialogue **Paramétrer** . Pour plus d’informations, consultez [Paramétrer (boîte de dialogue)](../../2014/integration-services/parameterize-dialog-box.md).  
  
##  <a name="DeletePackageLevel"></a> Pour supprimer un gestionnaire de connexions d’un package  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , cliquez sur l’onglet **Flux de contrôle** , **Flux de données** ou **Gestionnaire d’événements** pour rendre la zone **Gestionnaires de connexions** disponible.  
  
4.  Cliquez avec le bouton droit sur le gestionnaire de connexions à supprimer, puis cliquez sur **Supprimer**.  
  
     Si vous supprimez un gestionnaire de connexions utilisé par un élément de package tel qu'une tâche d'exécution SQL ou une source OLE DB, vous obtiendrez les résultats suivants :  
  
    -   Une icône d'erreur apparaît sur l'élément de package qui a utilisé le gestionnaire de connexions supprimé.  
  
    -   Échec de validation du package.  
  
    -   Impossible d’exécuter le package.  
  
5.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
##  <a name="DeleteProjectLevel"></a> Pour supprimer un gestionnaire de connexions partagé (Gestionnaire de connexions de niveau projet)  
  
1.  Pour supprimer un gestionnaire de connexions de niveau projet, cliquez avec le bouton droit sur le gestionnaire de connexions sous le nœud **Gestionnaires de connexions** dans la fenêtre **Explorateur de solutions** , puis cliquez **Supprimer**. [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] affiche le message d’avertissement suivant :  
  
    > [!WARNING]  
    >  Lorsque vous supprimez un gestionnaire de connexions au niveau projet, les packages qui utilisent le gestionnaire de connexions peuvent ne pas s'exécuter. Vous ne pouvez pas annuler cette action. Voulez -vous supprimer le gestionnaire de connexions ?  
  
2.  Cliquez sur OK pour supprimer le gestionnaire de connexions ou sur Annuler pour le conserver.  
  
    > [!NOTE]  
    >  Vous pouvez aussi supprimer un gestionnaire de connexions de niveau projet sous l’onglet **Gestionnaire de connexions** de la fenêtre **Concepteur SSIS** ouverte pour un package du projet. Pour ce faire, cliquez avec le bouton droit sur le nom du gestionnaire de connexions figurant sous l’onglet, puis cliquez sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Connexions Integration Services &#40;SSIS&#41;](connection-manager/integration-services-ssis-connections.md)   
 [Définir les propriétés d’un gestionnaire de connexions](../../2014/integration-services/set-the-properties-of-a-connection-manager.md)  
  
  
