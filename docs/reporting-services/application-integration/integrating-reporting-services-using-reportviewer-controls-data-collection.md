---
title: "Collecte des données dans le contrôle ReportViewer version 2016 | Microsoft Docs"
ms.custom: 
ms.date: 09/06/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
caps.latest.revision: "2"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b2f5f4743b838598aeb5f74271fa063af9bb60f3
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>Intégration de Reporting Services à l’aide de contrôles ReportViewer - collecte des données
Par défaut, le contrôle ReportViewer collecte des informations d’utilisation anonymes permettant à Microsoft de mieux comprendre la façon dont les clients utilisent le contrôle. Grâce à une meilleure compréhension de la façon dont les clients déploient et utilisent le contrôle de visionneuse, il est possible de concentrer le développement futur sur les améliorations les plus intéressantes pour la majorité des clients.

Pour obtenir une explication des principes de collecte de données utilisateur et d’utilisation de la version Microsoft SQL Server 2016 et de tout autre produit et service, consultez la [déclaration de confidentialité de Microsoft](https://www.microsoft.com/EN-US/privacystatement/SQLServer/Default.aspx).

## <a name="opting-out-of-telemetry"></a>Désactivation de la télémétrie

Vous pouvez désactiver la télémétrie par programmation par le biais du paramètre «EnableTelemetry ». Pour ce faire, modifiez la page .aspx qui héberge le contrôle.

```
\<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
\</rsweb:ReportViewer>
```

Vous pouvez également effectuer la désactivation avant que le contrôle ne soit restitué, comme dans les appels de Page_Load de la page d’hébergement.
    
```
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>Voir aussi

[Utilisation du contrôle WebForms ReportViewer](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[Intégration de Reporting Services à l’aide des contrôles ReportViewer](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 



