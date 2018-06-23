---
title: 'Tâche 13 : Ajout d’une Destination OLE DB pour écrire des données dans une Table intermédiaire MDS | Documents Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e6c67fa9-bb52-44a9-82f6-d86551cf12b2
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 75e77579857852e607b783534d149367a946318f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042123"
---
# <a name="task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table"></a>Tâche 13 : Ajout d'une destination OLE DB pour écrire des données dans une table intermédiaire MDS
  Maintenant que vous avez ajouté **ImportType** et **BatchTag** valeurs à tous les enregistrements, vous êtes prêt à les transmettre à MDS pour l’environnement intermédiaire. Dans cette tâche, vous utilisez la Destination OLE DB pour écrire les données dans **stg.supplier_Leaf** table intermédiaire.  
  
1.  Faites glisser **Destination OLE DB** de **autres Destinations** section dans le **boîte à outils SSIS** à la **de flux de données** onglet et déposez-le sous  **Ajouter les colonnes requises par MDS**.  
  
2.  Avec le bouton droit **Destination OLE DB** dans les **de flux de données** onglet, puis cliquez sur **renommer**. Type **écrire les données de fournisseur dans la Table intermédiaire MDS** et appuyez sur **entrée**.  
  
3.  Connecter le **ajouter les colonnes requises par MDS** à **écrire les données de fournisseur dans la Table intermédiaire MDS** à l’aide du connecteur bleu.  
  
4.  Double-cliquez sur **écrire les données de fournisseur dans la Table intermédiaire MDS** dans les **de flux de données** onglet.  
  
5.  Dans le **éditeur de Destination OLE DB** boîte de dialogue zone, assurez-vous que **(local). MDS** (ou **localhost. MDS**) est sélectionné pour le **Gestionnaire de connexions OLE DB** champ.  
  
6.  Sélectionnez **STG. Supplier_Leaf** table dans la liste des **nom de la table ou la vue**.  
  
     ![Éditeur de Destination OLE DB](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-01.jpg "éditeur de Destination OLE DB")  
  
7.  Basculez vers le **mappages** page en cliquant sur **mappage** dans le menu de gauche.  
  
8.  Carte **d’entrée** et **destination** colonnes comme indiqué dans le tableau suivant.  
  
     ![Éditeur de Destination OLEDB - mappages](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-02.jpg "éditeur de Destination OLEDB - mappages")  
  
9. Vérifiez que vous utilisez **_Output** colonnes pour les colonnes d’entrée, pas le **_état** ou **_Source** colonnes. **_Output** colonnes contiennent les valeurs de sortie du nettoyage DQS.  
  
10. Cliquez sur **OK** pour fermer la **éditeur de Destination OLE DB** boîte de dialogue.  
  
11. Le flux de données devrait être similaire à l'illustration suivante.  
  
     ![Fin de flux de données](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-03.jpg "s’est terminée de flux de données")  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 14 : Ajout de tâche d’exécution SQL au flux de contrôle pour exécuter la procédure stockée pour MDS](../../2014/tutorials/task-14-add-execute-to-control-flow-run-mds-stored-procedure.md)  
  
  