---
title: Définir les propriétés d’un gestionnaire de connexions | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], modifying
- modifying connection managers
ms.assetid: 54793114-2198-4d80-8091-e241d5a5d13c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0148cca6701db9f28ed6dd7abccb1a1f00269510
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48111858"
---
# <a name="set-the-properties-of-a-connection-manager"></a>Définir les propriétés d’un gestionnaire de connexions
  Tous les gestionnaires de connexions peuvent être configurés à l'aide de la fenêtre **Propriétés** .  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fournit également des boîtes de dialogue personnalisées permettant de modifier les différents types de gestionnaires de connexions dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. La boîte de dialogue offre un ensemble d'options différent pour chaque type de gestionnaire de connexions.  
  
### <a name="to-modify-a-connection-manager-using-the-properties-window"></a>Pour modifier un gestionnaire de connexions à l'aide de la fenêtre Propriétés  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Dans le concepteur SSIS, cliquez sur l’onglet **Flux de contrôle** , l’onglet **Flux de données** ou l’onglet **Gestionnaire d’événements** pour rendre la zone **Gestionnaires de connexions** disponible.  
  
4.  Cliquez avec le bouton droit sur le gestionnaire de connexions, puis sur **Propriétés**.  
  
5.  Dans la fenêtre **Propriétés** , modifiez les valeurs de propriété. La fenêtre **Propriétés** offre un accès à des propriétés non configurables dans l’éditeur standard d’un gestionnaire de connexions.  
  
6.  Cliquez sur **OK**.  
  
7.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
### <a name="to-modify-a-connection-manager-using-a-connection-manager-dialog-box"></a>Pour modifier un gestionnaire de connexions à l'aide d'une boîte de dialogue de gestionnaire de connexions  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , cliquez sur l’onglet **Flux de contrôle** , **Flux de données** ou **Gestionnaire d’événements** pour rendre la zone **Gestionnaires de connexions** disponible.  
  
4.  Dans la zone **Gestionnaires de connexions** , double-cliquez sur le gestionnaire de connexions pour ouvrir la boîte de dialogue **Gestionnaire de connexions** . Pour plus d'informations sur les types spécifiques de gestionnaires de connexions et les options disponibles pour chaque type, consultez le tableau suivant.  
  
    |Gestionnaire de connexions|Options|  
    |------------------------|-------------|  
    |[Gestionnaire de connexions ADO](connection-manager/ado-connection-manager.md)|[Configurer le gestionnaire de connexions OLE DB](configure-ole-db-connection-manager.md)|  
    |[Gestionnaire de connexions ADO.NET](connection-manager/ado-net-connection-manager.md)|[Configurer le gestionnaire de connexions ADO.NET](configure-ado-net-connection-manager.md)|  
    |[Gestionnaire de connexions Analysis Services](connection-manager/analysis-services-connection-manager.md)|[Référence de l’interface utilisateur de la boîte de dialogue Ajout d’un gestionnaire de connexions Analysis Services](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)|  
    |[Gestionnaire de connexions Excel](connection-manager/excel-connection-manager.md)|[Éditeur du gestionnaire de connexions Excel](../../2014/integration-services/excel-connection-manager-editor.md)|  
    |[Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md)|[Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)|  
    |[Gestionnaire de connexions de fichiers multiples](connection-manager/multiple-files-connection-manager.md)|[Référence de l’interface utilisateur de la boîte de dialogue Ajouter un gestionnaire de connexions de fichiers](connection-manager/add-file-connection-manager-dialog-box-ui-reference.md)|  
    |[Gestionnaire de connexions de fichiers plats](connection-manager/flat-file-connection-manager.md)|[Éditeur du gestionnaire de connexions de fichiers plats &#40;page Général&#41;](general-page-of-integration-services-designers-options.md)<br /><br /> [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Colonnes&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)<br /><br /> [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Avancé&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)<br /><br /> [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Aperçu&#41;](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)|  
    |[Gestionnaire de connexions de fichiers plats multiples](connection-manager/multiple-flat-files-connection-manager.md)|[Éditeur du Gestionnaire de connexions de fichiers plats multiples &#40;Page Général&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-general-page.md)<br /><br /> [Éditeur du Gestionnaire de connexions de fichiers plats multiples &#40;Page colonnes&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md)<br /><br /> [Éditeur du Gestionnaire de connexions de fichiers plats multiples &#40;Page avancé&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md)<br /><br /> [Éditeur du Gestionnaire de connexions de fichiers plats multiples &#40;afficher un aperçu de la Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)|  
    |[Gestionnaires de connexions FTP](connection-manager/ftp-connection-manager.md)|[Éditeur du gestionnaire de connexions FTP](../../2014/integration-services/ftp-connection-manager-editor.md)|  
    |[Gestionnaire de connexions HTTP](connection-manager/http-connection-manager.md)|[Éditeur du Gestionnaire de connexions HTTP &#40;Page du serveur&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)<br /><br /> [Éditeur du Gestionnaire de connexions HTTP &#40;Page Proxy&#41;](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)|  
    |[Gestionnaire de connexions MSMQ](connection-manager/msmq-connection-manager.md)|[Éditeur du gestionnaire de connexions MSMQ](../../2014/integration-services/msmq-connection-manager-editor.md)|  
    |[Gestionnaire de connexions ODBC](connection-manager/odbc-connection-manager.md)|[Informations de référence sur l’interface utilisateur du gestionnaire de connexions ODBC](../../2014/integration-services/odbc-connection-manager-ui-reference.md)|  
    |[Gestionnaire de connexions OLE DB](connection-manager/ole-db-connection-manager.md)|[Configurer le gestionnaire de connexions OLE DB](configure-ole-db-connection-manager.md)|  
    |[Gestionnaire de connexions SMO](connection-manager/smo-connection-manager.md)|[Éditeur du gestionnaire de connexions SMO](../../2014/integration-services/smo-connection-manager-editor.md)|  
    |[Gestionnaire de connexions SMTP](connection-manager/smtp-connection-manager.md)|[Éditeur du gestionnaire de connexions SMTP](../../2014/integration-services/smtp-connection-manager-editor.md)|  
    |[Gestionnaire de connexions de SQL Server Compact Edition](connection-manager/sql-server-compact-edition-connection-manager.md)|[SQL Server Compact Edition Connection Manager Editor &#40;Page de connexion&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)<br /><br /> [SQL Server Compact Edition Connection Manager Editor &#40;Page toutes les&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-all-page.md)|  
    |[Gestionnaire de connexions WMI](connection-manager/wmi-connection-manager.md)|[Éditeur du gestionnaire de connexions WMI](../../2014/integration-services/wmi-connection-manager-editor.md)|  
  
5.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Connexions Integration Services &#40;SSIS&#41;](connection-manager/integration-services-ssis-connections.md)   
 [Ajouter, supprimer ou partager un gestionnaire de connexions dans un package](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)  
  
  
