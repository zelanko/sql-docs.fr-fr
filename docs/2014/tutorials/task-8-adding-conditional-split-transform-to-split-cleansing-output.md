---
title: 'Tâche 8 : Ajout conditionnel fractionner la transformation pour fractionner la sortie de nettoyage | Documents Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4ebe420-a4a9-4076-89d3-41abe726fc5c
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6dc3b98e03a7940841bc97012c1a4e4220bb970d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140208"
---
# <a name="task-8-adding-conditional-split-transform-to-split-cleansing-output"></a>Tâche 8 : Ajout de la transformation de fractionnement conditionnel pour fractionner la sortie du nettoyage
  Dans cette tâche, vous allez ajouter une transformation de fractionnement conditionnel au flux de données. La transformation de fractionnement conditionnel peut acheminer les lignes vers différentes sorties, suivant le contenu des données. Pour ce didacticiel, vous utilisez la **état de l’enregistrement** colonne de sortie de la transformation de nettoyage DQS. Vous téléchargerez uniquement les enregistrements corrects ou corrigés sur le serveur MDS. Par conséquent vous permet de vérifier si le **état de l’enregistrement** est **Correct** ou **corrigés**et combiner des enregistrements avant de les télécharger dans MDS.  
  
1.  Glisser-déplacer **transformation de fractionnement conditionnel** de **courantes** section dans le **boîte à outils SSIS** à la **de flux de données** onglet sous **Nettoyer les données des fournisseurs**.  
  
2.  Avec le bouton droit **fractionnement conditionnel**, puis cliquez sur **renommer**. Type **Pick enregistrements corrects et corrigés** et appuyez sur **entrée**.  
  
3.  Se connecter **nettoyer les données des fournisseurs** et **Pick enregistrements corrects et corrigés** à l’aide du connecteur bleu.  
  
     ![Nettoyer le fournisseur données -> choisir les correctes et corrigé](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-01.jpg "nettoyer fournisseur données -> choisir les correctes et corrigée")  
  
4.  Double-cliquez sur **Pick enregistrements corrects et corrigés** dans les **de flux de données** onglet.  
  
5.  Modifier la **nom de sortie par défaut** au bas de l’écran pour **Correct**.  
  
6.  Développez **colonnes** dans les **volet en haut à gauche**.  
  
     ![Éditeur de Transformation de fractionnement conditionnel](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-02.jpg "éditeur de Transformation de fractionnement conditionnel")  
  
7.  Glisser-déplacer **état de l’enregistrement** à la **Condition** colonne.  
  
8.  Type **== « Corrigé »** regard **[état de l’enregistrement]** pour le **Condition** colonne.  
  
9. Cliquez sur **cas 1** dans les **colonne de nom de sortie**et remplacez le nom par **corrigés**.  
  
10. Cliquez sur **OK** pour fermer la **éditeur de Transformation de fractionnement conditionnel** boîte de dialogue.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 9 : Ajout d’Union tous les transformation pour combiner des enregistrements corrects et corrigés](../../2014/tutorials/task-9-adding-union-all-transform-to-combine-correct-and-corrected-records.md)  
  
  