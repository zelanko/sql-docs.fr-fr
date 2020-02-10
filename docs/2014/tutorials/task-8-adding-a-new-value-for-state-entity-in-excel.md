---
title: 'Tâche 8 : ajout d’une nouvelle valeur pour l’entité État dans Excel | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a763d76b-06a3-4d51-9614-01fc9fb1c158
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 831d0b504a65d485413772ee3711e689e29ee2a3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65489705"
---
# <a name="task-8-adding-a-new-value-for-state-entity-in-excel"></a>Tâche 8 : Ajout d'une nouvelle valeur pour l'entité État dans Excel
  Dans cette tâche, vous allez ajouter une valeur pour l'entité État dans Excel et publier la modification sur le serveur MDS.  
  
1.  Ajoutez une **feuille de travail** dans Excel en cliquant sur l’onglet nouveau situé en bas.  
  
     ![Excel - Onglet Nouvelle feuille de calcul](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel - Onglet Nouvelle feuille de calcul")  
  
2.  Dans **Excel**, cliquez sur l’onglet **données** de référence dans le menu, puis sur **afficher l’Explorateur** sur le ruban.  
  
3.  Dans le **Explorateur de données maître**, sélectionnez **Suppliers** pour **Model**. Vous devez voir deux entités : **Supplier** et **State** dans la liste d’entités.  
  
4.  Double-cliquez sur **État** dans la liste. Tous les membres de l’entité **État** de MDS doivent être affichés dans la feuille de calcul.  
  
5.  À présent, ajoutez une ligne à la fin avec les valeurs suivantes : **Caroline du Nord** pour **nom** et **NC** pour le **code**. Les codes de couleur différencient tous les nouveaux enregistrements, ou les enregistrements mis à jour, des autres enregistrements.  
  
     ![Excel - Ajouter North Carolina aux États](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel - Ajouter North Carolina aux États")  
  
6.  Cliquez sur **publier** sur le ruban pour publier la modification dans MDS.  
  
     ![Excel - Bouton Publier dans l'onglet des données de référence](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel - Bouton Publier dans l'onglet des données de référence")  
  
7.  Dans la boîte de dialogue **publier et annoter** , Notez que l’option **utiliser la même annotation pour toutes les modifications** est sélectionnée. Vous pouvez entrer ici une annotation unique pour toutes les modifications apportées.  
  
8.  Sélectionnez l’option **vérifier les modifications et fournir des annotations individuellement** pour fournir une annotation pour chaque modification (dans ce cas, une seule).  
  
     ![Excel - Boîte de dialogue Publier et annoter](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "Excel - Boîte de dialogue Publier et annoter")  
  
9. Cliquez sur **publier** pour publier des données sur MDS.  
  
10. Notez que le **codage en couleurs** pour la ligne avec **Caroline du Nord** comme **État** est le même que pour les autres enregistrements maintenant.  
  
11. **Facultatif :** Vérifiez que le nouveau membre (NC) est ajouté à l’entité **État** à l’aide de l' **explorateur** dans le **Data Manager maître**.  
  
12. Dans Excel, cliquez avec le bouton droit sur la feuille de calcul **État** en bas, puis cliquez sur **supprimer** pour supprimer la feuille de calcul. La suppression de la feuille de calcul ne supprime aucune donnée dans le serveur MDS.  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 9 : Création d'une hiérarchie dérivée à l'aide de Master Data Manager](../../2014/tutorials/task-9-creating-a-derived-hierarchy-using-master-data-manager.md)  
  
  
