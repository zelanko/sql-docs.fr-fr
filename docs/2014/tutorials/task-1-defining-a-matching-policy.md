---
title: 'Tâche 1 : définition d’une stratégie de correspondance | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6f89a720-fce5-4f60-bef3-a159bbc9f25c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 3e4777cf05e7f3eab62c389ace8b8d8a96cae304
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65481312"
---
# <a name="task-1-defining-a-matching-policy"></a>Tâche 1 : Définition d’une stratégie de correspondance
  Dans cette tâche, vous allez créer une stratégie de correspondance contenant une règle. La règle aura un élément requis : **ID du fournisseur**, ce qui signifie que les ID des fournisseurs doivent correspondre avant d’utiliser les autres domaines de la règle. La règle utilise deux autres domaines : **nom du fournisseur** avec une valeur **de similarité** définie sur **70%** et **adresse de messagerie du contact** avec une valeur **de similarité** définie à **30%**.  
  
1.  Dans la page principale du **client DQS**, cliquez sur la **flèche droite** en regard de la base de connaissances **fournisseurs** , puis sélectionnez **stratégie de correspondance**.  
  
     ![Menu Stratégie de correspondance dans la Page principale](../../2014/tutorials/media/et-definingamatchingpolicy-01.jpg "Menu Stratégie de correspondance dans la Page principale")  
  
2.  Dans la page **mapper** , sélectionnez **fichier Excel** pour **source de données**.  
  
3.  Cliquez sur **Parcourir**, assurez-vous que filtre est défini sur **classeur Excel**, puis sélectionnez le fichier **cleaned Supplier List. xls** que vous avez exporté après avoir effectué l’activité de nettoyage.  
  
    > [!NOTE]  
    >  À la fin de cette activité, vous ne pourrez pas exporter les résultats car l'activité est principalement axées sur la définition d'une stratégie de correspondance. Vous allez créer un projet de qualité des données pour l'activité de correspondance, et l'exécuter pour supprimer les doublons de la liste des fournisseurs en utilisant cette stratégie de correspondance dans la leçon suivante.  
  
4.  Mappez la colonne **RéfFournisseur** au domaine de l' **ID** de fournisseur, la colonne **nom du fournisseur** au **nom du fournisseur** domaine, la colonne **ContactEmailAddress** sur contacter le domaine de **messagerie** . Vous devez uniquement mapper les colonnes sources aux domaines que vous souhaitez utiliser pour définir la stratégie de correspondance. Dans ce cas, vous allez rendre les domaines ID du fournisseur, Nom du fournisseur et Adresse de messagerie du contact disponibles pour l'activité de stratégie de correspondance.  
  
     ![Page de mappage du processus de définition de la stratégie de correspondance](../../2014/tutorials/media/et-definingamatchingpolicy-02.jpg "Page de mappage du processus de définition de la stratégie de correspondance")  
  
5.  Cliquez sur **suivant** pour passer à la page **stratégie de correspondance** dans laquelle vous allez définir une stratégie de correspondance avec une règle.  
  
6.  Cliquez sur le bouton **créer une règle de correspondance** dans la barre d’outils pour créer une règle dans la stratégie.  
  
     ![Bouton à la barre d'outils Créer une règle de correspondance](../../2014/tutorials/media/et-definingamatchingpolicy-03.jpg "Bouton à la barre d'outils Créer une règle de correspondance")  
  
7.  Dans le volet Détails de la **règle** à droite, entrez **Supprimer les fournisseurs en double** pour le nom de la **règle**.  
  
8.  Dans le volet droit, cliquez sur **Ajouter un nouvel élément de domaine** dans la barre d’outils.  
  
     ![Détails de la règle - Bouton Ajouter un nouvel élément de domaine](../../2014/tutorials/media/et-definingamatchingpolicy-04.jpg "Détails de la règle - Bouton Ajouter un nouvel élément de domaine")  
  
9. Sélectionnez **ID du fournisseur** pour le **domaine** , puis activez la case à cocher **conditions préalables** . Notez que **la similarité** est définie automatiquement sur **exact**. En définissant l' **ID du fournisseur** comme **condition préalable**, vous spécifiez que les valeurs de ce champ dans les deux enregistrements doivent retourner une correspondance de 100%, sinon les enregistrements ne sont pas considérés comme une correspondance et les autres clauses de la règle sont ignorées.  
  
     ![Supprimer la définition de la règle des fournisseurs dupliqués](../../2014/tutorials/media/et-definingamatchingpolicy-05.jpg "Supprimer la définition de la règle des fournisseurs dupliqués")  
  
10. Cliquez à nouveau sur **Ajouter un nouvel élément de domaine** dans la barre d’outils.  
  
11. Sélectionnez **nom du fournisseur** domaine, sélectionnez **similaire** pour **similarité**, et tapez **70** pour le **poids**.  Ici, vous spécifiez que les noms des fournisseurs n'ont pas besoin d'être identiques, mais peuvent être similaires pour que les enregistrements soient considérés comme une correspondance. Le poids indique la contribution du score de ce champ au score de correspondance global.  
  
12. Répétez les deux étapes précédentes pour ajouter le domaine de **messagerie de contact** à **30** pour le **poids**.  
  
13. Notez que le **score de correspondance minimal** est défini sur **80%**, ce qui correspond à la valeur que vous voyez dans l’onglet **général** de la page de **configuration** de l' **administration de DQS**. Vous ne pouvez augmenter ce score qu'au-dessus de cette valeur de seuil, ici.  
  
14. Notez que l’option **clusters qui se chevauchent** est sélectionnée. Avec cette option, un enregistrement peut apparaître dans plusieurs clusters. Si vous modifiez le paramètre en Clusters qui ne se chevauchent pas, les clusters qui ont des enregistrements communs sont combinés dans un seul cluster.  
  
15. Le bouton **Démarrer** sur cette page vous permet de tester chaque règle de la stratégie séparément, tandis que le bouton Démarrer dans la page suivante vous permet de tester la stratégie entière (toutes les règles de la stratégie).  
  
16. Cliquez sur **suivant** pour passer à la page **résultats de correspondance** .  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 2 : Test et publication de la stratégie de correspondance](../../2014/tutorials/task-2-testing-and-publishing-the-matching-policy.md)  
  
  
