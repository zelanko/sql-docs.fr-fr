---
title: 'Tâche 2 : Télécharger des données fournisseurs sur mdS à l’aide de MDS Add-in pour Excel . Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 598deb57-e0cc-4e0a-aeb1-94432c094c67
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 4e3cd4cecd88bcad83c6e9f2a59ecd5f225fb02a
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487693"
---
# <a name="task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel"></a>Tâche 2 : Téléchargement des données des fournisseurs vers MDS à l’aide du complément MDS pour Excel
  Dans cette tâche, vous publiez les données nettoyées et fournisseurs à **MDS** à l’aide de **l’add-in MDS pour Excel**. Vous créez une entité nommée **Fournisseur** dans le modèle **Fournisseurs** que vous avez créé dans la leçon précédente. L'entité aura un attribut pour chaque colonne dans le fichier Excel. Les attributs de code et de nom de l’entité fournisseur correspondent aux colonnes **SupplierID** et **Supplier Name** dans Excel.  
  
1.  Open **Cleansed and Matched Suppliers.xls** in **Excel**.  
  
2.  Appuyez sur **CTRL-A** pour sélectionner des données entières. Il est **important** que vous sélectionniez l’ensemble des données dans la feuille de calcul.  
  
3.  Cliquez sur **Master Data** sur la barre du menu.  
  
4.  Cliquez sur Le bouton **Créer l’entité** sur le ruban.  
  
     ![Excel - Onglet des données de référence - Bouton Créer entité](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel - Onglet des données de référence - Bouton Créer entité")  
  
5.  Dans la boîte de dialogue **Manage Connections,** si vous ne voyez pas la connexion au **serveur MDS local** dans les **connexions existantes,** faites ce qui suit :  
  
    1.  Sélectionnez **Créer une nouvelle connexion**et cliquez sur **nouveau** bouton.  
  
    2.  Dans la boîte de dialogue **Add New Connection,** tapez **local MDS Server** pour la **description** et **http:\//localhost/MDS** pour **l’adresse du serveur MDS**, et cliquez **sur OK** pour fermer la boîte de dialogue.  
  
6.  Dans la boîte de dialogue **Manage Connections,** sélectionnez **Local MDS Server** (),`http://localhost/MDS`cliquez sur **Test** pour tester la connexion. Cliquez sur **OK** dans le message de confirmation.  
  
7.  Cliquez **sur Connectez-vous** pour vous connecter au serveur MDS.  
  
8.  Dans la boîte de dialogue **Create Entity,** sélectionnez **les fournisseurs** pour le **modèle**.  
  
9. Assurez-vous que **VERSION_1** est sélectionnée pour **la version**.  
  
10. Entrez **fournisseur** pour **le nouveau nom d’entité**.  
  
11. Sélectionnez **SupplierID** pour la colonne qui contient un champ **d’identification unique** (vous pouvez également générer un code automatiquement). Vous cartographiez essentiellement la colonne **SupplierID** **d’Excel** à l’attribut **Code** de **l’entité Fournisseur.**  
  
12. Sélectionnez **le nom du fournisseur** pour la colonne qui contient le champ de **noms.** Vous cartographiez essentiellement la colonne **Nom fournisseur** **d’Excel** à l’attribut **Nom** de **l’entité Fournisseur.** Les attributs **Code** et **Nom** sont des attributs obligatoires pour une entité dans MDS.  
  
     ![Boîte de dialogue Créer entité](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "Boîte de dialogue Créer entité")  
  
13. Cliquez **sur OK** pour créer l’entité sur MDS, publier les données maîtresses à l’entité, et fermer la boîte de dialogue Create **Entity.**  
  
14. Maintenant, vous devriez voir une nouvelle feuille intitulée **Fournisseur**, qui est le nom de l’entité, ajoutée à votre feuille de calcul Excel et en haut de la feuille de travail, vous devriez voir que la feuille de travail est connectée au serveur MDS. Notez que la feuille de travail originale (intitulée **Feuille1**) existe toujours.  
  
     ![Excel - Onglets Fournisseurs et Feuille1](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel - Onglets Fournisseurs et Feuille1")  
  
     ![Excel - Affichage des détails de la connexion MDS](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel - Affichage des détails de la connexion MDS")  
  
15. Gardez **Excel** ouvert.  
  
## <a name="next-task"></a>Tâche suivante  
 [Tâche 3 : Vérification des données dans Master Data Manager](../../2014/tutorials/task-3-verifying-the-data-in-master-data-manager.md)  
  
  
