---
title: 'Tâche 9 : ajout d’une transformation d’Union totale pour combiner des enregistrements corrects et corrigés | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 24ba466d-a7d3-49e7-9111-b348399c9e58
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 89e336b326550f07a5ad6fb5dfab449dbe349109
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85006251"
---
# <a name="task-9-adding-union-all-transform-to-combine-correct-and-corrected-records"></a>Tâche 9 : Ajout d’une transformation d’union totale pour combiner des enregistrements corrects et corrigés
  Dans cette tâche, vous allez ajouter une transformation d'union totale au flux de données. La transformation d'union totale combine plusieurs entrées en une seule sortie. Dans votre scénario, elle combine les enregistrements corrects et corrigés dans un seul flux.  
  
1.  Faites glisser la transformation **Union All** de la section **commun** de la **boîte à outils SSIS** vers l’onglet de **Workflow** et placez-la sous **Sélectionner les enregistrements corrects et corrigés**.  
  
2.  Cliquez avec le bouton droit sur la transformation d' **Union** totale sous l’onglet **Data Flow** , puis cliquez sur **Renommer**. Tapez **combiner les enregistrements corrects et corrigés**, puis appuyez sur **entrée**.  
  
     ![Combiner des enregistrements corrects et corrigés](../../2014/tutorials/media/et-addinguattocombinecacrecords-01.jpg "Combiner des enregistrements corrects et corrigés")  
  
3.  Connecter **Choisissez les enregistrements corrects et corrigés** pour **combiner les enregistrements corrects et corrigés** dans l’onglet de **Workflow** à l’aide du connecteur bleu. La boîte de dialogue **sélection de sortie d’entrée** doit s’afficher.  
  
4.  Dans la boîte de dialogue **sortie d’entrée** , sélectionnez **correct** pour la **sortie** , puis cliquez sur **OK**.  
  
     ![Boîte de dialogue Sélection entrée et sortie](../../2014/tutorials/media/et-addinguattocombinecacrecords-02.jpg "Boîte de dialogue Sélection entrée et sortie")  
  
5.  Déplacez le connecteur intitulé **correct** vers la gauche en faisant glisser le point à la fin du connecteur vers la gauche.  
  
     ![Connexion des corrects à Combiner des enregistrements corrects et corrigés](../../2014/tutorials/media/et-addinguattocombinecacrecords-03.jpg "Connexion des corrects à Combiner des enregistrements corrects et corrigés")  
  
6.  Si vous sélectionnez la transformation **choisir les enregistrements corrects et corrigés** , vous devez voir un autre connecteur bleu. Faites glisser ce connecteur bleu pour **combiner les enregistrements corrects et corrigés**.  
  
     ![Connexion des corrigés à Combiner des enregistrements corrects et corrigés](../../2014/tutorials/media/et-addinguattocombinecacrecords-04.jpg "Connexion des corrigés à Combiner des enregistrements corrects et corrigés")  
  
7.  Ce **connecteur** doit être **corrigé**. Étant donné que deux conditions sont **correctes** et **corrigées**et que l’une d’elles a déjà été utilisée, la boîte de dialogue **sélection de sortie d’entrée** ne s’affiche pas cette fois. Si les connecteurs se chevauchent, déplacez un connecteur à gauche et l'autre à droite en les faisant glisser.  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 10 : Ajout d’une transformation de regroupement probable pour identifier des doublons](../../2014/tutorials/task-10-adding-fuzzy-group-transform-to-identify-duplicates.md)  
  
  
