---
title: 'Tâche 1 : Définir une stratégie de correspondance | Microsoft Docs'
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
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65481312"
---
# <a name="task-1-defining-a-matching-policy"></a>Tâche 1 : Définition d’une stratégie de correspondance
  Dans cette tâche, vous allez créer une stratégie de correspondance contenant une règle. La règle aura une condition préalable : **ID du fournisseur**, ce qui signifie que les ID des fournisseurs doivent correspondre avant d’utiliser les autres domaines dans la règle. La règle utilise deux autres domaines : **Nom du fournisseur** avec **similarité** la valeur **70 %** et **adresse E-mail de Contact** avec **similarité** la valeur **30 %**.  
  
1.  Dans la page principale de **Client DQS**, cliquez sur **flèche droite** regard **fournisseurs** connaissances de base, puis sélectionnez **stratégie de correspondance**.  
  
     ![Menu de stratégie principal de correspondance Page](../../2014/tutorials/media/et-definingamatchingpolicy-01.jpg "Main Menu stratégie de correspondance Page")  
  
2.  Sur le **carte** page, sélectionnez **fichier Excel** pour **Source de données**.  
  
3.  Cliquez sur **Parcourir**, vérifiez que le filtre est défini sur **classeur Excel**, puis sélectionnez **Cleansed Supplier List.xls** que vous avez exporté après avoir effectué l’activité de nettoyage de fichiers.  
  
    > [!NOTE]  
    >  À la fin de cette activité, vous ne pourrez pas exporter les résultats car l'activité est principalement axées sur la définition d'une stratégie de correspondance. Vous allez créer un projet de qualité des données pour l'activité de correspondance, et l'exécuter pour supprimer les doublons de la liste des fournisseurs en utilisant cette stratégie de correspondance dans la leçon suivante.  
  
4.  Carte **SupplierID** colonne à **ID du fournisseur** domaine, **Supplier Name** colonne à **Supplier Name** domaine,  **ContactEmailAddress** colonne à **adresse E-mail de Contact** domaine. Vous devez uniquement mapper les colonnes sources aux domaines que vous souhaitez utiliser pour définir la stratégie de correspondance. Dans ce cas, vous allez rendre les domaines ID du fournisseur, Nom du fournisseur et Adresse de messagerie du contact disponibles pour l'activité de stratégie de correspondance.  
  
     ![Page du processus de définition de stratégie de correspondance de mappage](../../2014/tutorials/media/et-definingamatchingpolicy-02.jpg "Page du processus de définition de stratégie de correspondance de mappage")  
  
5.  Cliquez sur **suivant** pour déplacer vers le **stratégie de correspondance** page où vous allez définir une stratégie de correspondance avec une règle qu’il contient.  
  
6.  Cliquez sur **créer une règle de correspondance** la barre d’outils pour créer une règle dans la stratégie.  
  
     ![Créer un bouton de barre d’outils de règle correspondante](../../2014/tutorials/media/et-definingamatchingpolicy-03.jpg "créer un bouton de barre d’outils de règle correspondante")  
  
7.  Dans le **détails de la règle** volet de droite, entrez **supprimer les fournisseurs en double** pour le **nom de la règle**.  
  
8.  Cliquez sur **ajouter un nouvel élément de domaine** dans la barre d’outils dans le volet droit.  
  
     ![Détails - de la règle d’ajouter un nouveau bouton d’élément de domaine](../../2014/tutorials/media/et-definingamatchingpolicy-04.jpg "détails - de la règle d’ajouter un nouveau bouton d’élément de domaine")  
  
9. Sélectionnez **ID du fournisseur** pour le **domaine** et sélectionnez le **prérequis** case à cocher. Notez que **similarité** est automatiquement défini sur **Exact**. En définissant **ID du fournisseur** en tant que le **prérequis**, vous spécifiez que les valeurs pour ce champ dans les deux enregistrements doivent retourner une correspondance de 100 %, sans quoi les enregistrements ne sont pas considérés comme une correspondance et les autres clauses de la règle sont ignorés.  
  
     ![Supprimer la définition de règle de fournisseurs en double](../../2014/tutorials/media/et-definingamatchingpolicy-05.jpg "supprimer la définition de règle de fournisseurs en double")  
  
10. Cliquez sur **ajouter un nouvel élément de domaine** à partir de la barre d’outils à nouveau.  
  
11. Sélectionnez **Supplier Name** domaine, sélectionnez **similaire** pour **similarité**et le Type **70** pour le **poids**.  Ici, vous spécifiez que les noms des fournisseurs n'ont pas besoin d'être identiques, mais peuvent être similaires pour que les enregistrements soient considérés comme une correspondance. Le poids indique la contribution du score de ce champ au score de correspondance global.  
  
12. Répétez les étapes précédentes pour ajouter **adresse E-mail de Contact** domaine avec **30** pour le **poids**.  
  
13. Notez que le **min score de correspondance** a la valeur **80 %**, qui est la valeur que vous voyez dans le **général** onglet de la **Configuration** page de **Administration de DQS**. Vous ne pouvez augmenter ce score qu'au-dessus de cette valeur de seuil, ici.  
  
14. Notez que **Clusters qui se chevauchent** option est sélectionnée. Avec cette option, un enregistrement peut apparaître dans plusieurs clusters. Si vous modifiez le paramètre en Clusters qui ne se chevauchent pas, les clusters qui ont des enregistrements communs sont combinés dans un seul cluster.  
  
15. Le **Démarrer** bouton sur cette page vous permet de tester chaque règle dans la stratégie séparément, tandis que le bouton Démarrer dans la page suivante vous permet de tester la stratégie entière (toutes les règles dans la stratégie).  
  
16. Cliquez sur **suivant** pour basculer vers le **résultats de correspondance** page.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 2 : Test et publication de la stratégie de correspondance](../../2014/tutorials/task-2-testing-and-publishing-the-matching-policy.md)  
  
  
