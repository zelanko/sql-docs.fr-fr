---
title: Enregistrement des rapports (Générateur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 59ddc4b8-9517-4d3f-9c88-a07e9907cecb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01fcf6ef333a9b7c8a5c99630e6e9573f70d8059
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59955245"
---
# <a name="saving-reports-report-builder"></a>Enregistrement des rapports (Générateur de rapports)
  Dans le Générateur de rapports vous avez la possibilité d'enregistrer un rapport sur un serveur de rapports, une bibliothèque SharePoint, un partage de fichiers sur lequel vous disposez d'une autorisation d'écriture, ou sur votre ordinateur. Vous pouvez enregistrer un rapport au même emplacement que celui où vous l'avez ouvert, l'enregistrer à un emplacement différent ou avec un nouveau nom au même emplacement ou à un emplacement différent. Par défaut, un rapport est réenregistré à l'emplacement où vous l'avez ouvert. Lorsque vous enregistrez le rapport, vous enregistrez en fait la définition de rapport, laquelle décrit la disposition du rapport. Les données ne sont pas enregistrées. Chaque fois que vous exécutez le rapport, les données de rapport sont actualisées et peuvent être différentes de celles obtenues lors de la dernière exécution du rapport.  
  
 Si vous souhaitez enregistrer le rapport sous un format différent ou enregistrer la définition de rapport avec les données, utilisez l'une des fonctionnalités [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] suivantes :  
  
-   Exportez un rapport rendu vers un format de fichier différent tel qu'un fichier séparé par des virgules (CSV) ou un classeur Excel et enregistrez le rapport dans ce format. Vous pouvez également générer des flux de données à partir de rapports et enregistrer les données de rapport.  
  
-   Créez des abonnements de rapport pour remettre et enregistrer des rapports sur un partage de fichiers.  
  
-   Utilisez l'historique de rapport pour enregistrer des versions de rapports rendus en tant que copies historiques.  
  
 Pour en savoir plus sur l’affichage et la gestion des rapports directement sur le serveur de rapports, consultez [Recherche, affichage et gestion des rapports &#40;Générateur de rapports et SSRS&#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) et [Serveur de rapports Reporting Services &#40;mode natif&#41;](../report-server/reporting-services-report-server-native-mode.md) dans la [documentation en ligne](https://go.microsoft.com/fwlink/?LinkId=154888) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur msdn.microsoft.com.  
  
##  <a name="SavingReportDefinitions"></a> Enregistrement des définitions de rapport  
 Bien que vous puissiez enregistrer des rapports sur votre ordinateur, l'enregistrement des rapports sur un serveur de rapports offre de nombreux avantages.  
  
 L'enregistrement d'un rapport sur un serveur de rapports offre les avantages suivants :  
  
-   Les rapports sont mis à la disposition des autres utilisateurs qui sont autorisés à accéder au dossier dans lequel vous avez enregistré le rapport.  
  
-   Les rapports peuvent être gérés et affichés depuis le Gestionnaire de rapports.  
  
-   Les ressources de rapport, telles que les sources de données, les images et les sous-rapports, sont stockées à un seul et même endroit pour un accès plus facile.  
  
-   Les rapports peuvent être remis aux autres grâce aux abonnements.  
  
-   Les rapports sont stockés en toute sécurité dans la base de données du serveur de rapports.  
  
-   Les exécutions de rapport peuvent être journalisées et fournir des informations d'audit et de performance.  
  
 L'enregistrement d'un rapport sur un serveur de rapports est également appelé « publication » d'un rapport. Lorsque vous enregistrez le rapport, seule la définition de rapport est enregistrée. Chaque fois que vous exécutez le rapport, les données de rapport sont actualisées et peuvent être différentes de celles obtenues lors de la dernière exécution du rapport. Si vous souhaitez enregistrer la définition de rapport avec les données, vous devez utiliser la fonctionnalité d'historique de rapport. Grâce à cette fonctionnalité, vous enregistrez une copie du rapport avec ses données.  
  

  
##  <a name="ExportingAndSavingReports"></a> Exportation et enregistrement des rapports  
 Si vous avez un petit nombre de rapports à archiver, optez pour la solution consistant à exporter un rapport puis à l'enregistrer dans un fichier. Une fois que vous avez exporté un rapport vers une application (au format PDF ou Excel par exemple), vous pouvez l'enregistrer en tant que fichier et le placer dans un répertoire partagé protégé sur le réseau. Vous pouvez également télécharger le fichier enregistré au format PDF ou Excel en tant qu'élément de ressource si vous souhaitez conserver toutes les copies d'un rapport, quel que soit leur format, dans la base de données du serveur de rapports. Pour plus d’informations sur l’exportation d’un rapport, consultez [exportation des rapports &#40;Générateur de rapports et SSRS&#41; ](export-reports-report-builder-and-ssrs.md) et [télécharger un fichier ou un rapport &#40;le Gestionnaire de rapports&#41;](../reports/upload-a-file-or-report-report-manager.md).  
  

  
##  <a name="UsingFileShareDelivery"></a> Utilisation de la remise par partage de fichiers  
 Si vous avez un grand nombre de rapports à archiver, créez un abonnement qui remet le rapport directement au système de fichiers. Pour cette approche, vous devez créer un abonnement pour chaque rapport, choisir un dossier partagé où stocker les rapports et définir une planification qui détermine le moment auquel le fichier est créé. Une fois l'abonnement défini, le serveur de rapports peut exécuter le rapport sans surveillance et ajouter des fichiers de rapports à l'archive à l'aide de la planification que vous fournissez. Vous pouvez également créer des planifications à usage unique si vous souhaitez archiver des rapports occasionnellement. Pour plus d'informations sur les abonnements et la remise par partage de fichiers, consultez « Remise de fichiers dans Reporting Services » dans la [documentation de Reporting Services](https://go.microsoft.com/fwlink/?linkid=121312) de la documentation en ligne de SQL Server.  
  

  
##  <a name="UsingReportHistory"></a> Utilisation de l'historique de rapport  
 Vous pouvez également utiliser la fonctionnalité d'historique de rapport pour créer des copies historiques. Vous pouvez ensuite sauvegarder la base de données du serveur de rapports, puis stocker la sauvegarde à un emplacement sûr en vue d'une utilisation future. L'ensemble de l'historique de rapport (avec les rapports, les éléments de sources de données partagées, les dossiers, les abonnements et les planifications partagées) est stocké dans la base de données du serveur de rapports. Vous pouvez créer une sauvegarde pour conserver une copie permanente de l'historique et des métadonnées d'un rapport, notamment les informations d'abonnement indiquant ses différents destinataires. Pour plus d'informations, consultez « Gestion de l'historique de rapport » dans la [documentation de Reporting Services](https://go.microsoft.com/fwlink/?linkid=121312) de la documentation en ligne de SQL Server.  
  

  
##  <a name="HowTo"></a> Rubriques de procédures  
  
-   [Enregistrer des rapports sur un serveur de rapports &#40;Générateur de rapports&#41;](save-reports-to-a-report-server-report-builder.md)  
  
-   [Enregistrer un rapport dans une bibliothèque SharePoint &#40;Générateur de rapports&#41;](save-a-report-to-a-sharepoint-library-report-builder.md)  
  
-   [Enregistrer des rapports sur votre ordinateur &#40;Générateur de rapports&#41;](../save-reports-to-your-computer-report-builder.md)  
  

  
## <a name="see-also"></a>Voir aussi  
 [Rapports, parties de rapports et définitions de rapports &#40;Générateur de rapports et SSRS&#41;](../report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md)   
 [Installer, désinstaller et prise en charge du Générateur de rapports](../install-uninstall-and-report-builder-support.md)   
 [Recherche, affichage et gestion des rapports &#40;Générateur de rapports et SSRS&#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Exportation de rapports &#40;Générateur de rapports et SSRS&#41;](export-reports-report-builder-and-ssrs.md)   
 [Imprimer des rapports &#40;Générateur de rapports et SSRS&#41;](print-reports-report-builder-and-ssrs.md)  
  
  
