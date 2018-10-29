---
title: Collecte des données dans le contrôle ReportViewer version 2016 | Microsoft Docs
ms.date: 09/18/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 68e5a4c9789a6c0485433a3199d8d6a03c2a90d5
ms.sourcegitcommit: a251adad8474b477363df6a121431b837f22bf77
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47864337"
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>Intégration de Reporting Services à l’aide de contrôles ReportViewer - collecte des données

Des données d’utilisation anonymes sont collectées par le contrôle pour vous permettre de mieux comprendre comment les clients utilisent le produit. Les données d’utilisation permettent de concentrer le développement futur sur les améliorations les plus pertinentes pour les clients.

Une explication des pratiques de collecte et d’utilisation des données de Microsoft SQL Server et de la visionneuse de rapports est disponible dans la [déclaration de confidentialité](http://go.microsoft.com/fwlink/?LinkID=868444).

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



