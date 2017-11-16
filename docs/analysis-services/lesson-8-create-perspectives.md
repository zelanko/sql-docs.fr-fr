---
title: "Leçon 9 créer des Perspectives | Documents Microsoft"
ms.custom: 
ms.date: 03/27/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 993cf02a47240c0a74667f6220c6b2dd5d6df86c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-8-create-perspectives"></a>Leçon 8 : Créer des Perspectives
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

Dans cette leçon, vous allez créer une perspective Internet Sales. Une perspective définit un sous-ensemble visualisable d'un modèle et des points de vue du modèle focalisés sur un domaine d'activité ou sur une application. Lorsqu’un utilisateur se connecte à un modèle à l’aide d’un point de vue, ils voient uniquement les objets de modèle (tables, colonnes, mesures, hiérarchies et KPI) en tant que champs définis dans cette perspective.  
  
La perspective Internet Sales que vous créez dans cette leçon exclura l’objet de la table DimCustomer. Lorsque vous créez une perspective qui exclut certains objets de la vue, cet objet existe toujours dans le modèle ; toutefois, il n'est pas visible dans une liste de champs de client de création de rapports. Les colonnes calculées et les mesures incluses ou non dans une perspective peuvent toujours être calculées à partir de données d'objet exclues.  
  
L'objectif de cette leçon est plutôt de décrire comment créer des points de vue et de vous familiariser avec les outils de création de modèles tabulaires. Si vous développez ultérieurement ce modèle pour inclure des tables supplémentaires, vous pouvez créer des perspectives supplémentaires pour définir les différents points de vue du modèle, par exemple, l’inventaire et les ventes. Pour plus d’informations, consultez [Perspectives](../analysis-services/tabular-models/perspectives-ssas-tabular.md).  
  
Durée estimée pour effectuer cette leçon : **5 minutes**  
  
## <a name="prerequisites"></a>Conditions préalables  
Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [leçon 7 : créer des indicateurs de Performance clés](../analysis-services/lesson-7-create-key-performance-indicators.md).  
  
## <a name="create-perspectives"></a>Créer des perspectives  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Pour créer une perspective Internet Sales  
  
1.  Cliquez sur le **modèle** menu > **Perspectives** > **créer et gérer**.  
  
2.  Dans la boîte de dialogue **Perspectives** , cliquez sur **Nouvelle perspective**.  
  
3.  Double-cliquez sur le **nouvelle Perspective** en-tête de colonne, puis renommez **Internet Sales**.  
  
4.  Sélectionnez toutes les tables *sauf* **DimCustomer**.  
  
    ![en tant que-tabulaire-lesson8-perspectives](../analysis-services/media/as-tabular-lesson8-perspectives.png)
  
    Dans une prochaine leçon, vous utiliserez l’analyser dans la fonctionnalité Excel pour tester cette perspective. La liste de champs de tableau croisé dynamique Excel inclut chaque table à l’exception de la table DimCustomer.  

## <a name="whats-next"></a>Étape suivante
Accédez à la leçon suivante : [leçon 9 : créer des hiérarchies](../analysis-services/lesson-9-create-hierarchies.md).
  
  
  
  

