---
title: Création d’un modèle Sequence Clustering associé (Didacticiel intermédiaire sur l’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1fb4f5bc-1756-45ca-9cd7-411a8c5992a9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 71db7ba5246e151bbca8a52972a2ba835b80ddb6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62855875"
---
# <a name="creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial"></a>Création d'un modèle Sequence Clustering associé (Didacticiel sur l'exploration de données intermédiaire)
  Au cours de votre exploration du modèle Sequence Clustering, vous avez appris que d'autres attributs tels que Region ou Income ont de fortes répercussions sur les modèles ; par conséquent, pour mieux comprendre les séquences, vous allez créer un modèle Sequence Clustering associé et supprimer les attributs en rapport avec les caractéristiques démographiques des clients.  
  
 Au cours de cette tâche, vous allez créer une copie du modèle Sequence Clustering régional, puis supprimer du modèle toutes les colonnes qui ne sont pas directement en rapport avec les séquences.  
  
 Le nouveau modèle va contenir les mêmes colonnes que le modèle d'exploration de données sur lequel il se base. Toutefois, vous n'avez pas besoin de supprimer les colonnes de la structure d'exploration de données ; spécifiez simplement que le nouveau modèle d'exploration de données ignore ces colonnes.  
  
### <a name="to-make-a-copy-of-the-sequence-clustering-model"></a>Pour faire une copie du modèle Sequence Clustering  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans le concepteur d’exploration de données, cliquez sur l’onglet **modèles d’exploration** de données.  
  
2.  Cliquez avec le bouton droit sur le modèle que vous souhaitez copier, puis sélectionnez **nouveau modèle d’exploration de données**.  
  
3.  Dans la boîte de dialogue **nouveau modèle d’exploration de données** , tapez un nom de `Sequence Clustering`modèle, puis sélectionnez Microsoft.  
  
     Pour ce didacticiel, tapez le nom `Sequence Clustering`.  
  
4.  Cliquez sur **OK**.  
  
### <a name="to-remove-columns-from-the-mining-model"></a>Pour supprimer des colonnes du modèle d'exploration de données  
  
1.  Dans l’onglet **modèle d’exploration de données** , dans la colonne du nouveau modèle nommé Sequence Clustering, cliquez sur la ligne correspondant à l’attribut **revenu Group** , puis sélectionnez **Ignorer**.  
  
2.  Répétez cette étape pour la **région**d’attribut.  
  
3.  Cliquez sur le signe plus (+) en regard du nom de la table, **v Assoc SEQ Line Items**, pour développer la table et afficher les colonnes de la table imbriquée.  
  
     Le nouveau modèle doit comporter uniquement les colonnes suivantes :  
  
     **NumberKey de commande**  
  
     **Clé de numéro de ligne**  
  
     **Prédiction de modèle**  
  
### <a name="to-process-the-new-sequence-clustering-model"></a>Pour traiter le nouveau modèle Sequence Clustering  
  
1.  Sous l’onglet **modèle d’exploration de données** , cliquez avec le bouton `Sequence Clustering`droit sur le nouveau modèle nommé, puis sélectionnez **traiter le modèle**.  
  
     Étant donné que le nouveau modèle d'exploration de données simplifié est basé sur une structure qui a déjà été traitée, vous n'avez pas besoin de retraiter la structure. Vous pouvez traiter simplement le nouveau modèle d'exploration de données.  
  
2.  Cliquez sur **Oui** pour déployer le projet d’exploration de données mis à jour sur le serveur.  
  
3.  Dans la boîte de dialogue **traiter le modèle d’exploration de données** , cliquez sur **exécuter**.  
  
4.  Cliquez sur **Fermer** pour fermer la boîte de dialogue **État d’avancement du traitement** , puis cliquez de nouveau sur **Fermer** dans la boîte de dialogue traiter le modèle d' **exploration de données** .  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Création de prédictions sur un modèle Sequence Clustering &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exigences et considérations concernant le traitement &#40;exploration de données&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
