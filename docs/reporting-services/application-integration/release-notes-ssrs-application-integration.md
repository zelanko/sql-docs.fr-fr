---
title: Notes de publication des contrôles Visionneuse de rapports de SSRS
ms.date: 09/20/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
ms.reviewer: maggies
author: RhysSchmidtke
ms.author: rhys
ms.openlocfilehash: d6c7130e45e535ad1849bed5713313bf6f89020f
ms.sourcegitcommit: 071065bc5433163ebfda4fdf6576349f9d195663
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71923811"
---
# <a name="release-notes-for-the-report-viewer-controls-for-webforms-and-winforms-of-ssrs"></a>Notes de publication pour les contrôles de visionneuse de rapports pour WebForms et WinForms de SSRS

Voici les notes de publication pour les contrôles de la visionneuse de rapports de WebForms et WinForms, en rapport avec [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (SSRS).

Pour les notes de publication de SSRS, consultez [notes de publication pour SQL Server Reporting Services (SSRS) 2017 et versions ultérieures](../release-notes-reporting-services.md).

## <a name="15013580"></a>150.1358.0
| Modifier la description | Détails |
| :----------------- | :------ |
| Correctifs de bogues | Restauration d’une modification qui a supprimé les assemblys Microsoft. ReportViewer. Design des références de projet. |
|           | Dans le cadre des autres modifications, deux assemblys ont été modifiés de la version 15,0 à 15,3. Cela a été rétabli. |
| &nbsp; | &nbsp; |

## <a name="15013570"></a>150.1357.0
| Modifier la description | Détails |
| :----------------- | :------ |
| Correctifs de bogues  | Aperçu avant impression correct pour moniteur haute résolution |
|            | La boîte de dialogue Imprimer s’affiche en dehors de l’espace visible |
|            | Un grand nombre de paramètres entraînait des barres de défilement de paramètres et des listes déroulantes ne fonctionnaient pas correctement |
|            | Résolution du problème avec les paramètres null et date/heure |
|            | JQuery mis à jour vers la version 3.3.1 |
|            | Correction du chevauchement des cellules de tableau matriciel dans le rendu HTML |
|            | Suppression des références de projet au moment de la conception pour éliminer les assemblys Visual Studio erronés ajoutés aux projets |
|            | Correction de l’accessibilité pour la barre d’outils pour la narration uniquement pour les éléments actifs |
| &nbsp; | &nbsp; |

## <a name="15900148"></a>15.900.148

| Modifier la description | Détails |
| :----------------- | :------ |
| Correctif d’un bogue empêchant le chargement des rapports sans paramètres via **Server.LoadReportDefinition**. | &nbsp; |
| Contrôle WebForms Visionneuse de rapports. | Prise en charge de l’incorporation dans les pages de droite à gauche (pages qui changent le flux de texte à l’aide de la propriété CSS *direction:rtl;* ).<br/><br/>Prise en charge de la personnalisation du texte de la boîte de dialogue Imprimer via l’interface de localisation *IReportViewerMessages5*.<br/><br/>Amélioration de la prise en charge de l’accessibilité.<br/><br/>&bull; &nbsp; &nbsp; [package NuGet pour le contrôle de la visionneuse de rapports de WebForms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Webforms/150.900.148) |
| Contrôle WinForms Visionneuse de rapports. | Correctif pour l’impression quand une application s’exécute en mode Haute résolution.<br/><br/>&bull; &nbsp; &nbsp; [package NuGet pour le contrôle de la visionneuse de rapports de WinForms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Winforms/150.900.148) |
| &nbsp; | &nbsp; |

## <a name="next-steps"></a>Étapes suivantes

[Bien démarrer](integrating-reporting-services-using-reportviewer-controls-get-started.md) avec les contrôles Visionneuse de rapports.

D’autres questions ? [Essayez le forum Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
