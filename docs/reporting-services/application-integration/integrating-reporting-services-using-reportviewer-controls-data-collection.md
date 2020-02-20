---
title: Collecte des données dans le contrôle ReportViewer
description: Des données d’utilisation anonymes sont collectées par le contrôle pour mieux comprendre comment les clients utilisent le produit. Les données d’utilisation permettent de concentrer le développement futur sur les améliorations les plus pertinentes pour les clients.
author: maggiesMSFT
ms.author: maggies
ms.custom: ''
ms.reviewer: ''
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.date: 09/18/2018
ms.openlocfilehash: d7b70445fc4d8a29d8ebcdf7ecbffe4b54133f0e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "74796896"
---
# <a name="integrate-reporting-services-using-reportviewer-controls---data-collection"></a>Intégrer Reporting Services à l’aide de contrôles ReportViewer - Collecte des données

Des données d’utilisation anonymes sont collectées par le contrôle pour vous permettre de mieux comprendre comment les clients utilisent le produit. Les données d’utilisation permettent de concentrer le développement futur sur les améliorations les plus pertinentes pour les clients.

Une explication des pratiques de collecte et d’utilisation des données de Microsoft SQL Server et de la visionneuse de rapports est disponible dans la [déclaration de confidentialité](https://go.microsoft.com/fwlink/?LinkID=868444).

## <a name="opting-out-of-data-collection"></a>Désactivation de la collecte de données

La collecte des données d’utilisation peut être désactivée via la propriété ```EnableTelemetry```.

```xml
<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
</rsweb:ReportViewer>
```

Ou, de façon pragmatique, avant que le contrôle soit restitué.
    
```csharp
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>Voir aussi

[Utilisation du contrôle WebForms Visionneuse de rapports](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[Intégration de Reporting Services à l’aide des contrôles Visionneuse de rapports](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 



