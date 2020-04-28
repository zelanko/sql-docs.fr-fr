---
title: 'Tâche 6 : vérifier que l’attribut basé sur un domaine est créé à l’aide de la Data Manager maître | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6e90517a-910c-4c33-8f11-92ac3cff4fdc
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 56418adbefec0dc996fd83ce70415e86ec9509a3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "78171659"
---
# <a name="task-6-verify-that-the-domain-based-attribute-is-created-using-master-data-manager"></a>Tâche 6 : Tâche 6 : Vérification que l’attribut basé sur un domaine est créé à l’aide de Master Data Manager
  Dans cette tâche, vous allez vérifier que l’entité **État** est créée dans **MDS** et que l’attribut **État** de l’entité **Fournisseur** est un attribut basé sur un domaine qui dépend de l’entité **État** à l’aide de **Master Data Manager**.

1.  Basculez vers l’application web **Master Data Manger**.

2.  Cliquez sur **SQL Server 2012 Master Data Services** en haut pour accéder à la page d’accueil.

3.  Vérifiez que le modèle **Fournisseurs** est sélectionné et cliquez sur **Explorateur**. Vous pouvez actualiser la page si **l’Explorateur** est déjà ouvert.

4.  Pointez votre souris sur **Entités** dans la barre de menus et notez qu’il y a maintenant deux entités : **Fournisseur** et **État**.

     ![Menu Entités avec État et Fournisseur](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-01.jpg "Menu Entités avec État et Fournisseur")

5.  Cliquez sur **État** si l’entité n’est pas déjà ouverte.

6.  Sélectionnez **GA** dans la liste.

7.  Dans le volet **Détails** à droite, remplacez le **Nom** par **Géorgie** dans le **volet droit**, puis cliquez sur **OK**.

8.  Répétez les étapes précédentes pour les autres États.

    |Code|Nom|
    |----------|----------|
    |CA|Californie|
    |CO|Colorado|
    |IL|Illinois|
    |DC|District de Columbia|
    |FL|Floride|
    |AL|Alabama|
    |KY|Kentucky|
    |MA|Massachusetts|
    |AZ|Arizona|
    |MI|Michigan|
    |MN|Minnesota|
    |NJ|New Jersey|
    |NV|Nevada|
    |NY|New York|
    |OH|Ohio|
    |OK|Oklahoma|
    |OR|Oregon|
    |PA|Pennsylvanie|
    |SC|Caroline du Sud|
    |KS|Kansas|
    |TN|Tennessee|
    |TX|Texas|
    |UT|Utah|
    |VA|Virginie|
    |WA|Washington|
    |WI|Wisconsin|
    |HI|Hawaii|
    |MD|Maryland|
    |CT|Connecticut|

9. Sélectionnez l’une des entrées d’État et cliquez sur **Afficher les transactions** dans la barre d’outils. Vous devriez voir la transaction que vous venez de mettre à jour dans la liste des transactions.

10. Pointez la souris sur **Entités** dans le menu et cliquez sur **Fournisseur**.

11. Maintenant, notez qu’une valeur du champ **État** peut être modifiée dans le volet **Détails** à l’aide de la liste déroulante. Remarquez également que, dans la liste à gauche et dans la liste déroulante du volet **Détails**, le code est affiché en premier, suivi par le nom entre accolades. Vous pouvez également modifier d’autres valeurs dans le volet **Détails**.

     ![Attribute d'état avec codes et noms mis au jour](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-02.jpg "Attribute d'état avec codes et noms mis au jour")

## <a name="next-step"></a>étape suivante
 [Tâche 7 : Affichage des mises à jour effectuées à l’aide de Master Data Manager dans Excel](../../2014/tutorials/task-7-viewing-updates-made-using-master-data-manager-in-excel.md)


