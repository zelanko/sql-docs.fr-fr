---
title: 'Tâche 12 : Ajout d’une transformation de colonne à ajouter les colonnes requises par MDS dérivée | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 98ccb271-04da-4126-9729-67e9a479aaef
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 3c80f719bd756a0ad241ef270507e638b08c2081
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63222643"
---
# <a name="task-12-adding-derived-column-transform-to-add-columns-required-by-mds"></a>Tâche 12 : Ajout d’une transformation de colonne dérivée pour ajouter les colonnes requises par MDS
  Dans cette tâche, vous allez ajouter une transformation de colonne dérivée au flux de données. Vous ajoutez deux colonnes dérivées, **ImportType** et **BatchTag**, vers les enregistrements transmis à cette transformation. Vous devez ajouter ces colonnes avant de télécharger les données dans des tables intermédiaires dans MDS. Ces deux colonnes sont requises pour les tables intermédiaires dans MDS. Consultez [Tables intermédiaires des membres feuille](../master-data-services/leaf-member-staging-table-master-data-services.md) pour plus d’informations.  
  
1.  Glisser-déplacer **transformation de colonne dérivée** à partir de **commune** section dans le **boîte à outils SSIS** à la **de flux de données** onglet.  
  
2.  Avec le bouton droit **colonne dérivée** transformer dans le **de flux de données** onglet, puis cliquez sur **renommer**. Type **ajouter les colonnes requises par MDS** et appuyez sur **entrée**.  
  
3.  Se connecter **filtrer les doublons** à **ajouter les colonnes requises par MDS** à l’aide du connecteur bleu. Vous devez voir le **sélection entrée et sortie** boîte de dialogue.  
  
4.  Dans le **sélection entrée et sortie** boîte de dialogue, sélectionnez **enregistrements uniques**, puis cliquez sur **OK**.  
  
     ![Entrée de boîte de dialogue de sélection de sortie](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-01.jpg "d’entrée de boîte de dialogue de sélection de sortie")  
  
5.  Cliquez sur **SSIS** sur la barre de menus et cliquez sur **Variables**.  
  
6.  Dans le **Variables** fenêtre, cliquez sur **ajouter une Variable** dans la barre d’outils.  
  
     ![Fenêtre Variables SSIS](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-02.jpg "fenêtre Variables SSIS.")  
  
7.  Type **ImportType** pour le **nom** et **2** pour le **valeur**. Vous spécifiez la valeur 2 étant donné que vous souhaitez ajouter de nouveaux membres à une entité dans MDS. Pour plus d’informations sur ce paramètre, consultez [Table intermédiaire des membres feuille](../master-data-services/leaf-member-staging-table-master-data-services.md).  
  
8.  Cliquez sur **ajouter une Variable** à nouveau bouton de barre d’outils.  
  
9. Type **BatchTag** pour le **nom**, sélectionnez **chaîne** pour le **type de données**, et **EIMBatch** pour le **Valeur**. **BatchTag** est simplement un nom unique pour le lot que vous soumettrez à MDS.  
  
10. Dans le **de flux de données** onglet, double-cliquez sur **ajouter les colonnes requises par MDS**.  
  
11. Dans le **éditeur de Transformation de colonne dérivée** boîte de dialogue le **zone de liste dans le volet inférieur**, type **ImportType** pour le **nom de colonne dérivée**.  
  
12. Développez **Variables et paramètres** dans le volet supérieur gauche, glissez-déposez **User::ImportType** à la **Expression** colonne.  
  
     ![Dérivés d’éditeur de Transformation de colonne](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-03.jpg "dérivés d’éditeur de Transformation de colonne")  
  
13. Type **BatchTag** dans la ligne suivante pour le **nom de colonne dérivée**.  
  
14. Glisser-déplacer **User::BatchTag** de **Variables et paramètres** à la **Expression** colonne.  
  
15. Cliquez sur **OK** pour fermer la **Transformation de colonne dérivée** boîte de dialogue.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 13 : Ajout de Destination OLE DB pour écrire des données dans la Table intermédiaire MDS](../../2014/tutorials/task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table.md)  
  
  
