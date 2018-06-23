---
title: 'Tâche 5 : Création d’un attribut basé sur un domaine à partir d’Excel | Documents Microsoft'
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
ms.assetid: 07cbc624-2c6b-4568-96e4-f18663a05d80
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 5e7a8dda16d8f513b2c4b07b9f41712be806b8a9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139705"
---
# <a name="task-5-creating-a-domain-based-attribute-from-excel"></a>Tâche 5 : Créer un attribut basé sur un domaine à partir d'Excel
  Dans cette tâche, vous convertissez la **état** attribut de la **fournisseur** entité en tant qu’un **attribut basé sur un domaine**. Après avoir configuré l’attribut état pour être basés sur un domaine et le publier dans MDS, une nouvelle entité appelée **état** sera créé sur le serveur MDS avec toutes les valeurs dans la colonne et la **état** attribut de la **Fournisseur** entité sera remplie avec les valeurs à partir de la **état** entité. À présent, le **fournisseurs** modèle doit avoir deux entités : **fournisseur** et **état** où le **état** attribut de la  **Fournisseur** entité est un attribut basé sur un domaine qui dépend de **état** entité.  
  
1.  Basculez vers **Excel** fenêtre a **Cleansed and Matched Suppliers.xlsx** ouvrir.  
  
2.  Cliquez sur **Actualiser** bouton sur le ruban pour obtenir les dernières mises à jour à partir de MDS. Vous devez voir les deux enregistrements supplémentaires si vous avez effectué le paramètre facultatif **tâche 4**.  
  
3.  Cliquez sur le nom de la colonne **état** (cellule **I1**) dans le **ligne d’en-tête**.  
  
     ![Excel - bouton Propriétés d’attributs](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel - bouton Propriétés d’attributs")  
  
4.  Cliquez sur **propriétés d’attribut** sur le ruban.  
  
5.  Dans le **propriétés d’attribut** boîte de dialogue, sélectionnez **liste contrainte (basée sur le domaine)** pour le **type d’attribut**.  
  
6.  Type **état** pour le **nouveau nom d’entité** et cliquez sur **OK**.  
  
     ![Excel - boîte de dialogue de propriétés attribut](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel - boîte de dialogue de propriétés attribut")  
  
7.  Désormais, dans Excel, vous devez voir **bas** lorsque vous cliquez sur une valeur dans la **état** colonne. Modifiez la valeur à l'aide de la liste déroulante, le cas échéant.  
  
     ![Excel - liste déroulante liste avec les états](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel - liste déroulante de la liste des États")  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 6 : Vérifier que l’attribut basé sur un domaine est créé à l’aide de Master Data Manager](../../2014/tutorials/task-6-verify-domain-based-attribute-master-data-manager.md)  
  
  