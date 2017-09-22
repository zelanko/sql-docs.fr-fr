---
title: "Ajouter le composant WebPart Visionneuse de rapports à une page SharePoint | Documents Microsoft"
ms.custom: Add the Report Viewer web part to a page within your SharePoint site.
ms.date: 09/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a9397f427cac18d0c8bfc663f6bd477b0440b8a3
ms.openlocfilehash: 033d8092cab4e6aa0889f153d5e2e7d75ae31b03
ms.contentlocale: fr-fr
ms.lasthandoff: 09/15/2017

---

# <a name="add-report-viewer-web-part-to-a-sharepoint-page"></a>Ajouter le composant WebPart Visionneuse de rapports à une page SharePoint

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)])

Afficher un rapport, à partir de SQL Server Reporting Services ou le serveur de rapports Power BI, en ajoutant un composant WebPart Visionneuse de rapports à une page SharePoint.

![Composant WebPart Visionneuse de rapports sur une page SharePoint](media/sharepoint-report-viewer-web-part-on-page.png)

## <a name="prerequisites"></a>Conditions préalables

* Pour les rapports de chargement, les revendications au Service d’émission de jeton Windows (C2WTS) doit être configuré pour Kerberos la délégation contraint. Pour plus d’informations sur la configuration C2WTS, consultez [revendications au Service d’émission de jeton Windows (C2WTS) et Reporting Services](../install-windows/claims-to-windows-token-service-c2wts-and-reporting-services.md).

* Le composant WebPart Visionneuse de rapports doit être déployé pour votre batterie de serveurs SharePoint. Pour plus d’informations sur la façon de déployer le projet de solution composant WebPart Visionneuse de rapports, consultez [déployer le composant WebPart Visionneuse de rapports sur un site SharePoint](deploy-report-viewer-web-part.md).

## <a name="add-web-part"></a>Ajouter le composant WebPart

1. Dans votre site SharePoint, sélectionnez le **ENGRENAGE** icône dans le coin supérieur gauche et sélectionnez **ajouter une page**.

    ![Ajouter une page à un site sharepoint à partir de l’icône d’engrenage.](media/sharepoint-add-a-page.png)

2. Donnez à votre page un nom et sélectionnez **créer**.

3. Dans le Concepteur de la page, sélectionnez le **insérer** onglet dans le ruban. Puis sélectionnez **WebPart** au sein de la **parties** section.

    ![Insérer un composant WebPart à partir du ruban office.](media/sharepoint-insert-web-part.png)

4. Sous **catégories**, sélectionnez ** SQL Server Reporting Services (mode natif). Sous **parties**, sélectionnez **visionneuse de rapports**. Puis sélectionnez **ajouter**.

    ![Ajouter le composant WebPart Visionneuse de rapports.](media/sharepoint-report-viewer-web-part.png)

    Ceci peut vous sembler initialement avec une erreur. L’erreur est car l’URL de serveur de rapports par défaut est définie sur *http://localhost* et ne peut pas être disponible à cet emplacement.

## <a name="configure-the-report-viewer-web-part"></a>Configurer le composant WebPart Visionneuse de rapports

Pour configurer le composant WebPart pour pointer vers votre rapport, procédez comme suit.

1. Lorsque vous modifiez la page SharePoint, sélectionnez la flèche vers le bas dans le coin supérieur droit du composant WebPart, puis sélectionnez **WebPart modifier**.

    ![Modifier une page web à partir du web partie déroulante.](media/sharepoint-edit-web-part.png)

2. Entrez le **URL de Report Server** du serveur de rapports qui héberge votre rapport. Cela doit ressembler à *http://myrsserver/reportserver*.

3. Entrez le chemin d’accès et le nom du rapport que vous souhaitez afficher dans le composant WebPart. Cela s’apparente à *AdventureWorks Sample Reports/Company Sales*. Dans cet exemple, le rapport *Company Sales* est dans un dossier appelé *exemples de rapports AdventureWorks*.

4. Si votre rapport requiert des paramètres, une fois que vous avez spécifié l’URL du serveur de rapports et le nom du rapport, sélectionnez **charger les paramètres** au sein de la **paramètres** section.

5. Sélectionnez **Ok** pour enregistrer vos modifications à la configuration du composant WebPart.

6. Sélectionnez **enregistrer**, dans le ruban Office, pour enregistrer les modifications apportées à la page SharePoint.

![Composant WebPart Visionneuse de rapports sur une page SharePoint](media/sharepoint-report-viewer-web-part-on-page.png)

## <a name="considerations-and-limitations"></a>Considérations et limitations

* Le composant WebPart Visionneuse de rapports ne peut pas être utilisé sur les pages modernes dans SharePoint.
* Rapports Power BI ne peut pas être utilisés avec le composant WebPart Visionneuse de rapports.
* Si vous ne voyez pas le composant visionneuse de rapports, à ajouter à votre page, vérifiez que vous avez [déployé le composant WebPart Visionneuse de rapports](deploy-report-viewer-web-part.md).
* Le lien en haut de la partie web génère une erreur et ne pas accéder n’importe où.

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
