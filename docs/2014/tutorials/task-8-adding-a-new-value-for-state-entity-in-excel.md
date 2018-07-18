---
title: 'Tâche 8 : Ajout d’une nouvelle valeur pour l’entité état dans Excel | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a763d76b-06a3-4d51-9614-01fc9fb1c158
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4f4e79915ba28beb7cd28920faff2f79e6b339d6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163770"
---
# <a name="task-8-adding-a-new-value-for-state-entity-in-excel"></a>Tâche 8 : Ajout d'une nouvelle valeur pour l'entité État dans Excel
  Dans cette tâche, vous allez ajouter une valeur pour l'entité État dans Excel et publier la modification sur le serveur MDS.  
  
1.  Ajouter un **feuille de calcul** dans Excel en cliquant sur le nouvel onglet en bas.  
  
     ![Excel - nouvel onglet de feuille de calcul](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel - nouvel onglet de feuille de calcul")  
  
2.  Dans **Excel**, cliquez sur le **données maîtres** onglet dans le menu, puis cliquez sur **afficher l’Explorateur** sur le ruban.  
  
3.  Dans le **Explorateur de données de référence**, sélectionnez **fournisseurs** pour **modèle**. Vous devez voir deux entités : **fournisseur** et **état** dans la liste des entités.  
  
4.  Double-cliquez sur **état** dans la liste. Tous les membres de la **état** entité à partir de MDS doit être affichée dans la feuille de calcul.  
  
5.  Maintenant, ajoutez une ligne à la fin avec les valeurs suivantes : **Caroline du Nord** pour **nom** et **NC** pour **Code**. Les codes de couleur différencient tous les nouveaux enregistrements, ou les enregistrements mis à jour, des autres enregistrements.  
  
     ![Excel - ajouter North Carolina aux États](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel - ajouter North Carolina aux États")  
  
6.  Cliquez sur **publier** sur le ruban pour publier la modification dans MDS.  
  
     ![Excel - bouton sur l’onglet de données Master publier](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel - bouton sur l’onglet de données Master publier")  
  
7.  Sur le **publier et annoter** boîte de dialogue zone, notez que le **utiliser la même annotation pour toutes les modifications** est sélectionné. Vous pouvez entrer ici une annotation unique pour toutes les modifications apportées.  
  
8.  Sélectionnez **réviser les modifications et fournir des annotations individuellement** option pour spécifier une annotation pour chaque modification (dans ce cas, qu’un seul).  
  
     ![Excel - publier et annoter la boîte de dialogue](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "Excel : publier et annoter la boîte de dialogue")  
  
9. Cliquez sur **publier** pour publier des données dans MDS.  
  
10. Notez que **codage en couleurs** pour la ligne avec **Caroline du Nord** en tant que le **état** est identique à celui des autres enregistrements maintenant.  
  
11. **Facultatif :** Vérifiez que le nouveau membre (NC) est ajouté à la **état** entité à l’aide de la **Explorer** dans **Master Data Manager**.  
  
12. Dans Excel, cliquez sur le **état** feuille de calcul en bas, cliquez sur **supprimer** à supprimer de la feuille de calcul. La suppression de la feuille de calcul ne supprime aucune donnée dans le serveur MDS.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 9 : Création d’une hiérarchie dérivée à l’aide de Master Data Manager](../../2014/tutorials/task-9-creating-a-derived-hierarchy-using-master-data-manager.md)  
  
  
