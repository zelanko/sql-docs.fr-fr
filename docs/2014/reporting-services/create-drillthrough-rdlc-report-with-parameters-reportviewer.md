---
title: Créer un rapport d’extraction (RDLC) avec des paramètres à l’aide de ReportViewer (didacticiel SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 189c1edbd491eceb7849c90ed917e19e7720fe27
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56018061"
---
# <a name="create-a-drillthrough-rdlc-report-with-parameters-using-reportviewer-ssrs-tutorial"></a>Créer un rapport d'extraction (RDLC) avec des paramètres à l'aide de ReportViewer (didacticiel SSRS)
  Un rapport [d’extraction](https://technet.microsoft.com/library/ff519554.aspx) est un rapport que l’utilisateur ouvre en cliquant sur un lien situé dans un autre rapport. Il contient en général des détails sur un élément figurant dans le rapport de synthèse d'origine. Ce didacticiel vous guide tout au long des leçons suivantes pour créer un rapport d’extraction avec des paramètres et une requête, en [mode local](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md).  
  
## <a name="requirements"></a>Configuration requise  
 Pour utiliser cette procédure pas à pas, vous devez avoir accès à la **AdventureWorks2008** base de données exemple. La requête utilisée dans cette procédure pas à pas fonctionne également avec **AdventureWorks2012** base de données. Pour plus d’informations sur la façon d’obtenir le **AdventureWorks2008** exemple de base de données, consultez [procédure pas à pas : L’installation de la base de données AdventureWorks](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx) pour Microsoft Visual Studio 2010.  
  
 Cette procédure pas à pas part du principe que vous connaissez les requêtes Transaction-SQL et les objets ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) et [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) .  
  
 Utilisez Visual Studio 2010 ou Visual Studio 2012, ainsi que le modèle de site Web ASP.NET. pour créer une page Web ASP.NET avec un contrôle ReportViewer. Le contrôle est configuré en vue d'afficher un rapport que vous créez. Pour cette procédure pas à pas, vous créez l'application dans Microsoft Visual C#.  
  
## <a name="tasks"></a>Tâches  
 [Leçon 1 : Créer un nouveau Site Web](../reporting-services/lesson-1-create-a-new-web-site.md)   
 [Leçon 2 : Définir une connexion de données et la Table de données pour le rapport Parent](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)   
 [Leçon 3 : Concevoir le rapport Parent à l’aide de l’Assistant rapport](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md)   
 [Leçon 4 : Définir une connexion de données et la Table de données pour le rapport enfant](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md)   
 [Leçon 5 : Concevoir le rapport enfant à l’aide de l’Assistant rapport](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md)   
 [Leçon 6 : Ajouter un contrôle ReportViewer à l’Application](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md)   
 [Leçon 7 : Ajouter l’Action d’extraction dans le rapport Parent](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md)   
 [Leçon 8 : Créer un filtre de données](../reporting-services/lesson-8-create-a-data-filter.md)   
 [Leçon 9 : Générer et exécuter l’Application](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels sur Reporting Services &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md)   
 [Concevoir des rapports à l’aide du Concepteur de rapports &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
