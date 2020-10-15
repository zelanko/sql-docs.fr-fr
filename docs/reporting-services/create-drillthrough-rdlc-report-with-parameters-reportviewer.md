---
title: Créer un rapport d’extraction (RDLC) avec des paramètres - ReportViewer | Microsoft Docs
description: Découvrez comment créer un rapport d’extraction (RDLC) avec des paramètres et une requête dans le cadre d’une création de rapport en mode local.
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7f6e6e631b32aa7eab8d6c56c8b6f9e2cf03752f
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91891199"
---
# <a name="create-drillthrough-rdlc-report-with-parameters---reportviewer"></a>Créer un rapport d’extraction (RDLC) avec des paramètres - ReportViewer
Un rapport [d’extraction](./report-design/drillthrough-reports-report-builder-and-ssrs.md) est un rapport que l’utilisateur ouvre en cliquant sur un lien situé dans un autre rapport. Il contient en général des détails sur un élément figurant dans le rapport de synthèse d'origine. Ce tutoriel vous guide tout au long des leçons suivantes pour créer un rapport d’extraction avec des paramètres et une requête, en [mode local](report-server-sharepoint/local-mode-vs-connected-mode-reports-in-the-report-viewer.md).  
  
## <a name="requirements"></a>Spécifications  
Pour suivre cette procédure pas à pas, vous devez avoir accès à l’exemple de base de données **AdventureWorks2014** . Pour plus d’informations sur la façon d’obtenir l’exemple de base de données **AdventureWorks2014**, consultez [Exemples de bases de données AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases).  
  
Cette procédure pas à pas part du principe que vous connaissez les requêtes Transaction-SQL et les objets ADO.NET [DataSet](/dotnet/api/system.data.dataset) et [DataTable](/dotnet/api/system.data.datatable) .  
  
Utilisez Visual Studio 2015 et l’application web ASP.NET pour créer une page web ASP.NET avec un contrôle ReportViewer. Le contrôle est configuré en vue d'afficher un rapport que vous créez. Pour cette procédure pas à pas, vous créez l'application dans Microsoft Visual C#.  
  
## <a name="tasks"></a>Tâches  
[Leçon 1 : Créer un site web](../reporting-services/lesson-1-create-a-new-web-site.md)  
[Leçon 2 : Définir une connexion de données et une table de données pour le rapport parent](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)  
[Leçon 3 : Concevoir le rapport parent à l’aide de l’Assistant Rapport](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md)  
[Leçon 4 : Définir une connexion de données et une table de données pour le rapport enfant](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md)  
[Leçon 5 : Concevoir le rapport enfant à l’aide de l’Assistant Rapport](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md)  
[Leçon 6 : Ajouter un contrôle ReportViewer à l’application](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md)  
[Leçon 7 : Ajouter une action d’extraction dans le rapport parent](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md)  
[Leçon 8 : Créer un filtre de données](../reporting-services/lesson-8-create-a-data-filter.md)  
[Leçon 9 : Générer et exécuter l’application](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a>Voir aussi  
[Didacticiels sur Reporting Services &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md)  
[Concevoir des rapports à l’aide du Concepteur de rapports &#40;SSRS&#41;](../reporting-services/tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
