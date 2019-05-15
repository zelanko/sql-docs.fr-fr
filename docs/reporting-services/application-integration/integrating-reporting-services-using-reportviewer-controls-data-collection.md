---
title: Collecte des donnée dans le contrôle ReportViewer 2016
uthor: markingmyname
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.custom: ''
ms.date: 09/18/2018
ms.openlocfilehash: f1d24c2de0b6398b4effb2dcaa6129a7b252d130
ms.sourcegitcommit: e4794943ea6d2580174d42275185e58166984f8c
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65504133"
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>Intégration de Reporting Services à l’aide de contrôles ReportViewer - collecte des données

Des données d’utilisation anonymes sont collectées par le contrôle pour vous permettre de mieux comprendre comment les clients utilisent le produit. Les données d’utilisation permettent de concentrer le développement futur sur les améliorations les plus pertinentes pour les clients.

Une explication des pratiques de collecte et d’utilisation des données de Microsoft SQL Server et de la visionneuse de rapports est disponible dans la [déclaration de confidentialité](https://go.microsoft.com/fwlink/?LinkID=868444).

## <a name="opting-out-of-data-collection"></a>Désactivation de la collecte de données

La collecte des données d’utilisation peut être désactivée via la propriété ```EnableTelemetry```.

```
<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
</rsweb:ReportViewer>
```

Ou, de façon pragmatique, avant que le contrôle soit restitué.
    
```
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>Voir aussi

[Utilisation du contrôle WebForms Visionneuse de rapports](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[Intégration de Reporting Services à l’aide des contrôles Visionneuse de rapports](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 



