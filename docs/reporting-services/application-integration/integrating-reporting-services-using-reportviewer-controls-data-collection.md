---
title: Collecte des données dans le contrôle ReportViewer version 2016 | Microsoft Docs
ms.date: 09/06/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.suite: pro-bi
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 782888c9946fd09d9c711a6eda2a8f77fd18c3ba
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43267404"
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>Intégration de Reporting Services à l’aide de contrôles ReportViewer - collecte des données
Par défaut, le contrôle ReportViewer collecte des informations d’utilisation anonymes permettant à Microsoft de mieux comprendre la façon dont les clients utilisent le contrôle. Grâce à une meilleure compréhension de la façon dont les clients déploient et utilisent le contrôle de visionneuse, il est possible de concentrer le développement futur sur les améliorations les plus intéressantes pour la majorité des clients.

Pour obtenir une explication des pratiques de collecte et d’utilisation des données utilisateur des versions de Microsoft SQL Server 2016 et de tout autre produit ou service, consultez cette [déclaration de confidentialité]((http://go.microsoft.com/fwlink/?LinkID=868444)).

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



