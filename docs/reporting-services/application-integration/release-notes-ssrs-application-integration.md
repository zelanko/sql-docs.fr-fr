---
title: Notes de publication des contrôles Visionneuse de rapports de SSRS
ms.date: 09/20/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
ms.reviewer: maghan
author: RhysSchmidtke
ms.author: rhys
ms.openlocfilehash: 1528358c8aff5d6e99869f0f4f8c1676ee2d5e75
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67730906"
---
# <a name="release-notes-for-the-report-viewer-controls-for-webforms-and-winforms-of-ssrs"></a>Notes de publication pour les contrôles de visionneuse de rapports pour Web Forms et WinForms de SSRS

Voici les notes de publication pour les contrôles de visionneuse de rapports de WebForms et WinForms, liés à [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (SSRS).

Pour les notes de publication pour SSRS, consultez [notes de publication pour SQL Server Reporting Services (SSRS) 2017 et versions ultérieures](../release-notes-reporting-services.md).

## <a name="15013580"></a>150.1358.0
| Description de la modification | Détails |
| :----------------- | :------ |
| Correctifs de bogues | Restaurer une modification qui a supprimé les assemblys Microsoft.ReportViewer.Design de références du projet. |
|           | Dans le cadre d’autres modifications, les deux assemblys ont été modifiées à partir de la version 15.0 pour 15.3. Cela a été rétablie. |
| &nbsp; | &nbsp; |

## <a name="15013570"></a>150.1357.0
| Description de la modification | Détails |
| :----------------- | :------ |
| Correctifs de bogues  | Bon aperçu avant impression pour l’analyse de haute résolution |
|            | Boîte de dialogue Imprimer s’affiche en dehors de l’espace visible |
|            | Grand nombre de paramètres a entraîné les barres de défilement de paramètre et les listes déroulantes ne fonctionne ne pas correctement |
|            | Correction d’un problème avec les paramètres de temps Null et date |
|            | Mise à jour de JQuery vers la version 3.3.1 |
|            | Correction de chevauchement avec les cellules de tableau matriciel dans le rendu HTML |
|            | Supprimé le moment du design projet fait référence à éliminer des assemblys VS erronées ajoutés aux projets |
|            | Accessibilité correctif pour la barre d’outils pour commenter uniquement pour les éléments actifs |
| &nbsp; | &nbsp; |

## <a name="15900148"></a>15.900.148

| Description de la modification | Détails |
| :----------------- | :------ |
| Correctif d’un bogue empêchant le chargement des rapports sans paramètres via **Server.LoadReportDefinition**. | &nbsp; |
| Contrôle WebForms Visionneuse de rapports. | Prise en charge de l’incorporation dans les pages de droite à gauche (pages qui changent le flux de texte à l’aide de la propriété CSS *direction:rtl;* ).<br/><br/>Prise en charge de la personnalisation du texte de la boîte de dialogue Imprimer via l’interface de localisation *IReportViewerMessages5*.<br/><br/>Amélioration de la prise en charge de l’accessibilité.<br/><br/>&bull; &nbsp; &nbsp; [Package NuGet pour le contrôle de visionneuse de rapports de Web Forms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Webforms/150.900.148) |
| Contrôle WinForms Visionneuse de rapports. | Correctif pour l’impression quand une application s’exécute en mode Haute résolution.<br/><br/>&bull; &nbsp; &nbsp; [Package NuGet pour le contrôle de visionneuse de rapports de WinForms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Winforms/150.900.148) |
| &nbsp; | &nbsp; |

## <a name="next-steps"></a>Étapes suivantes

[Bien démarrer](integrating-reporting-services-using-reportviewer-controls-get-started.md) avec les contrôles Visionneuse de rapports.

D’autres questions ? [Essayez le forum Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
