---
title: 'Leçon 5 : Concevoir le rapport enfant à l’aide de l’Assistant rapport | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 19a3f927-ea97-4f40-a5f8-cd5f2598e4da
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: bc993c0881eb4aeeddb18c8df0efad69dbba261e
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52418350"
---
# <a name="lesson-5-design-the-child-report-using-the-report-wizard"></a>Leçon 5 : Concevoir le rapport enfant à l’aide de l’Assistant rapport
  Après avoir créé une connexion de données et une table de données pour le rapport enfant, l'étape suivante consiste à concevoir le rapport enfant à l'aide de l'Assistant Rapport dans le Concepteur de rapports. Pour plus d’informations sur le Concepteur de rapports, consultez [Concevoir des rapports à l’aide du Concepteur de rapports &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).  
  
### <a name="to-design-the-child-report-using-the-report-wizard"></a>Pour concevoir le rapport enfant à l'aide de l'Assistant Rapport  
  
1.  Vérifiez que le site web de niveau supérieur est sélectionné dans **l’Explorateur de solutions**.  
  
2.  Cliquez avec le bouton droit sur le site web et sélectionnez **Ajouter un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **Assistant rapport**, entrez un nom pour le fichier de rapport, puis cliquez sur **ajouter**.  
  
     Cette opération permet de lancer l'Assistant Rapport.  
  
4.  Dans le **propriétés du Dataset** page, dans le **source de données** , cliquez sur **DataSet2**.  
  
     La zone **Datasets disponibles** est automatiquement mise à jour avec l’objet DataTable que vous avez créé.  
  
5.  Cliquer sur **Suivant**.  
  
6.  Dans la page **Organiser les champs** , procédez comme suit :  
  
    1.  Faites glisser **ProductID**, **PurchaseOrderID**, **PurchaseOrderDetailID**, **OrderQty**, **ReceivedQty**, **RejectedQty**et **StockedQty** depuis **Champs disponibles** vers la zone **Valeurs** .  
  
    2.  Cliquez sur la flèche en regard **SUM (ProductID)**, **SUM (purchaseorderid)**, **SUM (purchaseorderdetailid)**, **SUM (OrderQty)**,  **SUM (receivedqty)**, **SUM (rejectedqty)**, et **SUM (stockedqty)** et désactivez le **somme** sélection.  
  
7.  Cliquez sur **suivant** à deux reprises, puis cliquez sur **Terminer** pour fermer la **Assistant rapport**.  
  
     Vous avez maintenant créé le fichier .rdlc. Le fichier s'ouvre dans le Concepteur de rapports. Le tableau matriciel que vous avez conçu est maintenant affiché dans l'aire de conception.  
  
8.  Le fichier .rdlc étant ouvert, ajoutez un paramètre en procédant comme suit :  
  
    1.  Cliquez sur **paramètres** dans le **les données de rapport** volet, puis cliquez sur **ajouter des paramètres**.  
  
    2.  Entrez **productid** dans la zone **Nom** .  
  
    3.  Vérifiez que **Entier** est sélectionné dans la zone de liste **Type de données** .  
  
    4.  Cliquez sur **OK**.  
  
9. Enregistrez le fichier .rdlc.  
  
## <a name="next-task"></a>Tâche suivante  
 Vous venez de concevoir le rapport enfant à l'aide de l'Assistant Rapport. Vous allez à présent ajouter un contrôle ReportViewer dans l'application de site Web.  
  
  
