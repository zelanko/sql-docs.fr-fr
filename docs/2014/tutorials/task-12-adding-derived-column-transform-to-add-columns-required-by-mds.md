---
title: 'Tâche 12 : ajout d’une transformation de colonne dérivée pour ajouter des colonnes requises par MDS | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 98ccb271-04da-4126-9729-67e9a479aaef
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8eac057177032892ac99f557aa9d18ce497b7b2f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054291"
---
# <a name="task-12-adding-derived-column-transform-to-add-columns-required-by-mds"></a>Tâche 12 : Ajout d’une transformation de colonne dérivée pour ajouter les colonnes requises par MDS
  Dans cette tâche, vous allez ajouter une transformation de colonne dérivée au flux de données. Vous ajoutez deux colonnes dérivées, **ImportType** et **BatchTag**, aux enregistrements passés à cette transformation. Vous devez ajouter ces colonnes avant de télécharger les données dans des tables intermédiaires dans MDS. Ces deux colonnes sont requises pour les tables intermédiaires dans MDS. Pour plus d’informations, consultez [tables de mise en lots des membres feuille](../master-data-services/leaf-member-staging-table-master-data-services.md) .  
  
1.  Glissez-déplacez la **transformation de colonne dérivée** de la section **commun** dans la **boîte à outils SSIS** vers l’onglet de **Workflow** .  
  
2.  Cliquez avec le bouton droit sur transformation de **colonne dérivée** sous l’onglet **Flow Data** , puis cliquez sur **Renommer**. Tapez **Add Columns required by MDS** et appuyez sur **entrée**.  
  
3.  Connectez les **doublons de filtre** pour **Ajouter les colonnes requises par MDS** à l’aide du connecteur Blue. La boîte de dialogue **sélection de sortie d’entrée** doit s’afficher.  
  
4.  Dans la boîte de dialogue **sélection de sortie d’entrée** , sélectionnez **enregistrements uniques**, puis cliquez sur **OK**.  
  
     ![Boîte de dialogue Sélection entrée et sortie](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-01.jpg "Boîte de dialogue Sélection entrée et sortie")  
  
5.  Cliquez sur **SSIS** dans la barre de menus et cliquez sur **variables**.  
  
6.  Dans la fenêtre **variables** , cliquez sur le bouton **Ajouter une variable** de la barre d’outils.  
  
     ![Fenêtre Variables SSIS.](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-02.jpg "Fenêtre Variables SSIS.")  
  
7.  Tapez **ImportType** pour le **nom** et **2** pour la **valeur**. Vous spécifiez la valeur 2 étant donné que vous souhaitez ajouter de nouveaux membres à une entité dans MDS. Pour plus d’informations sur ce paramètre, consultez [table de mise en lots des membres feuille](../master-data-services/leaf-member-staging-table-master-data-services.md).  
  
8.  Cliquez à nouveau sur le bouton **Ajouter une variable** de la barre d’outils.  
  
9. Tapez **BatchTag** pour le **nom**, sélectionnez **chaîne** comme **type de données**et **EIMBatch** pour la **valeur**. **BatchTag** est simplement un nom unique pour le lot que vous allez soumettre à MDS.  
  
10. Sous l’onglet **Data Flow** , double-cliquez sur **Add Columns required by MDS**.  
  
11. Dans la boîte de dialogue **éditeur de transformation de colonne dérivée** , dans la **zone de liste dans le volet inférieur**, tapez **ImportType** pour le nom de la **colonne dérivée**.  
  
12. Développez **variables et paramètres** dans le volet supérieur gauche, glissez-déposez **User :: ImportType** dans la colonne **expression** .  
  
     ![Éditeur de transformation de colonne dérivée](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-03.jpg "Éditeur de transformation de colonne dérivée")  
  
13. Tapez **BatchTag** dans la ligne suivante pour le **nom de la colonne dérivée**.  
  
14. Faites glisser **User :: BatchTag** à partir de **variables et de paramètres** vers la colonne **expression** .  
  
15. Cliquez sur **OK** pour fermer la boîte de dialogue **transformation de colonne dérivée** .  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 13 : Ajout d’une destination OLE DB pour écrire des données dans une table intermédiaire MDS](../../2014/tutorials/task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table.md)  
  
  
