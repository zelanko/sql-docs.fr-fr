---
title: 'Leçon 5 : concevoir le rapport enfant à l’aide de l’Assistant Rapport | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 19a3f927-ea97-4f40-a5f8-cd5f2598e4da
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 661b4f3cc63eb0c19fddb53f872e940d1f9976e2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108439"
---
# <a name="lesson-5-design-the-child-report-using-the-report-wizard"></a>Leçon 5 : concevoir le rapport enfant à l'aide de l'Assistant Rapport
  Après avoir créé une connexion de données et une table de données pour le rapport enfant, l'étape suivante consiste à concevoir le rapport enfant à l'aide de l'Assistant Rapport dans le Concepteur de rapports. Pour plus d’informations sur le Concepteur de rapports, consultez [Concevoir des rapports à l’aide du Concepteur de rapports &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).  
  
### <a name="to-design-the-child-report-using-the-report-wizard"></a>Pour concevoir le rapport enfant à l'aide de l'Assistant Rapport  
  
1.  Vérifiez que le site web de niveau supérieur est sélectionné dans **l’Explorateur de solutions**.  
  
2.  Cliquez avec le bouton droit sur le site web et sélectionnez **Ajouter un nouvel élément**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément** , cliquez sur **Assistant Rapport**, entrez un nom pour le fichier de rapport, puis cliquez sur **Ajouter**.  
  
     Cette opération permet de lancer l'Assistant Rapport.  
  
4.  Dans la page **Propriétés du DataSet** , dans la zone source de **données** , cliquez sur **dataset2**.  
  
     La zone **Datasets disponibles** est automatiquement mise à jour avec l’objet DataTable que vous avez créé.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans la page **Organiser les champs** , procédez comme suit :  
  
    1.  Faites glisser **ProductID**, **PurchaseOrderID**, **PurchaseOrderDetailID**, **OrderQty**, **ReceivedQty**, **RejectedQty**et **StockedQty** depuis **Champs disponibles** vers la zone **Valeurs** .  
  
    2.  Cliquez sur la flèche en regard de **Sum (ProductID)**, **Sum (PurchaseOrderID)**, **Sum (PurchaseOrderDetailID)**, **Sum (OrderQty)**, **Sum (ReceivedQty)**, **Sum (RejectedQty)** et **Sum (StockedQty)** et effacez la sélection **Sum** .  
  
7.  Cliquez sur **suivant** à deux reprises, puis sur **Terminer** pour fermer l' **Assistant Rapport**.  
  
     Vous avez maintenant créé le fichier .rdlc. Le fichier s'ouvre dans le Concepteur de rapports. Le tableau matriciel que vous avez conçu est maintenant affiché dans l'aire de conception.  
  
8.  Le fichier .rdlc étant ouvert, ajoutez un paramètre en procédant comme suit :  
  
    1.  Dans le volet **données du rapport** , cliquez sur **paramètres** , puis sur **Ajouter des paramètres**.  
  
    2.  Entrez **productid** dans la zone **Nom** .  
  
    3.  Vérifiez que **Entier** est sélectionné dans la zone de liste **Type de données** .  
  
    4.  Cliquez sur **OK**.  
  
9. Enregistrez le fichier .rdlc.  
  
## <a name="next-task"></a>Tâche suivante  
 Vous venez de concevoir le rapport enfant à l'aide de l'Assistant Rapport. Vous allez à présent ajouter un contrôle ReportViewer dans l'application de site Web.  
  
  
