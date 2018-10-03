---
title: Lier un rapport à une source de données partagée (SSRS) | Microsoft Docs
ms.date: 05/24/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-data
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c93c32d70ccc2cf1180b44e16c5983d584b2b19b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616068"
---
# <a name="bind-a-report-to-a-shared-data-source-ssrs"></a>Lier un rapport à une source de données partagée (SSRS)
  Dans certaines situations, par exemple si vous déplacez un rapport d’un serveur test vers un serveur de production, vous pouvez envisager d’enregistrer le fichier sur votre ordinateur local puis de le télécharger sur un autre serveur de rapports. Si vous téléchargez le rapport sur le nouveau serveur, vous devez le lier de nouveau à une source de données partagée stockée sur le nouveau serveur de rapports. Si vous ne liez pas de nouveau le rapport, celui-ci ne fonctionnera pas correctement en cas d’accès à partir du nouveau serveur de rapports.  
  
> [!IMPORTANT]  
>  Avant de procéder à cette opération, la source de données doit déjà exister sur le serveur de rapports ou la bibliothèque SharePoint. Pour plus d’informations sur les sources de données, consultez [Créer, modifier, puis supprimer des sources de données partagées &#40;SSRS&#41;](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md).  
  
## <a name="to-bind-a-report-to-a-shared-data-source-on-a-report-server-running-in-native-mode"></a>Pour lier un rapport à une source de données partagée sur un serveur de rapports s’exécutant en mode natif  
  
1.  Dans le portail web, cliquez sur les points de suspension (...) dans le coin supérieur droit de la vignette du rapport > **Gérer**.  

2.  Cliquez sur **Sources de données**.  
  
3.  Cliquez sur **Source de données partagée**, puis accédez à la source de données à laquelle vous souhaitez lier le rapport.  
  
4.  Sélectionnez la source de données, puis cliquez sur **Enregistrer**.  
  
5.  Cliquez sur **Appliquer**.  
  
     Le rapport est désormais lié à une source de données que vous avez sélectionnée.  
  
## <a name="to-bind-a-report-to-a-shared-data-source-on-a-report-server-running-in-sharepoint-integrated-mode"></a>Pour lier un rapport à une source de données partagée sur un serveur de rapports s’exécutant en mode intégré SharePoint  
  
1.  Si la bibliothèque n'est pas déjà ouverte, cliquez sur son nom dans la barre de lancement rapide. Si le nom de la bibliothèque n'est pas visible, cliquez sur **Afficher tout le contenu du site**, puis sur le nom de la bibliothèque.  
  
2.  Pointez sur le rapport, puis cliquez sur la flèche orientée vers le bas.  
  
3.  Cliquez sur **Gérer les sources de données**.  
  
4.  Cliquez sur **dataSource1**.  
  
5.  Dans la zone **Type de connexion** , vérifiez que **Source de données partagée** est activée.  
  
6.  Dans la zone **Lien de source de données** , cliquez sur le bouton (...).  
  
7.  Localisez la source de données que vous souhaitez utiliser.  
  
8.  Sélectionnez la source de données et cliquez sur **OK**.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. Cliquez sur **Fermer**.  
  
## <a name="see-also"></a> Voir aussi  
 [Télécharger des documents vers une bibliothèque SharePoint &#40;Reporting Services en mode SharePoint&#41;](../../reporting-services/report-server-sharepoint/upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)   
 [Créer et gérer des sources de données partagées &#40;Reporting Services en mode intégré SharePoint&#41;](http://msdn.microsoft.com/library/2d3428e4-a810-4e66-a287-ff18e57fad76)   
 [Connexions de données, sources de données et chaînes de connexion &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)  
  
  
