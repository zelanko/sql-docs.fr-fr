---
title: 'Analysis Services leçon du didacticiel 13 : Déployer | Microsoft Docs'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: ab561b096c4436349580201eec3b3ea10a8aaa75
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685306"
---
# <a name="deploy"></a>Déployer

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Dans cette leçon, vous configurez les propriétés de déploiement ; en spécifiant un serveur à déployer sur et un nom pour le modèle. Vous déployez ensuite le modèle sur le serveur. Une fois que votre modèle est déployé, les utilisateurs y connecter à l’aide d’une application cliente de création de rapports. Pour plus d’informations, consultez [déployer sur Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy) et [déploiement de solutions de modèle tabulaire](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md).  
  
Durée estimée pour effectuer cette leçon : **5 minutes**  
  
## <a name="prerequisites"></a>Prérequis  

Cet article fait partie d’un didacticiel de modélisation tabulaire, qui doit être effectué dans l’ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 12 : Analyser dans Excel](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md).  

> [!IMPORTANT]  
> Si le déploiement sur Azure Analysis Services, vous devez disposer [autorisations d’administrateur](https://docs.microsoft.com/azure/analysis-services/analysis-services-server-admins) sur le serever.  

> [!IMPORTANT]  
> Si vous avez installé la base de données exemple AdventureWorksDW sur un serveur local SQL Server, et que vous déployez votre modèle à un serveur Azure Analysis Services, un [passerelle de données locale](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway) est requis.
  
## <a name="deploy-the-model"></a>Déployer le modèle  
  
#### <a name="to-configure-deployment-properties"></a>Pour configurer les propriétés de déploiement  

  
1.  Dans **l’Explorateur de solutions**, cliquez sur le **AW Internet Sales** de projet, puis cliquez sur **propriétés**.  
  
2.  Dans le **Pages de propriétés de AW Internet Sales** boîte de dialogue **serveur de déploiement**, dans le **Server** propriété, entrez le nom complet du serveur. Si vous vous connectez à Azure Analysis Services, nom du serveur doit inclure l’URL complète.

    ![as-lesson13-deploy-property](../tutorial-tabular-1400/media/as-lesson13-deploy-property.png)
  
3.  Dans le **base de données** propriété, tapez **Adventure Works Internet Sales**.  
  
4.  Dans le **Nom_modèle** propriété, tapez **Adventure Works Internet Sales Model**.  
  
5.  Vérifiez vos sélections, puis cliquez sur **OK**.  
  
#### <a name="to-deploy-the-adventure-works-internet-sales"></a>Pour déployer les ventes sur Internet Adventure Works
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit le **AW Internet Sales** projet > **Build**.  

2.  Cliquez sur le **AW Internet Sales** projet > **déployer**.

    Lors du déploiement sur Azure Analysis Services, vous pouvez être invité à entrer votre compte. Entrez votre compte professionnel et un mot de passe, par exemple nancy@adventureworks.com. Ce compte doit être partie du groupe Administrateurs sur le serveur.
  
    La boîte de dialogue déployer apparaît et affiche l’état du déploiement des métadonnées, ainsi chaque table incluse dans le modèle.  
    
    ![as-lesson13-deploy-status](../tutorial-tabular-1400/media/as-lesson13-deploy-status.png)
  
3. Une fois le déploiement correctement effectué, cliquez sur **Fermer**.  
  

Cette leçon décrit la méthode plus courante et la plus simple pour déployer un modèle tabulaire à partir de SSDT. Options de déploiement avancées telles que l’Assistant de déploiement ou l’automatisation avec XMLA et AMO fournissent une plus grande souplesse, la cohérence et les déploiements planifiés. Pour plus d’informations, consultez [déploiement de solutions de modèle tabulaire](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md).

## <a name="conclusion"></a>Conclusion  
Félicitations ! Vous avez terminé de créer et déployer votre premier modèle tabulaire Analysis Services. Ce didacticiel vous a guidés dans les tâches courantes pour créer un modèle tabulaire. Maintenant que votre modèle Internet Sales Adventure Works est déployé, vous pouvez utiliser SQL Server Management Studio pour gérer le modèle, créer des scripts de processus et un plan de sauvegarde. Les utilisateurs peuvent également maintenant vous connecter au modèle à l’aide d’une application cliente de création de rapports tels que Microsoft Excel ou Power BI.  

![as-lesson13-ssms](../tutorial-tabular-1400/media/as-lesson13-ssms.png)
  
  
  
## <a name="whats-next"></a>Quelle est l’étape suivante ?
[Se connecter avec Power BI Desktop](https://docs.microsoft.com/azure/analysis-services/analysis-services-connect-pbi)   
[Leçon supplémentaire – sécurité dynamique](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)   
[Leçon supplémentaire – lignes de détails](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)   
[Leçon supplémentaire – hiérarchies déséquilibrées](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)   
