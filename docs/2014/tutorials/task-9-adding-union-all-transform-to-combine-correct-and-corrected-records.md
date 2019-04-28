---
title: 'Tâche 9 : Ajout d’Union All transformation pour combiner des enregistrements corrects et corrigés | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 24ba466d-a7d3-49e7-9111-b348399c9e58
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 2a3861e7de24e4fdf43ea11cf447b448c9d17b48
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62866409"
---
# <a name="task-9-adding-union-all-transform-to-combine-correct-and-corrected-records"></a>Tâche 9 : Ajout d’une transformation d’union totale pour combiner des enregistrements corrects et corrigés
  Dans cette tâche, vous allez ajouter une transformation d'union totale au flux de données. La transformation d'union totale combine plusieurs entrées en une seule sortie. Dans votre scénario, elle combine les enregistrements corrects et corrigés dans un seul flux.  
  
1.  Glisser-déplacer **Union All** transformer de **courants** section de la **boîte à outils SSIS** à la **de flux de données** onglet et placez-le sous **Choisir les enregistrements corrects et corrigés**.  
  
2.  Avec le bouton droit **Union All** transformer dans le **de flux de données** onglet, puis cliquez sur **renommer**. Type **combiner des enregistrements corrects et corrigés**, puis appuyez sur **entrée**.  
  
     ![Combiner des enregistrements corrects et corrigés Reocrds](../../2014/tutorials/media/et-addinguattocombinecacrecords-01.jpg "combiner Reocrds corrects et corrigés")  
  
3.  Se connecter **choisir enregistrements corrects et corrigés** à **combiner des enregistrements corrects et corrigés** dans le **de flux de données** onglet à l’aide du connecteur bleu. Vous devez voir le **sélection entrée et sortie** boîte de dialogue.  
  
4.  Dans le **e** boîte de dialogue, sélectionnez **Correct** pour **sortie** et cliquez sur **OK**.  
  
     ![Entrée de boîte de dialogue de sélection de sortie](../../2014/tutorials/media/et-addinguattocombinecacrecords-02.jpg "d’entrée de boîte de dialogue de sélection de sortie")  
  
5.  Déplacer le connecteur intitulé **Correct** vers la gauche en faisant glisser le point à la fin du connecteur vers la gauche.  
  
     ![Connexion des corrects à combiner des enregistrements Correct et corrigé](../../2014/tutorials/media/et-addinguattocombinecacrecords-03.jpg "connexion des corrects à combiner des enregistrements Correct et corrigé")  
  
6.  Si vous sélectionnez **choisir enregistrements corrects et corrigés** transformer, vous devez voir un autre connecteur bleu. Faites glisser ce connecteur bleu sur **combiner des enregistrements corrects et corrigés**.  
  
     ![Connexion des corrigés à combiner des enregistrements Correct et corrigé](../../2014/tutorials/media/et-addinguattocombinecacrecords-04.jpg "connexion des corrigés à combiner des enregistrements Correct et corrigé")  
  
7.  Cela **connecteur** doit être intitulé **corrigés**. Étant donné que vous avez seulement deux conditions **Correct** et **corrigés**, et une condition a déjà été utilisée, le **sélection entrée et sortie** boîte de dialogue s’affiche pas cette fois. Si les connecteurs se chevauchent, déplacez un connecteur à gauche et l'autre à droite en les faisant glisser.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 10 : Ajout d’une transformation de regroupement probable pour identifier les doublons](../../2014/tutorials/task-10-adding-fuzzy-group-transform-to-identify-duplicates.md)  
  
  
