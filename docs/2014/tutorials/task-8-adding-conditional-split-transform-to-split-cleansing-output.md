---
title: 'Tâche 8 : ajout d’une transformation de fractionnement conditionnel pour fractionner la sortie de nettoyage | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d4ebe420-a4a9-4076-89d3-41abe726fc5c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d5a55f0694094e6fe88a42946bcff34f420210f4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65489670"
---
# <a name="task-8-adding-conditional-split-transform-to-split-cleansing-output"></a>Tâche 8 : Ajout de la transformation de fractionnement conditionnel pour fractionner la sortie du nettoyage
  Dans cette tâche, vous allez ajouter une transformation de fractionnement conditionnel au flux de données. La transformation de fractionnement conditionnel peut acheminer les lignes vers différentes sorties, suivant le contenu des données. Pour ce didacticiel, vous utilisez la colonne de sortie de l’état de l' **enregistrement** à partir de la transformation de nettoyage DQS. Vous téléchargerez uniquement les enregistrements corrects ou corrigés sur le serveur MDS. Par conséquent, vous pouvez vérifier si l’état de l' **enregistrement** est **correct** ou **corrigé**et combiner les enregistrements avant de charger les enregistrements dans MDS.  
  
1.  Glissez-déplacez la **transformation de fractionnement conditionnel** de la section **commun** dans la **boîte à outils SSIS** vers l’onglet de **Workflow** sous **nettoyer les données des fournisseurs**.  
  
2.  Cliquez avec le bouton droit sur **fractionnement conditionnel**, puis cliquez sur **Renommer**. Tapez **Choisissez les enregistrements corrects et corrigés** , puis appuyez sur **entrée**.  
  
3.  Connectez **nettoyer les données des fournisseurs** et **sélectionnez les enregistrements corrects et corrigés** à l’aide du connecteur bleu.  
  
     ![Nettoyer les données du fournisseur-> choix correct & corrigé](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-01.jpg "Nettoyer les données des fournisseurs -> Choisir les correctes et les corrigées")  
  
4.  Double-cliquez sur **choisir les enregistrements corrects et corrigés** dans l’onglet **Data Flow** .  
  
5.  Modifiez le **nom de sortie par défaut** en bas de l’écran pour **corriger**le nom.  
  
6.  Développez **colonnes** dans le **volet en haut à gauche**.  
  
     ![Éditeur de transformation de fractionnement conditionnel](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-02.jpg "Éditeur de transformation de fractionnement conditionnel")  
  
7.  Glissez-déplacez l’état de l' **enregistrement** vers la colonne **condition** .  
  
8.  Tapez **= = "corrigé"** en regard de **[État de l’enregistrement]** pour la colonne **condition** .  
  
9. Cliquez sur **cas 1** dans la **colonne nom**de la sortie, puis remplacez le nom par **corrigé**.  
  
10. Cliquez sur **OK** pour fermer la boîte de dialogue **éditeur de transformation de fractionnement conditionnel** .  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 9 : Ajout d’une transformation d’union totale pour combiner des enregistrements corrects et corrigés](../../2014/tutorials/task-9-adding-union-all-transform-to-combine-correct-and-corrected-records.md)  
  
  
