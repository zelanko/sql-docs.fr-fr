---
title: Lier un rapport ou un modèle à une source de données partagée (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b6d973d4628e9c80b47c4fea0ef3476dbd05131f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66107449"
---
# <a name="bind-a-report-or-model-to-a-shared-data-source-ssrs"></a>Lier un rapport ou un modèle à une source de données partagée (SSRS)
  Dans certaines situations, par exemple si vous déplacez un rapport ou un modèle d'un serveur test vers un serveur de production, vous pouvez envisager d'enregistrer le fichier sur votre ordinateur local puis de le télécharger sur un autre serveur de rapports. Si vous téléchargez le rapport ou le modèle sur le nouveau serveur, vous devez le lier de nouveau à une source de données partagée stockée sur le nouveau serveur de rapports. Si vous ne liez pas de nouveau le rapport ou le modèle, celui-ci ne fonctionnera pas correctement en cas d'accès à partir du nouveau serveur de rapports.  
  
> [!IMPORTANT]  
>  Avant de procéder à cette opération, la source de données doit déjà exister sur le serveur de rapports ou la bibliothèque SharePoint. Pour plus d’informations sur les sources de données, consultez [Créer, modifier, puis supprimer des sources de données partagées &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md).  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-native-mode"></a>Pour lier un rapport ou un modèle à une source de données partagée sur un serveur de rapports s'exécutant en mode natif  
  
1.  Dans le **Gestionnaire de rapports**, cliquez sur le nom du rapport ou du modèle que vous avez téléchargé sur le serveur.  
  
     L'onglet Propriétés s'ouvre.  
  
2.  Cliquez sur **Sources de données**.  
  
3.  Cliquez sur **Parcourir**, puis accédez à la source de données à laquelle vous souhaitez lier le modèle ou le rapport.  
  
4.  Sélectionnez la source de données, puis cliquez sur **OK**.  
  
5.  Cliquez sur **Appliquer**.  
  
     Le rapport ou le modèle est désormais lié à une source de données que vous avez sélectionnée.  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-sharepoint-integrated-mode"></a>Pour lier un rapport ou un modèle à une source de données partagée sur un serveur de rapports s'exécutant en mode intégré SharePoint  
  
1.  Si la bibliothèque n'est pas déjà ouverte, cliquez sur son nom dans la barre de lancement rapide. Si le nom de la bibliothèque n'est pas visible, cliquez sur **Afficher tout le contenu du site**, puis sur le nom de la bibliothèque.  
  
2.  Pointez sur le rapport ou le modèle et cliquez sur la flèche orientée vers le bas.  
  
3.  Cliquez sur **Gérer les sources de données**.  
  
4.  Cliquez sur **dataSource1**.  
  
5.  Dans la zone **Type de connexion** , vérifiez que **Source de données partagée** est activée.  
  
6.  Dans la zone **Lien de source de données**, cliquez sur le bouton de sélection (...).  
  
7.  Localisez la source de données que vous souhaitez utiliser.  
  
8.  Sélectionnez la source de données et cliquez sur **OK**.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. Cliquez sur **Fermer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Télécharger un fichier ou un rapport &#40;Gestionnaire de rapports&#41;](../reports/upload-a-file-or-report-report-manager.md)   
 [Télécharger des documents vers une bibliothèque SharePoint &#40;Reporting Services en mode SharePoint&#41;](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)   
 [Créer et gérer des sources de données partagées &#40;Reporting Services en mode intégré SharePoint&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)   
 [Créer, supprimer ou modifier une source de données partagée &#40;Gestionnaire de rapports&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [Connexions de données, Sources de données et chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
