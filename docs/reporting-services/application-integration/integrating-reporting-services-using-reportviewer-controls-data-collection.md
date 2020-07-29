---
title: Collecte des données dans le contrôle ReportViewer
description: ReportViewer collecte des données d’utilisation anonymes afin de comprendre comment les clients utilisent le produit et d’axer le développement sur les améliorations les plus pertinentes pour les clients.
author: maggiesMSFT
ms.author: maggies
ms.custom: seo-lt-2019
ms.reviewer: ''
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.date: 06/03/2020
ms.openlocfilehash: 22f693824c244e02f313e488a067a0b732b2fa10
ms.sourcegitcommit: dc6ea6665cd2fb58a940c722e86299396b329fec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84423397"
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



