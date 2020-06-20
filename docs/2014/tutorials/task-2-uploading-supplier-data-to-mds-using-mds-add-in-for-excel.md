---
title: 'Tâche 2 : chargement des données des fournisseurs dans MDS à l’aide de Complément MDS pour Excel | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 598deb57-e0cc-4e0a-aeb1-94432c094c67
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5e825829eb70b695a619df8caaa59788d0ad413f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064767"
---
# <a name="task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel"></a>Tâche 2 : Téléchargement des données des fournisseurs vers MDS à l’aide du complément MDS pour Excel
  Au cours de cette tâche, vous allez publier les données du fournisseur et du nettoyage dans **MDS** à l’aide de la **complément MDS pour Excel**. Vous créez une entité nommée **fournisseur** dans le modèle **fournisseurs** que vous avez créé dans la leçon précédente. L'entité aura un attribut pour chaque colonne dans le fichier Excel. Les attributs de code et de nom de l’entité fournisseur correspondent aux colonnes **SupplierID** et **nom du fournisseur** dans Excel.  
  
1.  Ouvrir **les Suppliers.xlsnettoyées et mises en correspondance** dans **Excel**.  
  
2.  Appuyez sur **Ctrl + A** pour sélectionner des données entières. Il est **important** de sélectionner l’ensemble des données dans la feuille de calcul.  
  
3.  Dans la barre de menus, cliquez sur **données** de référence.  
  
4.  Cliquez sur le bouton **créer une entité** dans le ruban.  
  
     ![Excel - Onglet des données de référence - Bouton Créer entité](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel - Onglet des données de référence - Bouton Créer entité")  
  
5.  Dans la boîte de dialogue **gérer les connexions** , si vous ne voyez pas la connexion au **serveur MDS local** sous **connexions existantes**, procédez comme suit :  
  
    1.  Sélectionnez **créer une nouvelle connexion**, puis cliquez sur le bouton **nouveau** .  
  
    2.  Dans la boîte de dialogue **Ajouter une nouvelle connexion** , tapez **serveur MDS local** pour **Description** et **http : \/ /localhost/MDS** pour **adresse du serveur MDS**, puis cliquez sur **OK** pour fermer la boîte de dialogue.  
  
6.  Dans la boîte de dialogue **gérer les connexions** , sélectionnez **serveur MDS local** ( `http://localhost/MDS` ), puis cliquez sur **tester** pour tester la connexion. Cliquez sur **OK** dans le message de confirmation.  
  
7.  Cliquez sur **se connecter** pour vous connecter au serveur MDS.  
  
8.  Dans la boîte de dialogue **créer une entité** , sélectionnez **fournisseurs** pour le **modèle**.  
  
9. Assurez-vous que **Version_1** est sélectionné pour **version**.  
  
10. Entrez le **fournisseur** du **nouveau nom**de l’entité.  
  
11. Sélectionnez **SupplierID** pour **la colonne qui contient un champ d’identificateur unique** (vous pouvez également générer automatiquement un code). Vous mappez essentiellement la colonne **RéfFournisseur** dans **Excel** à l’attribut **code** de l’entité **Supplier** .  
  
12. Sélectionnez le **nom du fournisseur** pour **la colonne qui contient le champ noms** . Vous mappez essentiellement la colonne **nom du fournisseur** dans **Excel** à l’attribut **nom** de l’entité **fournisseur** . Les attributs de **code** et de **nom** sont des attributs obligatoires pour une entité dans MDS.  
  
     ![Boîte de dialogue Créer entité](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "Boîte de dialogue Créer entité")  
  
13. Cliquez sur **OK** pour créer l’entité sur MDS, publier les données de référence dans l’entité et fermer la boîte de dialogue **créer une entité** .  
  
14. Vous devez maintenant voir une nouvelle feuille intitulée **Supplier**, qui est le nom de l’entité, ajouté à votre feuille de calcul Excel et en haut de la feuille de calcul, vous devez voir que la feuille de calcul est connectée au serveur MDS. Notez que la feuille de calcul d’origine (intitulée **Feuil1**) existe toujours.  
  
     ![Excel - Onglets Fournisseurs et Feuille1](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel - Onglets Fournisseurs et Feuille1")  
  
     ![Excel - Affichage des détails de la connexion MDS](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel - Affichage des détails de la connexion MDS")  
  
15. Laissez **Excel** ouvert.  
  
## <a name="next-task"></a>Tâche suivante  
 [Tâche 3 : Vérification des données dans Master Data Manager](../../2014/tutorials/task-3-verifying-the-data-in-master-data-manager.md)  
  
  
