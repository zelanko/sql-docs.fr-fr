---
title: 'Leçon 3 : concevoir le rapport parent à l’aide de l’Assistant Rapport | Microsoft Docs'
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 2f69dcd3-cd6d-45a9-a62a-ba6f5f3179d8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ad06a5a76344348c71838873edcc490c75b7b2e2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62651275"
---
# <a name="lesson-3-design-the-parent-report-using-the-report-wizard"></a>Leçon 3 : concevoir le rapport parent à l'aide de l'Assistant Rapport
Après avoir créé une connexion de données et une table de données pour le rapport parent, l'étape suivante consiste à concevoir le rapport parent à l'aide de l'Assistant Rapport dans le Concepteur de rapports. Pour plus d’informations sur le Concepteur de rapports, consultez [Concevoir des rapports à l’aide du Concepteur de rapports &#40;SSRS&#41;](../reporting-services/tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).  
  
### <a name="to-design-the-parent-report-using-the-report-wizard"></a>Pour concevoir le rapport parent à l'aide de l'Assistant Rapport  
  
1.  Vérifiez que le site web de niveau supérieur est sélectionné dans **l’Explorateur de solutions**.  
  
2.  Cliquez avec le bouton droit sur le site web et sélectionnez **Ajouter un nouvel élément**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Assistant Rapport**, entrez un nom pour le fichier de rapport, puis sélectionnez **Ajouter**.  
  
    Cette opération permet de lancer l'Assistant Rapport.  
  
4.  Dans la page **Propriétés du dataset** , dans la zone **Source de données** , sélectionnez le **DataSet1** que vous avez créé à la [Leçon 2 : Définir une connexion de données et une table de données pour le rapport parent](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md).  
  
    La zone **Datasets disponibles** est mise à jour automatiquement avec l’objet **DataTable** créé précédemment.  
  
5.  Sélectionnez **Suivant**.  
  
6.  Dans la page **Organiser les champs** , procédez comme suit :  
  
    1.  Faites glisser **ProductID**, **Name**, **ProductNumber**, **SafetyStockLevel**et **ReorderLevel** depuis **Champs disponibles** vers la zone **Valeurs** .  
  
    2.  Sélectionnez la flèche en regard de **Sum(ProductID)** , **Sum(SafetyStockLevel)** , **Sum(ReorderLevel)** et effacez la sélection de **Somme** .  
  
7.  Sélectionnez deux fois **Suivant** , puis sélectionnez **Terminer** pour fermer **l’Assistant Rapport**.  
  
    Vous avez maintenant créé le fichier .rdlc. Le fichier s'ouvre dans le Concepteur de rapports. Le tableau matriciel que vous avez conçu est maintenant affiché dans l'aire de conception.  
  
8.  Enregistrez le fichier .rdlc.  
  
## <a name="next-task"></a>Tâche suivante  
Vous venez de concevoir le rapport parent à l'aide de l'Assistant Rapport. Vous allez à présent créer une connexion de données et une table de données pour le rapport enfant. Consultez la [Leçon 4 : Définir une connexion de données et une table de données pour le rapport enfant](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md).  
  
  
  

