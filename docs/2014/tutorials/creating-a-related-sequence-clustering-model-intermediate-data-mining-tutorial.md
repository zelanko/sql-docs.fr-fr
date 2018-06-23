---
title: Création d’un modèle Sequence Clustering associé (didacticiel sur l’exploration des données intermédiaires) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fb4f5bc-1756-45ca-9cd7-411a8c5992a9
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c0820b087583194e78af1d1de46b4affe3a1d9fc
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36311807"
---
# <a name="creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial"></a>Création d'un modèle Sequence Clustering associé (Didacticiel sur l'exploration de données intermédiaire)
  Au cours de votre exploration du modèle Sequence Clustering, vous avez appris que d'autres attributs tels que Region ou Income ont de fortes répercussions sur les modèles ; par conséquent, pour mieux comprendre les séquences, vous allez créer un modèle Sequence Clustering associé et supprimer les attributs en rapport avec les caractéristiques démographiques des clients.  
  
 Au cours de cette tâche, vous allez créer une copie du modèle Sequence Clustering régional, puis supprimer du modèle toutes les colonnes qui ne sont pas directement en rapport avec les séquences.  
  
 Le nouveau modèle va contenir les mêmes colonnes que le modèle d'exploration de données sur lequel il se base. Toutefois, vous n'avez pas besoin de supprimer les colonnes de la structure d'exploration de données ; spécifiez simplement que le nouveau modèle d'exploration de données ignore ces colonnes.  
  
### <a name="to-make-a-copy-of-the-sequence-clustering-model"></a>Pour faire une copie du modèle Sequence Clustering  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans le Concepteur d’exploration de données, cliquez sur le **des modèles d’exploration de données** onglet.  
  
2.  Cliquez sur le modèle que vous souhaitez copier et sélectionnez **nouveau modèle d’exploration de données**.  
  
3.  Dans le **nouveau modèle d’exploration de données** boîte de dialogue, tapez un nom de modèle, sélectionnez Microsoft `Sequence Clustering`.  
  
     Pour ce didacticiel, tapez le nom `Sequence Clustering`.  
  
4.  Cliquez sur **OK**.  
  
### <a name="to-remove-columns-from-the-mining-model"></a>Pour supprimer des colonnes du modèle d'exploration de données  
  
1.  Dans le **modèle d’exploration de données** onglet, dans la colonne pour le nouveau modèle nommé Sequence Clustering, cliquez sur la ligne pour le **Income Group** d’attribut, puis sélectionnez **ignorer**.  
  
2.  Répétez cette étape pour l’attribut **région**.  
  
3.  Cliquez sur le signe plus en regard du nom de la table, **v Assoc Seq Line Items**, pour développer la table et afficher les colonnes de la table imbriquée.  
  
     Le nouveau modèle doit comporter uniquement les colonnes suivantes :  
  
     **Commande NumberKey**  
  
     **Clé de numéro de ligne**  
  
     **Modèle de prévision**  
  
### <a name="to-process-the-new-sequence-clustering-model"></a>Pour traiter le nouveau modèle Sequence Clustering  
  
1.  Dans le **modèle d’exploration de données** onglet, cliquez sur le nouveau modèle nommé `Sequence Clustering`, puis sélectionnez **modèle de processus**.  
  
     Étant donné que le nouveau modèle d'exploration de données simplifié est basé sur une structure qui a déjà été traitée, vous n'avez pas besoin de retraiter la structure. Vous pouvez traiter simplement le nouveau modèle d'exploration de données.  
  
2.  Cliquez sur **Oui** pour déployer le projet d’exploration de données mises à jour sur le serveur.  
  
3.  Dans le **traiter le modèle d’exploration de données** boîte de dialogue, cliquez sur **exécuter**.  
  
4.  Cliquez sur **fermer** pour fermer la **progression du processus** boîte de dialogue, puis cliquez sur **fermer** à nouveau dans le **traiter le modèle d’exploration de données** boîte de dialogue.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Création de prédictions sur un modèle Sequence Clustering &#40;intermédiaire Didacticiel d’exploration de données&#41;](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement de la configuration requise et considérations &#40;d’exploration de données&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  