---
title: 'Leçon 3 : Concevoir le rapport Parent à l’aide de l’Assistant rapport | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 2f69dcd3-cd6d-45a9-a62a-ba6f5f3179d8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8fe60270cd3737e3c372fbf92ccb906beb8d06cb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63182915"
---
# <a name="lesson-3-design-the-parent-report-using-the-report-wizard"></a>Leçon 3 : Concevoir le rapport parent à l'aide de l'Assistant Rapport
  Après avoir créé une connexion de données et une table de données pour le rapport parent, l'étape suivante consiste à concevoir le rapport parent à l'aide de l'Assistant Rapport dans le Concepteur de rapports. Pour plus d’informations sur le Concepteur de rapports, consultez [Concevoir des rapports à l’aide du Concepteur de rapports &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).  
  
### <a name="to-design-the-parent-report-using-the-report-wizard"></a>Pour concevoir le rapport parent à l'aide de l'Assistant Rapport  
  
1.  Vérifiez que le site web de niveau supérieur est sélectionné dans **l’Explorateur de solutions**.  
  
2.  Cliquez avec le bouton droit sur le site web et sélectionnez **Ajouter un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **Assistant rapport**, entrez un nom pour le fichier de rapport, puis cliquez sur **ajouter**.  
  
     Cette opération permet de lancer l'Assistant Rapport.  
  
4.  Sur le **propriétés du Dataset** page, dans le **source de données** boîte, sélectionnez le **DataSet1** que vous avez créé dans [leçon 2 : Définir une connexion de données et la Table de données pour le rapport Parent](lesson-2-define-a-data-connection-and-data-table-for-parent-report.md).  
    La zone **Datasets disponibles** est mise à jour automatiquement avec l’objet **DataTable** créé précédemment.  
  
5.  Cliquer sur **Suivant**.  
  
6.  Dans la page **Organiser les champs** , procédez comme suit :  
  
    1.  Faites glisser **ProductID**, **Name**, **ProductNumber**, **SafetyStockLevel**et **ReorderLevel** depuis **Champs disponibles** vers la zone **Valeurs** .  
  
    2.  Cliquez sur la flèche en regard **SUM (ProductID)**, **SUM (safetystocklevel)**, **SUM (ReorderLevel)** et désactivez le **somme** sélection.  
  
7.  Cliquez sur **suivant** à deux reprises, puis cliquez sur **Terminer** pour fermer la **Assistant rapport**.  
  
     Vous avez maintenant créé le fichier .rdlc. Le fichier s'ouvre dans le Concepteur de rapports. Le tableau matriciel que vous avez conçu est maintenant affiché dans l'aire de conception.  
  
8.  Enregistrez le fichier .rdlc.  
  
## <a name="next-task"></a>Tâche suivante  
 Vous venez de concevoir le rapport parent à l'aide de l'Assistant Rapport. Vous allez à présent créer une connexion de données et une table de données pour le rapport enfant.  
  
  
