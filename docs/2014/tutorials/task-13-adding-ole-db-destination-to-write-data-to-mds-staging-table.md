---
title: 'Tâche 13 : ajout d’OLE DB destination pour écrire des données dans la table de mise en lots MDS | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: e6c67fa9-bb52-44a9-82f6-d86551cf12b2
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7c5fc9d863c23c1cae08c04fef7810aeda446762
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65476985"
---
# <a name="task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table"></a>Tâche 13 : Ajout d'une destination OLE DB pour écrire des données dans une table intermédiaire MDS
  Maintenant que vous avez ajouté des valeurs **ImportType** et **BatchTag** à tous les enregistrements, vous êtes prêt à les envoyer à MDS pour la mise en lots. Au cours de cette tâche, vous allez utiliser la destination de la OLE DB pour écrire les données dans **STG. supplier_Leaf** table de mise en lots.  
  
1.  Faites **glisser OLE DB** la section destination à partir d' **autres destinations** de la **boîte à outils SSIS** vers l’onglet de **Workflow** et déposez-la sous **Ajouter les colonnes requises par MDS**.  
  
2.  Cliquez avec le bouton droit sur **OLE DB destination** dans l’onglet **Flow Data** , puis cliquez sur **Renommer**. Tapez **écrire les données des fournisseurs dans la table intermédiaire MDS** et appuyez sur **entrée**.  
  
3.  Connectez le **module ajouter les colonnes requises par MDS** pour **écrire les données des fournisseurs dans la table intermédiaire MDS** à l’aide du connecteur bleu.  
  
4.  Double-cliquez sur **écrire les données des fournisseurs dans la table intermédiaire MDS** sous l’onglet du tableau de **bord de données** .  
  
5.  Dans la boîte de dialogue **éditeur de Destination OLE DB** , assurez-vous que **(local). MDS** (ou **localhost. MDS**) est sélectionné pour le champ **Gestionnaire de connexions OLE DB** .  
  
6.  Sélectionnez **STG. Supplier_Leaf** table de la liste de **noms de la table ou**de la vue.  
  
     ![Éditeur de destination OLEDB](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-01.jpg "Éditeur de destination OLEDB")  
  
7.  Basculez vers la page **mappages** en cliquant sur **mappage** dans le menu de gauche.  
  
8.  Mappez les colonnes **d’entrée** et de **destination** comme indiqué dans le tableau suivant.  
  
     ![Éditeur de destination OLEDB - Mappages](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-02.jpg "Éditeur de destination OLEDB - Mappages")  
  
9. Vérifiez que vous utilisez **_output** colonnes pour les colonnes d’entrée, et non les colonnes **_Status** ou **_source** . **_Output** colonnes contiennent les valeurs de sortie du nettoyage DQS.  
  
10. Cliquez sur **OK** pour fermer la boîte de dialogue **éditeur de destination de OLE DB** .  
  
11. Le flux de données devrait être similaire à l'illustration suivante.  
  
     ![Flux de données terminé](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-03.jpg "Flux de données terminé")  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 14 : Ajout d'une tâche d'exécution SQL au flux de contrôle pour exécuter la procédure stockée pour MDS](../../2014/tutorials/task-14-add-execute-to-control-flow-run-mds-stored-procedure.md)  
  
  
