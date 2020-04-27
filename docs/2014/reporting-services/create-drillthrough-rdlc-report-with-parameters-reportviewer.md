---
title: Créer un rapport d’extraction (RDLC) avec des paramètres à l’aide de ReportViewer (didacticiel SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7efb713b5dbf9a3f19118bb3572ccd35778aad19
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109647"
---
# <a name="create-a-drillthrough-rdlc-report-with-parameters-using-reportviewer-ssrs-tutorial"></a>Créer un rapport d'extraction (RDLC) avec des paramètres à l'aide de ReportViewer (didacticiel SSRS)
  Un rapport [d’extraction](https://technet.microsoft.com/library/ff519554.aspx) est un rapport que l’utilisateur ouvre en cliquant sur un lien situé dans un autre rapport. Il contient en général des détails sur un élément figurant dans le rapport de synthèse d'origine. Ce tutoriel vous guide tout au long des leçons suivantes pour créer un rapport d’extraction avec des paramètres et une requête, en [mode local](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md).  
  
## <a name="requirements"></a>Spécifications  
 Pour utiliser cette procédure pas à pas, vous devez avoir accès à l’exemple de base de données **AdventureWorks2008** . La requête utilisée dans cette procédure pas à pas fonctionne également avec la base de données **AdventureWorks2012** . Pour plus d’informations sur l’obtention de l’exemple de base de données **AdventureWorks2008** , consultez [procédure pas à pas : installation de la base de données AdventureWorks](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx) pour Microsoft Visual Studio 2010.  
  
 Cette procédure pas à pas part du principe que vous connaissez les requêtes Transaction-SQL et les objets ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) et [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) .  
  
 Utilisez Visual Studio 2010 ou Visual Studio 2012, ainsi que le modèle de site Web ASP.NET. pour créer une page Web ASP.NET avec un contrôle ReportViewer. Le contrôle est configuré en vue d'afficher un rapport que vous créez. Pour cette procédure pas à pas, vous créez l'application dans Microsoft Visual C#.  
  
## <a name="tasks"></a>Tâches  
 [Leçon 1 : créer un nouveau site Web](../reporting-services/lesson-1-create-a-new-web-site.md)   
 [Leçon 2 : définir une connexion de données et une table de données pour le rapport parent](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)   
 [Leçon 3 : concevoir le rapport parent à l’aide de l’Assistant Rapport](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md)   
 [Leçon 4 : définir une connexion de données et une table de données pour le rapport enfant](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md)   
 [Leçon 5 : concevoir le rapport enfant à l’aide de l’Assistant Rapport](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md)   
 [Leçon 6 : ajouter un contrôle ReportViewer à l’application](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md)   
 [Leçon 7 : ajouter une action d’extraction au rapport parent](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md)   
 [Leçon 8 : créer un filtre de données](../reporting-services/lesson-8-create-a-data-filter.md)   
 [Leçon 9 : Générer et exécuter l'application](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels de Reporting Services &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md)   
 [Concevoir des rapports à l’aide du Concepteur de rapports &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
