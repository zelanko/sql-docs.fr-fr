---
title: "Leçon 5 : Concevoir le rapport enfant à l’aide de l’Assistant rapport | Documents Microsoft"
ms.custom: 
ms.date: 05/18/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 19a3f927-ea97-4f40-a5f8-cd5f2598e4da
caps.latest.revision: 8
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 285ade0eaf63fee0733fcfcb9e8f627e8c666a6b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="lesson-5-design-the-child-report-using-the-report-wizard"></a>Leçon 5 : concevoir le rapport enfant à l'aide de l'Assistant Rapport
Après avoir créé une connexion de données et une table de données pour le rapport enfant, l'étape suivante consiste à concevoir le rapport enfant à l'aide de l'Assistant Rapport dans le Concepteur de rapports. Pour plus d’informations sur le Concepteur de rapports, consultez [Concevoir des rapports à l’aide du Concepteur de rapports &#40;SSRS&#41;](../reporting-services/tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).  
  
### <a name="to-design-the-child-report-using-the-report-wizard"></a>Pour concevoir le rapport enfant à l'aide de l'Assistant Rapport  
  
1.  Vérifiez que le site web de niveau supérieur est sélectionné dans **l’Explorateur de solutions**.  
  
2.  Cliquez avec le bouton droit sur le site web et sélectionnez **Ajouter un nouvel élément**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément** , cliquez sur **Assistant Rapport**, entrez un nom pour le fichier de rapport, puis sélectionnez **Ajouter**.  
  
    Cette opération permet de lancer l'Assistant Rapport.  
  
4.  Dans la page **Propriétés du dataset** , dans la zone **Source de données** , sélectionnez **DataSet2**.  
  
    La zone **Datasets disponibles** est automatiquement mise à jour avec l’objet DataTable que vous avez créé.  
  
5.  Sélectionnez **Suivant**.  
  
6.  Dans la page **Organiser les champs** , procédez comme suit :  
  
    1.  Faites glisser **ProductID**, **PurchaseOrderID**, **PurchaseOrderDetailID**, **OrderQty**, **ReceivedQty**, **RejectedQty**et **StockedQty** depuis **Champs disponibles** vers la zone **Valeurs** .  
  
    2.  Sélectionnez la flèche en regard de **Sum(ProductID)**, **Sum(PurchaseOrderID)**, **Sum(PurchaseOrderDetailID)**, **Sum(OrderQty)**, **Sum(ReceivedQty)**, **Sum(RejectedQty)**et **Sum(StockedQty)** , puis effacez la sélection de **Somme** .  
  
7.  Sélectionnez deux fois **Suivant** , puis sélectionnez **Terminer** pour fermer **l’Assistant Rapport**.  
  
    Vous venez de créer le fichier .rdlc. Le fichier s'ouvre dans le Concepteur de rapports. Le tableau matriciel que vous avez conçu est maintenant affiché dans l'aire de conception.  
  
8.  Le fichier .rdlc étant ouvert, ajoutez un paramètre en procédant comme suit :  
  
    1.  Dans le volet **Données du rapport** , cliquez avec le bouton droit sur **Paramètres** , puis sélectionnez **Ajouter des paramètres**.  
  
    2.  Entrez **productid** dans la zone **Nom** .  
  
    3.  Vérifiez que **Entier** est sélectionné dans la zone de liste **Type de données** .  
  
    4.  Cliquez sur **OK**.  
  
9. Enregistrez le fichier .rdlc.  
  
## <a name="next-task"></a>Tâche suivante  
Vous venez de concevoir le rapport enfant à l'aide de l'Assistant Rapport. Vous allez à présent ajouter un contrôle ReportViewer dans l'application de site Web. Consultez [Leçon 6 : Ajouter un contrôle ReportViewer à l’application](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md).  
  
  
  


