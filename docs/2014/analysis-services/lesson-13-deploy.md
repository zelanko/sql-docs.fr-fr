---
title: 'Leçon 14 : déployer | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 24863a8a-9017-415a-a97b-fbac76ed0675
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 96ffa6445d46f1e68efa907330d0945a499bf3b2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66079140"
---
# <a name="lesson-14-deploy"></a>Leçon 14 : Déploiement
  Dans cette leçon, vous allez configurer les propriétés de déploiement ; pour cela, vous allez spécifier une instance de serveur de déploiement d'Analysis Services qui s'exécute en mode tabulaire, ainsi qu'un nom pour le modèle que vous déployez. Vous allez ensuite déployer le modèle sur cette instance. Après son déploiement, les utilisateurs peuvent se connecter au modèle en utilisant une application de création de rapports cliente. Pour plus d’informations, consultez [Déploiement d’une solution de modèle tabulaire &#40;SSAS Tabulaire&#41;](tabular-models/tabular-model-solution-deployment-ssas-tabular.md).  
  
 Durée estimée pour suivre cette leçon : **5 minutes**  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Cette rubrique fait partie d’un didacticiel de modélisation tabulaire, qui doit être suivi dans l’ordre prévu. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 13 : Analyser dans Excel](lesson-12-analyze-in-excel.md).  
  
## <a name="deploy-the-model"></a>Déployer le modèle  
  
#### <a name="to-configure-deployment-properties"></a>Pour configurer les propriétés de déploiement  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet **Adventure Works Internet Sales Tabular Model**, puis dans le menu contextuel, cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue **Pages des propriétés de AW Internet Sales Tabular Model**, sous **Serveur de déploiement**, dans la propriété **Serveur**, tapez le nom d’une instance Analysis Services en mode tabulaire. Ce sera l'instance sur laquelle sera déployé votre modèle.  
  
    > [!IMPORTANT]  
    >  Vous devez disposer d'autorisations d'administration sur une instance Analysis Services distante afin de déployer dans celle-ci.  
  
3.  Vérifiez que la propriété **mode de requête** est définie sur **in-Memory**.  
  
    > [!NOTE]  
    >  Le modèle créé à l'aide de ce didacticiel n'est pas pris en charge en mode DirectQuery.  
  
4.  Dans la propriété **Database** , tapez `Adventure Works Internet Sales Model`.  
  
5.  Dans la propriété nom du **cube** , `Adventure Works Internet Sales Model`tapez.  
  
6.  Passez en revue vos sélections, puis cliquez sur **OK**.  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a>Pour déployer le modèle tabulaire Internet Sales Adventure Works  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Générer**, puis cliquez sur **Déployer AW Internet Sales Tabular Model**.  
  
     La boîte de dialogue Déployer apparaît et affiche l'état de déploiement des métadonnées ainsi que de chaque table incluse dans le modèle.  
  
## <a name="conclusion"></a>Conclusion  
 Félicitations ! Vous avez terminé de créer et déployer votre premier modèle tabulaire Analysis Services. Ce didacticiel vous a guidé dans les tâches les plus courantes associées à la création d’un modèle tabulaire. Maintenant que votre modèle Internet Sales Adventure Works est déployé, vous pouvez utiliser SQL Server Management Studio pour gérer le modèle, créer des scripts de processus et un plan de sauvegarde. Les utilisateurs peuvent se connecter au modèle à l'aide d'une application cliente de création de rapports telle que Microsoft Excel ou [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)].  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour en savoir plus sur les propriétés de modèle tabulaire qui prennent en charge les rapports [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], consultez [Propriétés de la génération de rapports Power View &#40;SSAS Tabulaire&#41;](tabular-models/properties-ssas-tabular.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mode DirectQuery &#40;&#41;tabulaire SSAS](tabular-models/directquery-mode-ssas-tabular.md)   
 [Configurer les propriétés de déploiement et de modélisation des données par défaut &#40;SSAS tabulaire&#41;](tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)   
 [Bases de données model tabulaires &#40;&#41;SSAS tabulaire](tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
