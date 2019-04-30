---
title: 'Tâche 2 : Téléchargement des données des fournisseurs vers MDS à l’aide de complément MDS pour Excel | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 598deb57-e0cc-4e0a-aeb1-94432c094c67
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 1cbaacd23fcaa1e28d6cce6d64a168d0fab4befc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63250223"
---
# <a name="task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel"></a>Tâche 2 : Téléchargement des données des fournisseurs vers MDS à l’aide du complément MDS pour Excel
  Dans cette tâche, vous publiez les données nettoyées des fournisseurs à **MDS** à l’aide de la **complément MDS pour Excel**. Vous créez une entité nommée **fournisseur** dans le **fournisseurs** modèle que vous avez créé dans la leçon précédente. L'entité aura un attribut pour chaque colonne dans le fichier Excel. Les attributs de Code et le nom de l’entité fournisseur correspondent à la **SupplierID** et **Supplier Name** colonnes dans Excel.  
  
1.  Ouvrez **nettoyées et mises en correspondance de Suppliers.xls** dans **Excel**.  
  
2.  Appuyez sur **CTRL + A** pour sélectionner la totalité des données. Il est **important** que vous sélectionnez l’ensemble des données dans la feuille de calcul.  
  
3.  Cliquez sur **données maîtres** sur la barre de menus.  
  
4.  Cliquez sur **créer une entité** bouton sur le ruban.  
  
     ![Excel - onglet de données Master - bouton Créer entité](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel - onglet de données Master - bouton Créer entité")  
  
5.  Dans **gérer les connexions** boîte de dialogue, si vous ne voyez pas la connexion à **serveur local MDS** sous **connexions existantes**, procédez comme suit :  
  
    1.  Sélectionnez **créer une nouvelle connexion**, puis cliquez sur **New** bouton.  
  
    2.  Dans le **ajouter une nouvelle connexion** boîte de dialogue, tapez **serveur Local MDS** pour **Description** et **http://localhost/MDS** pour  **Adresse du serveur MDS**, puis cliquez sur **OK** pour fermer la boîte de dialogue.  
  
6.  Dans **gérer les connexions** boîte de dialogue, sélectionnez **serveur Local MDS** (http://localhost/MDS), cliquez sur **tester** pour tester la connexion. Cliquez sur **OK** dans le message de confirmation.  
  
7.  Cliquez sur **Connect** pour se connecter au serveur MDS.  
  
8.  Dans le **créer une entité** boîte de dialogue, sélectionnez **fournisseurs** pour le **modèle**.  
  
9. Vérifiez que **VERSION_1** est sélectionné pour **Version**.  
  
10. Entrez **fournisseur** pour **nouveau nom d’entité**.  
  
11. Sélectionnez **SupplierID** pour **la colonne qui contient un identificateur unique** champ (vous pouvez également générer un code automatiquement). Vous mappez essentiellement la **SupplierID** colonne **Excel** à la **Code** attribut de **fournisseur** entité.  
  
12. Sélectionnez **Supplier Name** pour **la colonne qui contient les noms** champ. Vous mappez essentiellement la **Supplier Name** colonne dans **Excel** à la **nom** attribut de la **fournisseur** entité. Le **Code** et **nom** attributs sont des attributs obligatoires pour une entité dans MDS.  
  
     ![Créer la boîte de dialogue entité](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "créer la boîte de dialogue d’entité")  
  
13. Cliquez sur **OK** pour créer l’entité dans MDS, publiez les données de référence à l’entité et fermez **créer une entité** boîte de dialogue.  
  
14. Maintenant, vous devez voir une nouvelle feuille de calcul intitulée **fournisseur**, qui est le nom de l’entité, ajoutée à votre feuille de calcul Excel et en haut de la feuille de calcul, vous devez voir que la feuille de calcul est connecté au serveur MDS. Notez que la feuille de calcul d’origine (intitulé **Sheet1**) existe toujours.  
  
     ![Excel - onglets fournisseurs et Feuille1](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel - onglets fournisseurs et Feuille1")  
  
     ![Excel - affichage des détails de la connexion MDS](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel - affichage des détails de la connexion MDS")  
  
15. Conserver **Excel** ouvrir.  
  
## <a name="next-task"></a>Tâche suivante  
 [Tâche 3 : Vérification des données dans Master Data Manager](../../2014/tutorials/task-3-verifying-the-data-in-master-data-manager.md)  
  
  
