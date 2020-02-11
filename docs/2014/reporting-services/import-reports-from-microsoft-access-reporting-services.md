---
title: Importer des rapports à partir de Microsoft Access (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 862d8b90f3c91dffda35971677db7fdc231c1b63
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108930"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a>Importer des rapports depuis Microsoft Access (Reporting Services)
  Dans Concepteur de rapports, vous pouvez importer des rapports à [!INCLUDE[msCoName](../includes/msconame-md.md)] partir d’une base de données ou d’un projet Access. Microsoft Access 2002 (ou version ultérieure) doit être installé sur le même ordinateur que le Concepteur de rapports.  
  
 Lorsque vous utilisez la fonctionnalité d'importation, tous les états contenus dans le fichier de base de données ou de projet sont importés. Si votre fichier Access contient plusieurs états, vous pouvez créer un projet de rapport séparé dans lequel importer les états, puis ouvrir les fichiers RDL individuels dans votre projet de rapport principal. Vous pouvez modifier les états après les avoir importés dans le Concepteur de rapports.  
  
> [!NOTE]  
>  
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne prend pas en charge tous les objets de rapport Access. Les éléments qui ne sont pas convertis sont affichés dans la fenêtre **liste des tâches** . Pour plus d’informations, consultez [fonctionnalités de rapport d’accès prises en charge &#40;&#41;SSRS ](../../2014/reporting-services/supported-access-report-features-ssrs.md).  
  
### <a name="to-import-reports-from-microsoft-access"></a>Pour importer des rapports à partir de Microsoft Access  
  
1.  Ouvrez ou créez un projet dans lequel importer les rapports.  
  
2.  Dans le menu **projet** , pointez sur **importer des rapports**, puis cliquez sur **Microsoft Access**. Vous pouvez également cliquer avec le bouton droit sur le projet dans Explorateur de solutions, pointer sur **importer des rapports**, puis cliquer sur **Microsoft Access**.  
  
3.  Dans la boîte de dialogue **ouvrir** , sélectionnez la base de données Access (. mdb,. accdb) ou le projet (. ADP) qui contient les rapports, puis cliquez sur **ouvrir**. Tous les rapports contenus dans le fichier de base de données ou de projet sont importés et répertoriés dans le dossier Rapports de l'Explorateur de solutions.  
  
4.  Recherchez les erreurs de génération dans la fenêtre **liste des tâches** . Pour afficher la fenêtre de **liste des tâches** , ouvrez le menu **affichage** , pointez sur **autres fenêtres**, puis cliquez sur **liste des tâches**.  
  
## <a name="see-also"></a>Voir aussi  
 [Concevoir des rapports à l’aide du Concepteur de rapports &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
