---
title: Télécharger des Documents vers une bibliothèque SharePoint (Reporting Services en Mode SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- SharePoint integration [Reporting Services], content management
- uploading reports [Reporting Services]
ms.assetid: 93bd1b19-061b-409f-8dc2-ec416b2f4b39
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 65f3388137c4fe26e1fcc51c11711944c89bd0c8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37295879"
---
# <a name="upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode"></a>Télécharger des documents vers une bibliothèque SharePoint (Reporting Services en mode SharePoint)
  Vous pouvez télécharger des définitions de rapport et des modèles de rapport vers une bibliothèque SharePoint. Lorsque vous téléchargez un élément du serveur de rapports, vous devez sélectionner une bibliothèque ou un dossier dans une bibliothèque. Vous ne pouvez pas télécharger un élément de serveur de rapports vers une liste ou une page.  
  
 Vous ne pouvez pas télécharger de fichier de source de données (.rds). Toutefois, vous pouvez publier des fichiers .rds à partir d'un outil de conception, par exemple le Concepteur de rapports, vers une bibliothèque SharePoint. Au cours de la publication, un nouveau fichier .rsds est créé à partir du fichier .rds original dans la solution. Vous pouvez également créer un nouveau fichier .rsds dans une bibliothèque SharePoint, puis définir les propriétés de connexion à la source de données dans les rapports et les modèles téléchargés pour utiliser la nouvelle connexion.  
  
> [!NOTE]  
>  Le serveur de rapports doit être configuré pour le mode SharePoint ; par ailleurs, l'instance du produit SharePoint doit posséder le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] qui fournit les fichiers programme pour le stockage des éléments du serveur de rapports et leur accès à partir d'un site SharePoint.  
  
 Pour télécharger un document vers une bibliothèque, vous devez disposer de l'autorisation « Ajouter des éléments » au niveau du site. Si vous utilisez les paramètres de sécurité par défaut, cette autorisation est accordée aux membres du groupe **Propriétaires** qui disposent du niveau d’autorisation Contrôle total et aux membres du groupe **Membres** qui disposent du niveau d’autorisation Contribuer.  
  
### <a name="to-add-a-report-definition-or-report-model-to-a-library"></a>Pour ajouter une définition ou un modèle de rapport dans une bibliothèque  
  
1.  Ouvrez la bibliothèque ou un dossier dans une bibliothèque. Si la bibliothèque n'est pas ouverte, cliquez sur son nom dans le menu de lancement rapide. Si le nom de la bibliothèque n'est pas visible, cliquez sur **Afficher tout le contenu du site**, puis sur le nom de la bibliothèque.  
  
2.  Dans le menu **Télécharger** , cliquez sur **Télécharger un document**.  
  
3.  Pour télécharger un fichier de rapport ou de modèle de rapport unique, sélectionnez un fichier de définition de rapport (.rdl) ou de modèle de rapport (.smdl), puis cliquez sur **OK**.  
  
     Si la définition de rapport utilise un fichier de source de données partagée (.rsds) pour stocker les informations de connexion à une source de données externe, vous pouvez télécharger les fichiers .rdl et .rsds au même moment. Pour cela, cliquez sur **Télécharger plusieurs fichiers**, spécifiez les deux fichiers, puis cliquez sur **OK**.  
  
 Si vous téléchargez un rapport qui contient des références à des sources de données partagées, à des modèles de rapport ou à des sous-rapports, les références seront rompues dans le rapport lors du téléchargement des fichiers. Pour plus d’informations sur la réinitialisation des références, consultez [Créer et gérer des sources de données partagées &#40;Reporting Services en mode intégré SharePoint&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).  
  
 Lorsque vous téléchargez un rapport, il s'exécute à la demande lorsque vous l'ouvrez, récupérant les données actives à partir de la source de données. Vous pouvez configurer le rapport pour récupérer des données suivant une planification ou utiliser les données mises en cache. Pour plus d’informations, consultez [Définir les options de traitement &#40;Reporting Services en mode intégré SharePoint&#41;](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).  
  
 Un rapport peut contenir des paramètres permettant aux utilisateurs de filtrer les données. Vous pouvez configurer les paramètres pour utiliser des valeurs spécifiques ou modifier la manière dont elles apparaissent à l'utilisateur. Pour plus d’informations, consultez [Définir les paramètres sur un rapport publié &#40;Reporting Services en mode intégré SharePoint&#41;](report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Publier un rapport dans une bibliothèque SharePoint](reports/publish-a-report-to-a-sharepoint-library.md)   
 [Publier une source de données partagée sur une bibliothèque SharePoint](reports/publish-a-shared-data-source-to-a-sharepoint-library.md)   
 [Accord d'autorisations sur des éléments de serveur de rapports sur un site SharePoint](security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
  
  
