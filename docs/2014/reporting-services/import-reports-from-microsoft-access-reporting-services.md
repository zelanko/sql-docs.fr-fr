---
title: Importer des rapports à partir de Microsoft Access (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
author: maggiesmsft
ms.author: maghan
manager: kfile
ms.openlocfilehash: 84f74f51879a777ea0b9874f1b124806c109e02f
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56022190"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a>Importer des rapports depuis Microsoft Access (Reporting Services)
  Dans le Concepteur de rapports, vous pouvez importer des rapports à partir d’un [!INCLUDE[msCoName](../includes/msconame-md.md)] base de données Access ou un projet. Microsoft Access 2002 (ou version ultérieure) doit être installé sur le même ordinateur que le Concepteur de rapports.  
  
 Lorsque vous utilisez la fonctionnalité d'importation, tous les états contenus dans le fichier de base de données ou de projet sont importés. Si votre fichier Access contient plusieurs états, vous pouvez créer un projet de rapport séparé dans lequel importer les états, puis ouvrir les fichiers RDL individuels dans votre projet de rapport principal. Vous pouvez modifier les états après les avoir importés dans le Concepteur de rapports.  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne prend pas en charge tous les objets de rapport Access. Les éléments qui ne sont pas convertis sont affichés dans le **liste des tâches** fenêtre. Pour plus d’informations, consultez [fonctionnalités des états Access prises en charge &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md).  
  
### <a name="to-import-reports-from-microsoft-access"></a>Pour importer des rapports à partir de Microsoft Access  
  
1.  Ouvrez ou créez un projet dans lequel importer les rapports.  
  
2.  Sur le **projet** menu, pointez sur **importer des rapports**, puis cliquez sur **Microsoft Access**. Sinon, cliquez sur le projet dans l’Explorateur de solutions, pointez sur **importer des rapports**, puis cliquez sur **Microsoft Access**.  
  
3.  Dans le **Open** boîte de dialogue, sélectionnez la base de données Access (.mdb, .accdb) ou un projet (.adp) qui contient les rapports, puis cliquez sur **Open**. Tous les rapports contenus dans le fichier de base de données ou de projet sont importés et répertoriés dans le dossier Rapports de l'Explorateur de solutions.  
  
4.  Vérifier le **liste des tâches** fenêtre pour les erreurs de build. Pour afficher le **liste des tâches** fenêtre, ouvrez le **vue** menu, pointez sur **Windows autres**, puis cliquez sur **liste des tâches**.  
  
## <a name="see-also"></a>Voir aussi  
 [Concevoir des rapports à l’aide du Concepteur de rapports &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
