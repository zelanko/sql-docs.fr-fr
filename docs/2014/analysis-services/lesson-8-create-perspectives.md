---
title: 'Leçon 9 : Créer des Perspectives | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 83d9b10af87926a26b2a671ff162163d3c8fa62f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163609"
---
# <a name="lesson-9-create-perspectives"></a>Leçon 9 : Créer des perspectives
  Dans cette leçon, vous allez créer une perspective Internet Sales. Une perspective définit un sous-ensemble visualisable d'un modèle et des points de vue du modèle focalisés sur un domaine d'activité ou sur une application. Lorsqu'un utilisateur se connecte à un modèle à l'aide d'une perspective, il voit uniquement les objets de modèle (tables, colonnes, mesures, hiérarchies et KPI) en tant que champs définis dans cette perspective.  
  
 La perspective Internet Sales que vous créez dans cette leçon exclura l'objet table Customer. Lorsque vous créez une perspective qui exclut certains objets de la vue, cet objet existe toujours dans le modèle ; toutefois, il n'est pas visible dans une liste de champs de client de création de rapports. Les colonnes calculées et les mesures incluses ou non dans une perspective peuvent toujours être calculées à partir de données d'objet exclues.  
  
 L'objectif de cette leçon est plutôt de décrire comment créer des points de vue et de vous familiariser avec les outils de création de modèles tabulaires. Si vous développez par la suite ce modèle pour inclure des tables supplémentaires, vous pourrez créer des perspectives supplémentaires pour définir des points de vue différents, concernant, par exemple, les stocks et la forces de vente.  
  
 Pour plus d’informations, consultez [Perspectives &#40;SSSAS Tabulaire&#41;](tabular-models/perspectives-ssas-tabular.md).  
  
 Durée estimée pour effectuer cette leçon :**5 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 8 : Créer les indicateurs de performance clés](lesson-7-create-key-performance-indicators.md).  
  
## <a name="create-perspectives"></a>Créer des perspectives  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Pour créer une perspective Internet Sales  
  
1.  Dans le Concepteur de modèles, cliquez sur le **modèle** menu, puis sur **Perspectives**.  
  
2.  Dans la boîte de dialogue **Perspectives** , cliquez sur **Nouvelle perspective**.  
  
3.  Pour renommer la perspective, double-cliquez sur le **nouvelle Perspective 1** en-tête de colonne, puis tapez `Internet Sales`.  
  
4.  Dans **champs**, sélectionnez les tables suivantes **Date**, **Geography**, **produit**, **Product Category**, **Product Subcategory**, et `Internet Sales`.  
  
     Notez que vous avez exclu la table Customer et toutes ses colonnes de cette perspective. Ultérieurement, au cours de la leçon 12, vous utiliserez la fonctionnalité Analyser dans Excel pour tester cette perspective. La liste de champs de tableau croisé dynamique Excel inclut chaque table sauf la table Customer.  
  
5.  Vérifiez vos sélections, vérifiez que la table **Customer** n’est pas sélectionnée, puis cliquez sur **OK**  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour poursuivre l’étude de ce didacticiel, passez à la [Leçon 10 : Créer des hiérarchies](lesson-9-create-hierarchies.md).  
  
  
